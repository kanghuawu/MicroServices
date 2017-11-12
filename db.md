# MySQL

### Command

```
mysql --user=<user name> --password

enter password: <password>

SHOW <database name>;

USE <database name>;

CREATE DATABASE <database name>;

GRANT ALL PRIVILEGES ON <database name>.* To '<user name>'@'<ip>' IDENTIFIED BY '<password>';

example:

GRANT ALL PRIVILEGES ON lb_server.* To 'lb_server'@'localhost' IDENTIFIED BY 'password';

SELECT User FROM mysql.user;

```