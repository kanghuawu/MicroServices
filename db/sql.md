# SQL

## MySQL Study

* lookup table instead of enum [here](https://stackoverflow.com/questions/761211/how-to-handle-enumerations-without-enum-fields-in-a-database/761343#761343)

* B Tree vs B+Tree [here](https://stackoverflow.com/questions/870218/differences-between-b-trees-and-b-trees)

### Resources

* [GRANT ALL PRIVILEGES](https://stackoverflow.com/questions/5016505/mysql-grant-all-privileges-on-database)


### Baisc Command

```
mysql --user=<user name> --password

ALTER USER 'root'@'localhost' IDENTIFIED BY 'MyNewPass';

SHOW <database name>;

USE <database name>;

CREATE DATABASE <database name>;

GRANT ALL PRIVILEGES ON <database name>.* TO '<user name>'@'<ip>' IDENTIFIED BY '<password>';

example:

GRANT ALL PRIVILEGES ON lb_server.* TO 'lb_server'@'localhost' IDENTIFIED BY 'password';

# show all users
SELECT User FROM mysql.user;

SHOW DATABASES LIKE 'Leetcode';

CREATE DATABASE IF NOT EXISTS Leetcode;

USE Leetcode;

DROP TABLE Employee;

CREATE TABLE IF NOT EXISTS Employee (
    Id INT,
    Salary INT
);
```

## PostgreSQL

```sql
CREATE TABLE account_role
(
  user_id integer NOT NULL,
  role_id integer NOT NULL,
  grant_date timestamp without time zone,
  PRIMARY KEY (user_id, role_id),
  CONSTRAINT account_role_role_id_fkey FOREIGN KEY (role_id)
      REFERENCES role (role_id) MATCH SIMPLE
      ON UPDATE NO ACTION ON DELETE NO ACTION,
  CONSTRAINT account_role_user_id_fkey FOREIGN KEY (user_id)
      REFERENCES account (user_id) MATCH SIMPLE
      ON UPDATE NO ACTION ON DELETE NO ACTION
);

CREATE INDEX index_name
ON table_name (column1_name, column2_name);

CREATE INDEX index_name
on table_name (conditional_expression);

DROP INDEX index_name;
```

## Isolation

**Dirty Reads** occur when one transaction reads data written by another, uncommitted, transaction. The danger with dirty reads is that the other transaction might never commit, leaving the original transaction with "dirty" data.

**Non Repeatable Reads** occur when one transaction attempts to access the same data twice and a second transaction modifies the data between the first transaction's read attempts. This may cause the first transaction to read two different values for the same data, causing the original read to be non-repeatable

**Phantom Read** occurs when two same queries are executed, but the rows retrieved by the two, are different. For example, suppose transaction T1 retrieves a set of rows that satisfy some search criteria. Now, Transaction T2 generates some new rows that matches the search criteria for transaction T1. If transaction T1 reexecutes the statement that reads the rows, it gets a different set of rows this time.


> [wiki](https://en.wikipedia.org/wiki/Isolation_(database_systems)#Isolation_levels)
> [geeksforgeeks](https://www.geeksforgeeks.org/transaction-isolation-levels-dbms/)
