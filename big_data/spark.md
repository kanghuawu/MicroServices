# Spark

## Setup

* https://blog.insightdatascience.com/spinning-up-a-spark-cluster-on-spot-instances-step-by-step-e8ed14ebb3b

## Advanced

* Top 5 Mistakes When Writing Spark Applications [youtube](https://www.youtube.com/watch?v=WyfHUNnMutg), [slide](https://www.slideshare.net/hadooparchbook/top-5-mistakes-when-writing-spark-applications-66374492)
* The Top Five Mistakes Made When Writing Streaming Applications - Mark Grover Ted Malaska [youtube](https://www.youtube.com/watch?v=I7cULsDbSaU), [slide](https://www.slideshare.net/hadooparchbook/top-5-mistakes-when-writing-streaming-applications)
* Spark yarn cluster vs client - how to choose which one to use? [stackoverflow](https://stackoverflow.com/questions/41124428/spark-yarn-cluster-vs-client-how-to-choose-which-one-to-use?rq=1)
* Long-running Spark Streaming Jobs on YARN Cluster [Marcin Kuthan blog](http://mkuthan.github.io/blog/2016/09/30/spark-streaming-on-yarn/)
* Mastering Spark Unit Testing (Ted Malaska) [youtube](https://www.youtube.com/watch?v=4U9Me6shpno)

## Cassandra Integration

* datastax connector (python)[here](https://github.com/datastax/spark-cassandra-connector/blob/master/doc/15_python.md)
* wrapper for datastax connector (python)[here](https://github.com/anguenot/pyspark-cassandra)
  * `SPARK_HOME/bin/pyspark --packages anguenot:pyspark-cassandra:0.7.0`

## SQL

* JSON with Spark SQL
  * scala [example 1](http://blog.antlypls.com/blog/2016/01/30/processing-json-data-with-sparksql/)
  * scala [example 2](https://stackoverflow.com/questions/39355149/how-to-read-json-with-schema-in-spark-dataframes-spark-sql)
  * scala [example 3](https://databricks.com/blog/2015/02/02/an-introduction-to-json-support-in-spark-sql.html)
  * python [example 4](http://nadbordrozd.github.io/blog/2016/05/22/one-weird-trick-that-will-fix-your-pyspark-schemas/)

## Todo
```shell
## Advanced Tunning

https://www.youtube.com/watch?t=3215&v=HG2Yd-3r4-M

### Skewed data

* https://stackoverflow.com/questions/40373577/skewed-dataset-join-in-spark

* https://databricks.com/session/handling-data-skew-adaptively-in-spark-using-dynamic-repartitioning

* https://datarus.wordpress.com/2015/05/04/fighting-the-skew-in-spark/

* http://silverpond.com.au/2016/10/06/balancing-spark.html
* https://github.com/vaquarkhan/vk-wiki-notes/wiki
* https://community.hortonworks.com/questions/51391/dataframessets-simple-join-is-skewed-due-to-join-c.html
```
