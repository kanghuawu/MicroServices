
# Basics

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
DESCRIBE keyspaces;

CREATE KEYSPACE mydb WITH replication={
  'class': 'SimpleStrategy', 
  'replication_factor': '1'
};

DESCRIBE TABLE users;

DESCRIBE mydb;

USE mydb;

CREATE TABLE users ( 
  firstname text,
  lastname text,
  age int,
  email text,
  city text,
  PRIMARY KEY (lastname));

DESCRIBE TABLE users;

INSERT INTO users (firstname, lastname, age, email, city) 
VALUES ('John', 'Smith', 46, 'johnsmith@email.com', 'Sacramento');

INSERT INTO users (firstname, lastname, age, email, city) 
VALUES ('Jane', 'Doe', 36, 'janedoe@email.com', 'Beverly Hills');

SELECT * FROM users;

SELECT * FROM users WHERE lastname= 'Doe';

UPDATE users SET city= 'San Jose' WHERE lastname= 'Doe';

DELETE from users WHERE lastname = 'Doe';

DROP TABLE users;

DROP KEYSPACE mydb;
```
