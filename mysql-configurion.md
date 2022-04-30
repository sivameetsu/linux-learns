## MySQL Configurion

#### What is MySQL?

MySQL is currently the most popular database management system software used for managing the relational database. It is open-source database software, which is supported by Oracle Company. It is fast, scalable, and easy to use database management system in comparison with Microsoft SQL Server and Oracle Database.MySQL follows the working of a client/server architecture.MySQL supports many Operating Systems like Windows, Linux.

**MySQL INSTALLATION**
  
```bash
sudo apt update
sudo apt install mysql-server -y
```
**secure installtion**

```bash
sudo mysql_secure_installation
.....
```

**MySQL login**

```bash
sudo mysql -u root -p
```
   
**How to exit the database**

```bash
exit (or) \q
```
    


#### Create a MySQL New User:-

```bash
CREATE USER 'New_user_name'@'localhost' IDENTIFIED BY 'password';
```
![Screenshot from 2022-04-28 20-55-30](https://user-images.githubusercontent.com/102893121/165788150-f4263fc5-6a9a-499d-b4de-404f2af01d1d.png)



#### To grant all privileges to MySQL User on all databases:-

```bash
GRANT ALL PRIVILEGES ON *.* TO 'Neww_user_name'@'localhost' WITH GRANT OPTION;
```

![Screenshot from 2022-04-28 20-57-49](https://user-images.githubusercontent.com/102893121/165788530-abfaa209-8368-4d11-803b-93de143f57b8.png)


#### To grant insert privileges to a MySQL user:-

```bash 
GRANT INSERT ON *.* TO 'New_user-name'@'localhost';
```
![Screenshot from 2022-04-28 21-01-05](https://user-images.githubusercontent.com/102893121/165789253-1f4357f1-fd98-45a2-8341-66c1fddc6626.png)



#### To show all the privileges in a specified user:-

```bash
SHOW GRANTS FOR 'new_user_name'@'localhost';
```

![image](https://user-images.githubusercontent.com/91359308/164619150-fa0ccbad-0241-4c82-b1fd-357a572f5f6a.png)

#### List out the details of users:-

![image](https://user-images.githubusercontent.com/91359308/164619600-2d0a46a7-303a-4764-9a51-2ec690af9005.png)



#### Create a Database:- 

![image](https://user-images.githubusercontent.com/98270930/164432767-f103370c-7ba6-42c6-9d05-5f881fb1b58e.png)

#### Show the Created Database:- 

 ![image](https://user-images.githubusercontent.com/98270930/164433044-e189e893-5549-4b81-8f05-42d63a4506a6.png)

#### Enter into the specified Database:- 

 ![image](https://user-images.githubusercontent.com/98270930/164433288-a061e2e5-26aa-4b93-90fe-cdb70cd822ec.png)
 
 #### Delete the Database:-
 
 ![image](https://user-images.githubusercontent.com/98270930/164434562-50e2d6f2-6e5f-4de9-9bb2-522124a8d163.png)


#### Database Table Creation Syntax
```bash
    CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype,
   ....
);
```
#### MySQL ALTER TABLE Statement

##### 1) ALTER TABLE - ADD Column:-
 ```bash

  ALTER TABLE table_name
    ADD column_name datatype; 
```
##### 2) ALTER TABLE - DROP COLUMN:-
 ```bash

  ALTER TABLE table_name
    DROP COLUMN column_name;  
```
##### 3) ALTER TABLE - MODIFY COLUMN:-
 ```bash

  ALTER TABLE table_name
    MODIFY COLUMN column_name datatype;   
```
#### MySQL Copy/Clone/Duplicate Table:-
 ```bash
    CREATE TABLE new_table_name  
      SELECT column1, column2, column3   
        FROM existing_table_name;    
```

####  MySQL INSERT INTO Statement:-
 ```bash
    INSERT INTO table_name (column1, column2, column3, ...) VALUES (value1, value2, value3, ...); 
                                            [or]
    INSERT INTO table_name VALUES (value1, value2,...valueN),( value1, value2,...valueN ),...........,( value1, value2,...valueN );                                      
```

####  MySQL UPDATE Statement:-
 ```bash
    UPDATE table_name  
        SET column1 = value1, column2 = value2, ...
            WHERE condition;                                               
```

#### MySQL ORDER BY:
```bash
    SELECT column1, column2, ...
        FROM table_name
            ORDER BY column1, column2, ... ASC|DESC; 
```

#### LIMIT - The LIMIT clause is used to specify the number of records to return.
```bash
    SELECT column_name(s)
        FROM table_name
            WHERE condition
                LIMIT number; 
```
#### Basic Syntax of MySQL 

|S.NO|SYNTAX|DESCRIPTION|
|---|----|-----|
|1.|CREATE DATABASE [db-name];  |To create a new database.|
|2.|SHOW DATABASES;|List out the databases.|
|3.|USE [db-name];|Enter into the specified database.|
|4.|DROP DATABASE [db_name];|To delete the specified database.|
|5.|CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';| Create a new user|
|6.|GRANT permission_type ON database.table TO 'username'@'localhost';| To grant privileges to a user account |
|7.|GRANT INSERT ON * . * TO 'username'@'localhost';|To grant insert privileges to a MySQL user|
|8.|SHOW GRANTS FOR username;|To display all the current privileges held by a user|
|9.|GRANT ALL PRIVILEGES ON * . * TO 'database_user'@'localhost';|To grant all privileges to MySQL User on all databases|
|10.|GRANT ALL PRIVILEGES ON database_name.* TO 'database_user'@'localhost';|To grant all privileges to a user account on a specific database|
|11.|GRANT ALL PRIVILEGES ON database_name.table_name TO 'database_user'@'localhost';|To grant all privileges to a user account over a specific table from a database |
|12.|REVOKE permission_type ON database.table TO 'username'@'localhost';|Revoke Privileges MySQL User Account|
|13.|DROP USER 'username'@'localhost';|Remove an Entire User Account|
|14.|TRUNCATE TABLE table_name;|It is used to delete the data inside a table.|
|15.|SHOW TABLES; | List out all the tables in specified database.|
|16.|RENAME old_table TO new_table;| To rename the name of the table|
|17.|DESC table_name|Describe the specified table details.|
|18.|DROP TABLE  table_name;|It is used to delete complete the data in the table.|
|19.|DELETE FROM table_name WHERE condition; |To delete the row of the table using where condition.|
|20.|SELECT column1, column2, ...FROM table_name; |To view the specified colums details in specified table.|
|21.|SELECT * FROM table_name; |To view a details of the entire specified table.|

### Reference:-

For more details visit this page - https://www.javatpoint.com/mysql-tutorial
----


## MySQL Install And create user Process (Ubuntu OS)

In this case first Update and install the MYsql USing this Command

Ctrl + t - open terminal and 

**sudo apt update** - update the previous files then 

enter **Sudo apt-get install mysql-server -y** after install the server

check running status on the server using **sudo systemctl status mysql.service** It complete status shown **Active** then going to coinfig process

## MYSQL Config process

 In this section first run secure Process Like Password, privilages set and etc... using this commant
 
 **sudo mysql_secure_installation**

after enter the (yes or no) option 
set ROOT password and remind or note the Root password on your dairy or Note
then select your Password strenght (Low,medium,High) 
complete this section then move user,datebase,table creation privileges 

## Mysql user,datebase,table creation privileges**

In this section we will show how to create user datebase table and the privileges 

first of all enter with ur root user and password using this comment

**mysql -u root -p**

then enter ur Root Password

then enter mysql server 

first create the user on the server using this command
CREATE USER 'user_name'@'localhost' IDENTIFIED BY 'password';

(corrctly enter user name and password)

then check user is created or not using this command

**select user from mysql.user;**

then grant ALL privileges to user for this command

**GRANT ALL PRIVILEGES ON *.* TO 'sammy'@'localhost' WITH GRANT OPTION;**

in this section give specific database permission for this command

**GRANT ON database_name.* TO 'sammy'@'localhost';** 

then save ur privilege changes using this command

**fluses privileges;**

and check ur privileges are assign or not using this commant

**show grants for user1@localhost;**

Next We will create database on Root user Set privilege to specify user

first create database on Root User account and give specify permission to user this account

**create database database_name;**

and check database are create or niot using this commant

**show databases;**

then give permission to access the user

**grant all on user_name.* to user'3@'localhost';**

check ur privileges are assign or not using this commant

**show grants for user1@localhost;**
in this section complete then next table create

**Next create table for the databases**

in this section first you enter ur user account 

then create table 

**CREATE TABLE TABLE NAME( NAME varchar(50) , age int , address varchar(50) );**

using this commant modify for ur changes

to view the table use below command

**describe table_name;**

then insert values to the Table using this commnad for ur values

**insert into A(Memberid,MemberName,MemeberAge) values (3, 'deva1', 2);**

to view the value you insert the table use below command

**describe table_name;**
 
 complete the section Next How to get backup database and table
 
 In this Section first how to backup single database for Mysql in below commant
 
 **mysqldump -u root -p user1data > /home/deva/Mysql_bak/user1data_bak.sql**

then create multiple databases backup in sinle comment

**mysqldump -u root -p --databases user1data user2data user3data > /home/deva/Mysql_bak/alldatabase_bak.sql**

and Next create back in single Table

**mysqldump -u root -p user1data A >/home/deva/Table_bak/single_bak.sql**

and next Multiple table in single  command

**mysqldump -u root -p user1data A B C >/home/deva/Table_bak/all_bak.sql**

##Restore

in this section how to restore the bacup tables in single file

**mysql -u root -p user3data < /home/deva/Table_bak/a3_bak.sql**

Multiple table restore

**mysql -u root -p user3data < /home/deva/Table_bak/all3_bak.sql**

in this section restore single data base in mysql

in restore process first you remove privious databases using drop commant

create new empty database 

**mysql -u root -p user1data < /home/deva/Mysql_bak/user1data_bak.sql**

in this section restore single data base in mysql

**mysql -u root -p uset1 < /home/deva/Mysql_bak/alldatabase_bak.sql **

restore single and mutiple restore process cmd is same.


