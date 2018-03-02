# MySQL

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
