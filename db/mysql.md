# MySQL

### Resources

* [GRANT ALL PRIVILEGES](https://stackoverflow.com/questions/5016505/mysql-grant-all-privileges-on-database)


### Command

```
mysql --user=<user name> --password

enter password: <password>

SHOW <database name>;

USE <database name>;

CREATE DATABASE <database name>;

GRANT ALL PRIVILEGES ON <database name>.* TO '<user name>'@'<ip>' IDENTIFIED BY '<password>';

example:

GRANT ALL PRIVILEGES ON lb_server.* TO 'lb_server'@'localhost' IDENTIFIED BY 'password';

SELECT User FROM mysql.user;

```