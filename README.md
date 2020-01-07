Sysbench - loading data from specified file
====

Sysbench is a popular open source benchmark tool written in C and Lua. It is used to run various MySQL benchmark test. It provides different OLTP workloads, including insert, read / write, read only, write only, update with index and update without index, etc.

Here sysbench code has been modified to support loading data from given text file. Text files can be gerated using tools like [SDGen](https://github.com/AussieGuy0/SDgen), with different compressibilities for MySQL benchmarking.

You can follow README in sysbench folder to build / install sysbench.

1 option is added to support specifying input files for loading data to MySQL tables -

`--table-data-src-file=txt_file_path`

Used along with below option MySQL page copmression can be tested with different data compressibilities.

`--create-table-options={None|lz4|zlib}`

These 2 options are workload options, they need to be added after workload file name in sysbench command line. For an example -

`sysbench --db-driver=mysql --mysql-socket=/tmp/mysqld.sock --mysql-db=sbtest --mysql-user=root --mysql-pwd=my_password --report-interval=1 --time=3600 --threads=64 --percentile=95 /usr/local/share/sysbench/oltp_insert.lua --warmup-time=60 --rand-type=uniform --histogram=on --tables=64 --table-size=5000000 --create-table-options=none --table-data-src-file=./normal.txt prepare`


Original Sysbench [README](README.org.md) goes here.
