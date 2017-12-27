# Hadoop

### Resources

* [tomwhite](https://github.com/tomwhite/hadoop-book)


```
set up pycharm 
https://stackoverflow.com/questions/34685905/how-to-link-pycharm-with-pyspark

export PYSPARK_PYTHON=python3

PYTHONSTARTUP=code.py pyspark

https://community.cloudera.com/t5/Cloudera-Manager-Installation/What-is-the-Path-of-hdfs-site-xml-core-xml/m-p/15188
hdfs://quickstart.cloudera:8020

```


```
https://community.cloudera.com/t5/Cloudera-Manager-Installation/What-is-the-Path-of-hdfs-site-xml-core-xml/m-p/15188
/etc/hadoop/[service name]/hdfs-site.xml

Example:
/etc/hadoop/conf.cloudera.hdfs1/hdfs-site.xml

core-site.xml on the same path.

```