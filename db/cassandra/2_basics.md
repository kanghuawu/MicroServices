# Basics

## Types

### Numeric Data Type
* int: 32-bit signed integer (Java int)
* bigint: 64-bit signed long integer (Java long)
* smallint: 16-bit signed integer (Java short)
* tinyint: An 8-bit signed integer (Java tinyint)
* varint: A variable precision signed integer (equivalent to java.math.BigInteger)
* float: 32-bit IEEE-754 floating point (Java float)
* double: 64-bit IEEE-754 floating point (Java double)
* decimal: variable precision decimal (equivalent to java.math.BigDecimal) 
### Textual Data Types
* text, varchar: Synonyms for a UTF-8 character string
* ascii: An ASCII character string 
### Time and Identity Data Types
* timestamp: 2015-06-15 20:05:07.013-0700
* date, time
* uuid: Type **4** UUID. For exampe, 1a6300ca-0572-**4**736-a393-c0b7229e193e.
* timeuuid: Type **1** UUID. For exampe, XX-XX-**1**XX-XX-XX
### Other Simple Data Types
* boolean
* blob
* inet
* counter
### Collections
* set
* list
* map
### User-Defined Types (UDTs)
```shell
CREATE TYPE address (
   street text,
   city text,
   state text,
   zip_code int);
```

## Models
### Clusters
### Keyspaces
### Tables
Each column family is stored on disk in its own separate file. So to optimize performance, it’s important to keep columns that you are likely to query together in the same column family, and a super column can be helpful for this.
### Columns
### Super Columns
The basic structure of a super column is its name, which is a byte array (just as with a regular column), and the columns it stores. Its columns are held as a map whose keys are the column names and whose values are the columns.

The SuperColumn class implements both the IColumn and the IColumnContainer classes.

### Composite Keys/compound key/partitions
Cassandra uses a special primary key called a composite key (or compound key) to represent wide rows, also called partitions. The composite key consists of a partition key, plus an  optional set of clustering columns.

There is an important consideration when modeling with super columns: Cassandra does not index subcolumns, so when you load a super column into memory, all of its columns are loaded as well. You can use a composite key of your own design to help you with queries.

## Design Patterns

* Materialized View: It is common to create a **[secondary index](#secondary-index)** that represents additional queries. Because you don’t have a SQL WHERE clause, you can recreate this effect by writing your data to a second column family that is created specifically to represent that query.
* Valueless Column: A key can itself hold a value. In other words, you can have a valueless column.
* Aggregate Key: When you use the Valueless Column pattern, you may also need to employ the Aggregate Key pattern.

## Design Differences Between RDBMS and Cassandra
* No joins
* No referential integrity
* Denormalization
* Query-first design
* Designing for optimal storage
* Sorting is a design decision

## Secondary Index
A secondary index is helpful for quickly looking up data when searching by one or more non-key columns [here](https://cloud.google.com/spanner/docs/secondary-indexes).

SSTable Attached Secondary Index (SASI): A New Secondary Index Implementation
```shell
CREATE CUSTOM INDEX user_last_name_sasi_idx ON user (last_name) 
  USING 'org.apache.cassandra.index.sasi.SASIIndex';

# Like
SELECT * FROM user WHERE last_name LIKE 'N%';

# Inequality
SELECT * FROM user WHERE age > 10;
```
### Don'ts
* Columns with high cardinality. For example, indexing on the user.addresses column could be very expensive, as the vast majority of addresses are unique.
* Columns with very low data cardinality. For example, it would make little sense to index on the user.title column in order to support a query for every “Mrs.” in the user table, as this would result in a massive row in the index.
* Columns that are frequently updated or deleted. Indexes built on these columns can generate errors if the amount of deleted data (tombstones) builds up more quickly than the compaction process can handle.


## Reference and Resources

* Cassandra The Definitive Guide
* https://www.ebayinc.com/stories/blogs/tech/cassandra-data-modeling-best-practices-part-1/
* https://www.ebayinc.com/stories/blogs/tech/cassandra-data-modeling-best-practices-part-2/
