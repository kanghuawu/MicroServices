# Hadoop

## Setup

* https://blog.insightdatascience.com/spinning-up-a-free-hadoop-cluster-step-by-step-c406d56bae42
* http://hadoop.apache.org/docs/current/hadoop-project-dist/hadoop-common/SingleCluster.html

### Resources

* [tomwhite](https://github.com/tomwhite/hadoop-book)


```
set up pycharm 
https://stackoverflow.com/questions/34685905/how-to-link-pycharm-with-pyspark

# if use virtualenv manual export following command after active virtualenv
export PYSPARK_PYTHON=`which python3`

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
