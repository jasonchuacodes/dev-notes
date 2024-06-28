### Step 1: Update Package List

Open a terminal and run the following commands to update the package list:
`sudo apt update sudo apt upgrade`
### Step 2: Install MySQL Server

Install the MySQL Server package by running:
`sudo apt install mysql-server`

During the installation process, you will be prompted to set a password for the MySQL root user. Make sure to remember this password, as you will need it to access and configure the MySQL server.

### Step 3: Start MySQL Service

After the installation is complete, MySQL should start automatically. If not, you can start the MySQL service with:
`sudo service mysql start`

### Step 4: Check MySQL Status

You can check the status of the MySQL service by running:
`sudo service mysql status`

### Step 5: Access MySQL

To access the MySQL server, you can use the MySQL command-line client. Run the following command and enter the root password when prompted:
`mysql -u root -p`

