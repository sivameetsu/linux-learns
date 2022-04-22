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
sudo mysql_secure_installtion
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
    
**How to Create New MySQL User**

|S.NO|SYNTAX|DESCRIPTION|
|---|----|-----|
|1.|CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';| Create a new user|
|2.|GRANT permission_type ON database.table TO 'username'@'localhost';| to grant privileges to a user account |
|3.|GRANT INSERT ON * . * TO 'username'@'localhost';|to grant insert privileges to a MySQL user|
|4.|SHOW GRANTS FOR username;|To display all the current privileges held by a user|
|5.|GRANT ALL PRIVILEGES ON *.* TO 'database_user'@'localhost';|To grant all privileges to MySQL User on all databases|
|6.|GRANT ALL PRIVILEGES ON database_name.* TO 'database_user'@'localhost';|To grant all privileges to a user account on a specific database|
|7.|GRANT ALL PRIVILEGES ON database_name.table_name TO 'database_user'@'localhost';|To grant all privileges to a user account over a specific table from a database |
|8.|REVOKE permission_type ON database.table TO 'username'@'localhost';|Revoke Privileges MySQL User Account|
|9.|DROP USER 'username'@'localhost';|Remove an Entire User Account|


![image](https://user-images.githubusercontent.com/98270930/164440513-e8d7f900-461d-4db9-9382-62d153b1f232.png)

![image](https://user-images.githubusercontent.com/98270930/164442717-9d8699bc-d67a-42b8-b779-63d3e06c57c8.png)

![image](https://user-images.githubusercontent.com/98270930/164443627-9caf820a-68d6-4626-a5f2-8d96b4578ee5.png)

![image](https://user-images.githubusercontent.com/98270930/164444271-ae4a6350-2c79-47c6-b928-75de64fd624e.png)


#### MySQL Database Basic syntax

|S.NO|SYNTAX|DESCRIPTION|
|---|----|-----|
|1.|CREATE DATABASE [db-name];  |To create a new database.|
|2.|SHOW DATABASES;|List out the databases.|
|3.|USE [db-name];|Enter into the specified database.|
|4.|DROP DATABASE [db_name];|To delete the specified database.|


#### Output 

![image](https://user-images.githubusercontent.com/98270930/164432767-f103370c-7ba6-42c6-9d05-5f881fb1b58e.png)

 ![image](https://user-images.githubusercontent.com/98270930/164433044-e189e893-5549-4b81-8f05-42d63a4506a6.png)

 ![image](https://user-images.githubusercontent.com/98270930/164433288-a061e2e5-26aa-4b93-90fe-cdb70cd822ec.png)
 
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

![image](https://user-images.githubusercontent.com/98270930/164617301-b93b1806-e354-4f14-a079-8439e092c3ea.png)

![image](https://user-images.githubusercontent.com/98270930/164617414-dbe67257-ba14-4cd9-b15e-461243a86151.png)

![image](https://user-images.githubusercontent.com/98270930/164617506-d45b25d2-cb2c-4d5e-bd36-141c0e300a0b.png)

![image](https://user-images.githubusercontent.com/98270930/164618028-e9a74e1b-559f-4d31-8dfb-276aedc3ec0a.png)


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
