## MySQL Install And create user Process (Ubuntu OS)
---

_What is Mysql_

MySQL creates a database for storing and manipulating data, defining the relationship of each table. Clients can make requests by typing specific SQL statements on MySQL. The server application will respond with the requested information and it will appear on the clients' side.


_Install Mysql Service_

```bash

sudo apt update
sudo apt-get install mysql-server -y

```

check running status on the server using 

```bash

sudo systemctl status mysql.service

```
---

**MYSQL Config process**

First, use this command to run security processes such as passwords, privileges, and so on.
 
 ```bash
 
 sudo mysql_secure_installation
 
```
* #Change the password for root ? ((Press y|Y for Yes, any other key for No) :
* #Remove anonymous users? (Press y|Y for Yes, any other key for No) : 
* #Disallow root login remotely? (Press y|Y for Yes, any other key for No) : 
* #Remove test database and access to it? (Press y|Y for Yes, any other key for No) : 
* #Reload privilege tables now? (Press y|Y for Yes, any other key for No) : 
 

**_Mysql user,datebase,table creation & set privileges_**

We'll create a user, a database, a table, and permissions in this section.

first of all enter with ur root user and password using this comment

```bash

mysql -u root -p

```

_create the user_

```bash

CREATE USER 'user_name'@'localhost' IDENTIFIED BY 'password';

```

* To see the user list --> `select user from mysql.user`


_Grant ALL privileges to user_

```bash

GRANT ALL PRIVILEGES ON *.* TO 'sammy'@'localhost' WITH GRANT OPTION;
FLUSH PRIVILEGES;
```
_Revoke Permmission_

```bash

REVOKE ALL PRIVILEGES ON *.* FROM 'username'@'localhost';
or
REVOKE permission ON *.*FROM 'user'@'localhost';
FLUSH PRIVILEGES;
```

To view the user privileges --> `SHOW GRANTS FOR username@localhost;`

**Max Used privileges**

* Select
* Insert
* Update

---

**Create database on Root user Set privilege to specify user**

Create a database on the Root User account and grant specific permissions to this account's users.

```bash

create database database_name;

```
Check if the database has been created. ---> `show databases;`

_In the database, set user permissions_

```bash

GRANT all ON database_name.* TO 'sammy'@'localhost';
flush privileges;

```

* To view the users permission ---> `show grants for user1@localhost;`
* To enter any database use this commant  ---> `use database name`
* To view the current database name ---> `status;`
* To exit the databse use this command ---> `exit` 

---

**Create table in the databases**

in this section first you enter ur user account 

_create table_ 

```bash

CREATE TABLE TABLE NAME( NAME varchar(50) , age int , address varchar(50) );

```

* To view the table --> `describe table_name:`

_Insert values to the tables_


```bash

insert into A(Memberid,MemberName,MemeberAge) values (3, 'deva1', 2);

```

* To view the value you insert the table ---> `select * from table name;`

 
complete the section Next How to get backup database and table
 
In this Section first how to backup single database for Mysql in below commant
 
 ```bash
 mysqldump -u root -p user1data > /home/deva/Mysql_bak/user1data_bak.sql
 ```

then create multiple databases backup in sinle comment

```bash
 mysqldump -u root -p --databases user1data user2data user3data > /home/deva/Mysql_bak/alldatabase_bak.sql
 ```

and Next create back in single Table

```bash
mysqldump -u root -p user1data A >/home/deva/Table_bak/single_bak.sql
```

and next Multiple table in single  command

```bash
mysqldump -u root -p user1data A B C >/home/deva/Table_bak/all_bak.sql
```

##Restore

in this section how to restore the bacup tables in single file

```bash
mysql -u root -p user3data < /home/deva/Table_bak/a3_bak.sql
```

Multiple table restore

```bash
mysql -u root -p user3data < /home/deva/Table_bak/all3_bak.sql
```

in this section restore single data base in mysql

in restore process first you remove privious databases using drop commant

create new empty database 

```bash
mysql -u root -p user1data < /home/deva/Mysql_bak/user1data_bak.sql
```

in this section restore single data base in mysql
**in this commant use is base terminal not mysql**

```bash
mysql -u root -p uset1 < /home/deva/Mysql_bak/alldatabase_bak.sql
```

restore single and mutiple restore process cmd is same.

to check the restore database table record
```bash
select count(*) from data_2;
```

## MySql backup database file transfer one server to another server

first enter the mysql console
backup ur need database using this command

```bash
 mysqldump -u root -p database name > file path/user1data_bak.sql
 ```
and tranfer ur file to another server using this command

```bash
scp source_file_name username@destination_host:destination_folder
```
once file transfered then next restore using this command **using command in base terminal not mysql console**

```bash
mysql -u root -p databasename < filepath/backup.sql;
```

to check the restore database table record
```bash
select count(*) from data_2;
```
