#### Scenario
We have created a new database in MySQL but upon trying to connect it to our DBMS (i.e. TablePlus), it says that the access is denied.

The error "ERROR 1698 (28000): Access denied for user 'root'@'localhost'" typically occurs when attempting to connect to MySQL as the root user without the correct authentication method.

#### Solution:
We need to connect to MySQL and update the password of the user that owns the database.

Step 1: In the terminal, start the mysql server
`sudo service mysql start`

You may choose to verify if the mysql server is active.
`sudo service mysql status`

Step 2: Connect to the mysql service 
`mysql -u <USER> -p`

You may choose to verify if this is the user that has the newly created database.
`mysql > show databases;`

Step 3: Update the user password
`ALTER USER '<SET_USER>'@'localhost' IDENTIFIED WITH mysql_native_password BY '<NEW_PASSWORD>';`
