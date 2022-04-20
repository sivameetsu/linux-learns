## MySQL Configurion

#### What is MySQL?

MySQL is currently the most popular database management system software used for managing the relational database. It is open-source database software, which is supported by Oracle Company. It is fast, scalable, and easy to use database management system in comparison with Microsoft SQL Server and Oracle Database.MySQL follows the working of a client/server architecture.
MySQL supports many Operating Systems like Windows
, Linux
#### How MySQL Works?

![image](https://user-images.githubusercontent.com/91359308/163947248-11d3d500-84d1-475a-9a53-d98fde11fd77.png)

#### MySQL Data Types
  Each column in a database table is required to have a name and a data type.

  An SQL developer must decide what type of data that will be stored inside each column when creating a table. The data type is a guideline for SQL to       understand what type of data is expected inside of each column, and it also identifies how SQL will interact with the stored data.

  In MySQL there are three main data types: **string**, **numeric**, and **date and time**.
  
 ##### 1. String Data Types:
  
  ![image](https://user-images.githubusercontent.com/91359308/163949310-74e71d76-61c6-4f54-9cac-2c10a1857f6e.png)

  ##### 2. Numeric Data Types:
  
  ![image](https://user-images.githubusercontent.com/91359308/163949560-ecd81d03-c5f2-477e-9e28-20dbb2c44f15.png)
  
  ##### 3. Date and Time Data Types:
  
  ![image](https://user-images.githubusercontent.com/91359308/163949699-a87cfcad-dfd0-4f45-9176-8a7d0f9a0e07.png)
  
  #### MySQL INSTALLATION
  
    sudo apt update
    sudo apt install mysql
  
  #### MySQL Server Connection
  
    sudo mysql -u root -p
   
  #### How to exit the database
  
     exit (or) \q
    
    
### How to Create New MySQL User

|S.NO|SYNTAX|DESCRIPTION|
|---|----|-----|
|1.|CREATE USER 'username'@'localhost' IDENTIFIED BY 'password'; [or] CREATE USER 'username'@'ip_address' IDENTIFIED BY 'password';| Create a new user|
|2.|GRANT permission_type ON database.table TO 'username'@'localhost';| to grant privileges to a user account |
|3.|GRANT INSERT ON *.* TO 'username'@'localhost';|to grant insert privileges to a MySQL user|
|4.|SHOW GRANTS FOR username;|To display all the current privileges held by a user|
|5.|GRANT ALL PRIVILEGES ON *.* TO 'database_user'@'localhost';|To grant all privileges to MySQL User on all databases|
|6.|GRANT ALL PRIVILEGES ON database_name.* TO 'database_user'@'localhost';|To grant all privileges to a user account on a specific database|
|7.|GRANT ALL PRIVILEGES ON database_name.table_name TO 'database_user'@'localhost';|To grant all privileges to a user account over a specific table from a database |
|8.|REVOKE permission_type ON database.table TO 'username'@'localhost';|Revoke Privileges MySQL User Account|
|9.|DROP USER 'username'@'localhost';|Remove an Entire User Account|

#### MySQL Database Basic syntax

|S.NO|SYNTAX|DESCRIPTION|
|---|----|-----|
|1.|CREATE DATABASE [db-name];  |To create a new database.|
|2.|SHOW DATABASES;|List out the databases.|
|3.|USE [db-name];|Enter into the specified database.|
|4.|DROP DATABASE [db_name];|To delete the specified database.|

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
|1.|TRUNCATE TABLE table_name;|It is used to delete the data inside a table.|
|2.|SHOW TABLES; | List out all the tables in specified database.|
|3.|RENAME old_table TO new_table;| To rename the name of the table|
|4.|DESC table_name|Describe the specified table details.|
|5.|DROP TABLE  table_name;|It is used to delete complete the data in the table.|
|6.|DELETE FROM table_name WHERE condition; |To delete the row of the table using where condition.|
|7.|SELECT column1, column2, ...FROM table_name; |To view the specified colums details in specified table.|
|8.|SELECT * FROM table_name; |To view a details of the entire specified table.|

### Reference:-

For more details visit this page - https://www.javatpoint.com/mysql-tutorial
