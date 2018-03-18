
# Cassandra

## Directory

```shell
# config (e.g. cassandra.yaml) is under /usr/local/etc/cassandra

# logs is under /usr/local/var/log/cassandra/

# data is under /usr/local/var/lib/cassandra/data/
```

## Setup

```shell
# might bring up correct config
brew services start cassandra

cassandra -f
```
> It is possible, but generally not recommended, to create multiple keyspaces per application.

## CQL

```shell
desc keyspaces;

CREATE KEYSPACE mydb WITH replication={
  'class': 'SimpleStrategy', 
  'replication_factor': '1'
};

desc table users;

desc mydb;

use mydb;

CREATE TABLE users ( 
  firstname text,
  lastname text,
  age int,
  email text,
  city text,
  PRIMARY KEY (lastname));

desc table users;

INSERT INTO users (firstname, lastname, age, email, city) 
VALUES ('John', 'Smith', 46, 'johnsmith@email.com', 'Sacramento');

INSERT INTO users (firstname, lastname, age, email, city) 
VALUES ('Jane', 'Doe', 36, 'janedoe@email.com', 'Beverly Hills');

SELECT * FROM users;

SELECT * FROM users WHERE lastname= 'Doe';

UPDATE users SET city= 'San Jose' WHERE lastname= 'Doe';

DELETE from users WHERE lastname = 'Doe';
```

## Data Model

### Keyspaces

### Column Families (Tables)
Each column family is stored on disk in its own separate file. So to optimize perform- ance, it’s important to keep columns that you are likely to query together in the same column family, and a super column can be helpful for this.
### Columns
### Super Columns
* The basic structure of a super column is its name, which is a byte array (just as with a regular column), and the columns it stores. Its columns are held as a map whose keys are the column names and whose values are the columns.

* The SuperColumn class implements both the IColumn and the IColumnContainer classes.

### Composite Keys
There is an important consideration when modeling with super columns: Cassandra does not index subcolumns, so when you load a super column into memory, all of its columns are loaded as well. You can use a composite key of your own design to help you with queries.

### Design Patterns

#### Materialized View
It is common to create a **secondary index** that represents additional queries. Because you don’t have a SQL WHERE clause, you can recreate this effect by writing your data to a second column family that is created specifically to represent that query.

> Secondary Index: A secondary index is helpful for quickly looking up data when searching by one or more non-key columns [here](https://cloud.google.com/spanner/docs/secondary-indexes).

#### Valueless Column
A key can itself hold a value. In other words, you can have a valueless column.

#### Aggregate Key
When you use the Valueless Column pattern, you may also need to employ the Aggregate Key pattern.

# Reference and Resources

* Cassandra The Definitive Guide
* https://www.ebayinc.com/stories/blogs/tech/cassandra-data-modeling-best-practices-part-1/
* https://www.ebayinc.com/stories/blogs/tech/cassandra-data-modeling-best-practices-part-2/
