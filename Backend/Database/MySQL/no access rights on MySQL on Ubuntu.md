
On some systems, like [Ubuntu](https://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29), MySQL is using the [Unix auth_socket plugin](https://dev.mysql.com/doc/mysql-security-excerpt/5.5/en/socket-pluggable-authentication.html) by default.

Basically it means that: _db_users using it, will be "authenticated" by **the system user credentials.**_ You can see if your `root` user is set up like this by doing the following:

```
sudo mysql -u root # I had to use "sudo" since it was a new installation

mysql> USE mysql;
mysql> SELECT User, Host, plugin FROM mysql.user;

+------------------+-----------------------+
| User             | plugin                |
+------------------+-----------------------+
| root             | auth_socket           |
| mysql.sys        | mysql_native_password |
| debian-sys-maint | mysql_native_password |
+------------------+-----------------------+
```

As you can see in the query, the `root` user is using the `auth_socket` plugin.

There are two ways to solve this:

1. You can set the _root_ user to use the `mysql_native_password` plugin
2. You can create a new `db_user` with you `system_user` (recommended)

**Option 1:**

```
sudo mysql -u root # I had to use "sudo" since it was a new installation

mysql> USE mysql;
mysql> UPDATE user SET plugin='mysql_native_password' WHERE User='root';
mysql> FLUSH PRIVILEGES;
mysql> exit;

sudo service mysql restart
```

**Option 2:** (replace YOUR_SYSTEM_USER with the username you have)

```
sudo mysql -u root # I had to use "sudo" since it was a new installation

mysql> USE mysql;
mysql> CREATE USER 'YOUR_SYSTEM_USER'@'localhost' IDENTIFIED BY 'YOUR_PASSWD';
mysql> GRANT ALL PRIVILEGES ON *.* TO 'YOUR_SYSTEM_USER'@'localhost';
mysql> UPDATE user SET plugin='auth_socket' WHERE User='YOUR_SYSTEM_USER';
mysql> FLUSH PRIVILEGES;
mysql> exit;

sudo service mysql restart
```

Remember that if you use option #2 you'll have to connect to MySQL as your system username (`mysql -u YOUR_SYSTEM_USER`).