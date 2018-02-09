## *SQL DML clauses*  

#### Data Manipulation Language (DML) which deals with data manipulation and is used to store, modify, retrieve, delete and update data in a database.

* `SELECT` - [retrieve data from a database]()
* `INSERT` - [insert data into a table](https://www.w3schools.com/sql/sql_insert.asp)
* `UPDATE` -[updates existing data within a table]()
* `DELETE` - [Delete all records from a database table]()
* `MERGE` - [UPSERT operation (insert or update)]()
* `CALL` - [call a PL/SQL or Java subprogram]()
* `EXPLAIN PLAN` - [interpretation of the data access path]()
* `LOCK TABLE` - [concurrency Control]()


### Excersise :

#### 1. Write a SQL statement to insert a record with your own value into the table countries against each columns.
```SQL
Here in the following is the structure of the table countries.

+--------------+---------------+------+-----+---------+-------+
| Field        | Type          | Null | Key | Default | Extra |
+--------------+---------------+------+-----+---------+-------+
| COUNTRY_ID   | varchar(2)    | YES  |     | NULL    |       |
| COUNTRY_NAME | varchar(40)   | YES  |     | NULL    |       |
| REGION_ID    | decimal(10,0) | YES  |     | NULL    |       |
+--------------+---------------+------+-----+---------+-------+
```
#### Answer :-  
```SQL
INSERT INTO countries values(1,'india',1);
```
#### Output :
```SQL
mysql> select * from countries;
+------------+--------------+-----------+
| COUNTRY_ID | COUNTRY_NAME | REGION_ID |
+------------+--------------+-----------+
| 1          | india        |         1 |
+------------+--------------+-----------+
```
#### 2.  Write a SQL statement to insert one row into the table countries against the column country_id and country_name.
```SQL
Here in the following is the structure of the table countries.

+--------------+---------------+------+-----+---------+-------+
| Field        | Type          | Null | Key | Default | Extra |
+--------------+---------------+------+-----+---------+-------+
| COUNTRY_ID   | varchar(2)    | YES  |     | NULL    |       |
| COUNTRY_NAME | varchar(40)   | YES  |     | NULL    |       |
| REGION_ID    | decimal(10,0) | YES  |     | NULL    |       |
+--------------+---------------+------+-----+---------+-------+
```
#### Answer :-  
```SQL
INSERT INTO countries(COUNTRY_ID, COUNTRY_NAME) values(2,'AUS');
```
#### Output :
```SQL
    mysql> SELECT * FROM countries;
+------------+--------------+-----------+
| COUNTRY_ID | COUNTRY_NAME | REGION_ID |
+------------+--------------+-----------+
| 1          | india        |         1 |
| 2          | AUS          |      NULL |
+------------+--------------+-----------+
```

#### 3. Write a SQL statement to create duplicate of countries table named country_new with all structure and data.
```SQL
Here in the following is the structure of the table countries.

+--------------+---------------+------+-----+---------+-------+
| Field        | Type          | Null | Key | Default | Extra |
+--------------+---------------+------+-----+---------+-------+
| COUNTRY_ID   | varchar(2)    | YES  |     | NULL    |       |
| COUNTRY_NAME | varchar(40)   | YES  |     | NULL    |       |
| REGION_ID    | decimal(10,0) | YES  |     | NULL    |       |
+--------------+---------------+------+-----+---------+-------+
```
#### Answer :-  
 ```SQL
 CREATE TABLE country_new AS select * from countries;
```
#### Output :
```SQL
 mysql> select * from country_new;
+------------+--------------+-----------+
| COUNTRY_ID | COUNTRY_NAME | REGION_ID |
+------------+--------------+-----------+
| 1          | india        |         1 |
| 2          | AUS          |      NULL |
+------------+--------------+-----------+
```
#### 4. Write a SQL statement to insert NULL values against region_id column for a row of countries table.

#### Answer :-
```SQL
 INSERT INTO countries values(3,'Brazil',NULL);
```
#### Output :
```SQL
mysql> select * from countries;
+------------+--------------+-----------+
| COUNTRY_ID | COUNTRY_NAME | REGION_ID |
+------------+--------------+-----------+
| 1          | india        |         1 |
| 2          | AUS          |      NULL |
| 3          | Brazil       |      NULL |
+------------+--------------+-----------+
```
#### 5. Write a SQL statement to insert 3 rows by a single insert statement.

#### Answer :-
```SQL
INSERT INTO countries values(4,'pakistan',4),(5,'AUS',5),(6,'INDIA',6);
```
#### Answer :-
```SQL
mysql> DESC COUNTRIES;
+--------------+---------------+------+-----+---------+-------+
| Field        | Type          | Null | Key | Default | Extra |
+--------------+---------------+------+-----+---------+-------+
| COUNTRY_ID   | varchar(2)    | YES  |     | NULL    |       |
| COUNTRY_NAME | varchar(40)   | YES  |     | NULL    |       |
| REGION_ID    | decimal(10,0) | YES  |     | NULL    |       |
+--------------+---------------+------+-----+---------+-------+
```

#### 6. Write a SQL statement insert rows from country_new table to countries table.
```sql
Here is the rows for country_new table. Assume that, the countries table is empty.

+------------+--------------+-----------+
| COUNTRY_ID | COUNTRY_NAME | REGION_ID |
+------------+--------------+-----------+
| C0001      | India        |      1001 |
| C0002      | USA          |      1007 |
| C0003      | UK           |      1003 |
+------------+--------------+-----------+
```
#### Answer :-
```SQL
INSERT INTO countries select * from country_new;
```
#### Answer :-
```SQL
mysql> select * from countries;
+------------+--------------+-----------+
| COUNTRY_ID | COUNTRY_NAME | REGION_ID |
+------------+--------------+-----------+
| C001       | india        |      1001 |
| C002       | USA          |      1007 |
| C003       | UK           |      1003 |
+------------+--------------+-----------+
```

#### 7. Write a SQL statement to insert one row in jobs table to ensure that no duplicate value will be entered in the job_id column.

#### Answer :-
```SQL
mysql> desc jobs;
+-------------+-------------+------+-----+---------+-------+
| Field       | Type        | Null | Key | Default | Extra |
+-------------+-------------+------+-----+---------+-------+
| job_id      | int(11)     | NO   | PRI | NULL    |       |
| job_title   | varchar(50) | YES  |     | NULL    |       |
| min_salalry | int(11)     | YES  |     | NULL    |       |
| max_salary  | int(11)     | YES  |     | NULL    |       |
+-------------+-------------+------+-----+---------+-------+
```
```SQL
INSERT INTO jobs values(1,'INTERN',20000,50000);
```
#### Output :-
```SQL
mysql> select * from jobs;
+--------+-----------+-------------+------------+
| job_id | job_title | min_salalry | max_salary |
+--------+-----------+-------------+------------+
|      1 | INTERN    |       20000 |      50000 |
|      2 | INTERN    |       20000 |      50000 |
+--------+-----------+-------------+------------+

mysql> INSERT INTO jobs values(2,'INTERN',20000,50000);
ERROR 1062 (23000): Duplicate entry '2' for key 'PRIMARY'

```

#### 8. Write a SQL statement to insert one row in jobs table to ensure that no duplicate value will be entered in the job_id column.

#### Answer :-
```SQL
mysql> desc jobs;
+-------------+-------------+------+-----+---------+-------+
| Field       | Type        | Null | Key | Default | Extra |
+-------------+-------------+------+-----+---------+-------+
| job_id      | int(11)     | NO   | PRI | NULL    |       |
| job_title   | varchar(50) | YES  |     | NULL    |       |
| min_salalry | int(11)     | YES  |     | NULL    |       |
| max_salary  | int(11)     | YES  |     | NULL    |       |
+-------------+-------------+------+-----+---------+-------+
```
```SQL
INSERT INTO jobs values(3,'INTERN',20000,50000);
```
#### Output :-
```SQL
mysql> select * from jobs;
+--------+-----------+-------------+------------+
| job_id | job_title | min_salalry | max_salary |
+--------+-----------+-------------+------------+
|      1 | INTERN    |       20000 |      50000 |
|      2 | INTERN    |       20000 |      50000 |
|      3 | INTERN    |       20000 |      50000 |
+--------+-----------+-------------+------------+
3 rows in set (0.00 sec)

mysql> INSERT INTO jobs values(3,'INTERN',20000,50000);
ERROR 1062 (23000): Duplicate entry '3' for key 'PRIMARY'

```
#### 9. Write a SQL statement to insert a record into the table countries to ensure that, a country_id and region_id combination will be entered once in the table.

#### Answer :-
``Assuming countri table stuctures``
```sql
CREATE TABLE IF NOT EXISTS COUNTRIES(
  `COUNTRY_ID` VARCHAR(5) UNIQUE NOT NULL,
  `COUNTRY_NAME` VARCHAR(40),
  `REGION_ID` DECIMAL(10,0) UNIQUE NOT NULL
);
```
``Table stuctures is ``
```SQL
mysql> desc countries;
+--------------+---------------+------+-----+---------+-------+
| Field        | Type          | Null | Key | Default | Extra |
+--------------+---------------+------+-----+---------+-------+
| COUNTRY_ID   | varchar(5)    | NO   | PRI | NULL    |       |
| COUNTRY_NAME | varchar(40)   | YES  |     | NULL    |       |
| REGION_ID    | decimal(10,0) | NO   | UNI | NULL    |       |
+--------------+---------------+------+-----+---------+-------+
```
``Insert data into table countries``
```SQL
INSERT INTO countries VALUES(1,'india',1);
INSERT INTO countries VALUES(2,'india',2);
INSERT INTO countries VALUES(3,'india',3);
```
#### Output :-
```SQL
mysql> select * from countries;
+------------+--------------+-----------+
| COUNTRY_ID | COUNTRY_NAME | REGION_ID |
+------------+--------------+-----------+
| 1          | india        |         1 |
| 2          | india        |         2 |
| 3          | india        |         3 |
+------------+--------------+-----------+
```
``if you enter duplicate value it shows error``
```sql
mysql> insert into countries values(3,'india',3);
ERROR 1062 (23000): Duplicate entry '3' for key 'COUNTRY_ID'
```

#### 10. Write a SQL statement to insert rows into the table countries in which the value of country_id column will be unique and auto incremented.


#### Answer :-
``Assuming countri table stuctures``
```sql
CREATE TABLE IF NOT EXISTS COUNTRIES(
  `COUNTRY_ID` INT(5) UNIQUE NOT NULL AUTO_INCREMENT,
  `COUNTRY_NAME` VARCHAR(40),
  `REGION_ID` DECIMAL(10,0) UNIQUE NOT NULL
);
```
``Table stuctures is ``
```SQL
mysql> DESC COUNTRIES;
+--------------+---------------+------+-----+---------+----------------+
| Field        | Type          | Null | Key | Default | Extra          |
+--------------+---------------+------+-----+---------+----------------+
| COUNTRY_ID   | int(5)        | NO   | PRI | NULL    | auto_increment |
| COUNTRY_NAME | varchar(40)   | YES  |     | NULL     |                |
| REGION_ID    | decimal(10,0) | NO   | UNI | NULL    |                |
+--------------+---------------+------+-----+---------+----------------+
```
``Insert data in table countries``
```SQL
INSERT INTO countries VALUES(4,'AUS',4);
```

#### Output :-
```SQL
mysql> select * from countries;
+------------+--------------+-----------+
| COUNTRY_ID | COUNTRY_NAME | REGION_ID |
+------------+--------------+-----------+
| 1          | india        |         1 |
| 2          | india        |         2 |
| 3          | india        |         3 |
| 4          | AUS          |         4 |
+------------+--------------+-----------+
```
#### 11. Write a SQL statement to insert records into the table countries to ensure that the country_id column will not contain any duplicate data and this will be automatically incremented and the column country_name will be filled up by 'N/A' if no value assigned for that column.

#### Answer :-
``Assuming countri table stuctures``
```sql
CREATE TABLE IF NOT EXISTS COUNTRIES(
  `COUNTRY_ID` INT(5) PRIMARY KEY AUTO_INCREMENT,
  `COUNTRY_NAME` VARCHAR(40) DEFAULT 'N/A',
  `REGION_ID` DECIMAL(10,0) UNIQUE NOT NULL
);
```
``Table stuctures is ``
```SQL
mysql> DESC COUNTRIES;
+--------------+---------------+------+-----+---------+----------------+
| Field        | Type          | Null | Key | Default | Extra          |
+--------------+---------------+------+-----+---------+----------------+
| COUNTRY_ID   | int(5)        | NO   | PRI | NULL    | auto_increment |
| COUNTRY_NAME | varchar(40)   | YES  |     | N/A     |                |
| REGION_ID    | decimal(10,0) | NO   | UNI | NULL    |                |
+--------------+---------------+------+-----+---------+----------------+
```
``Insert data in table countries``
```SQL
INSERT INTO countries(COUNTRY_ID,REGION_ID) VALUES(6,6);
```

#### Output :-
```SQL
mysql> SELECT * FROM COUNTRIES;
+------------+--------------+-----------+
| COUNTRY_ID | COUNTRY_NAME | REGION_ID |
+------------+--------------+-----------+
|          6 | N/A          |         6 |
+------------+--------------+-----------+
```
#### 12. Write a SQL statement to insert rows in the job_history table in which one column job_id is containing those values which are exists in job_id column of jobs table.

#### Answer :-
``Assuming JOBS table stuctures``
```sql
CREATE TABLE `JOBS` (
  `job_id` INT PRIMARY KEY,
  `job_title` VARCHAR(50),
  `min_salalry` INT,
  `max_salary` INT CHECK(max_salary < 25000)
  );
```
``Table stuctures is ``
```SQL
mysql> DESC JOBS;
+-------------+-------------+------+-----+---------+-------+
| Field       | Type        | Null | Key | Default | Extra |
+-------------+-------------+------+-----+---------+-------+
| job_id      | int(11)     | NO   | PRI | NULL    |       |
| job_title   | varchar(50) | YES  |     | NULL    |       |
| min_salalry | int(11)     | YES  |     | NULL    |       |
| max_salary  | int(11)     | YES  |     | NULL    |       |
+-------------+-------------+------+-----+---------+-------+
```
``Assuming JOB_HISTORY table stuctures``
```sql
  CREATE TABLE `job_history`(
    `employee_id` INT,
    `start_date` DATE,
    `end_date` DATE NOT NULL CHECK(`end_date` LIKE `--/--/----`),
    `job_id` INT,
    `department_id` INT,
    FOREIGN KEY(job_id) REFERENCES JOBS(job_id)
    );
```
``Table stuctures is ``
```SQL
mysql> desc job_history;
+---------------+---------+------+-----+---------+-------+
| Field         | Type    | Null | Key | Default | Extra |
+---------------+---------+------+-----+---------+-------+
| employee_id   | int(11) | YES  |     | NULL    |       |
| start_date    | date    | YES  |     | NULL    |       |
| end_date      | date    | NO   |     | NULL    |       |
| job_id        | int(11) | YES  | MUL | NULL    |       |
| department_id | int(11) | YES  |     | NULL    |       |
+---------------+---------+------+-----+---------+-------+
```
``insert data into jobs table ``
```sql
INSERT INTO jobs VALUES(1,'intern',2000,6000);
```
`` insert data into job_history table if job_id exists in jobs table``
```sql
INSERT INTO job_history VALUES(1,'2018/2/2','2018/3/3',1,4);
```
#### Output :-
```SQL
mysql> SELECT * FROM job_history;
+-------------+------------+------------+--------+---------------+
| employee_id | start_date | end_date   | job_id | department_id |
+-------------+------------+------------+--------+---------------+
|           1 | 2018-02-02 | 2018-03-03 |      1 |             4 |
+-------------+------------+------------+--------+---------------+
```
#### 13. Write a SQL statement to insert rows into the table employees in which a set of columns department_id and manager_id contains a unique value and that combined values must have exists into the table departments.

#### Answer :-

``Assuming Departments table stuctures``
```sql
 CREATE TABLE departments(
 department_id decimal(4,0) NOT NULL DEFAULT '0',
 department_name varchar(30) NOT NULL,
 manager_id decimal(6,0) NOT NULL DEFAULT '0',
 location_id decimal(4,0),
 PRIMARY KEY(department_id, manager_id)
 );
```
``Table stuctures is ``
```SQL
mysql> desc departments;
+-----------------+--------------+------+-----+---------+-------+
| Field           | Type         | Null | Key | Default | Extra |
+-----------------+--------------+------+-----+---------+-------+
| department_id   | decimal(4,0) | NO   | PRI | 0       |       |
| department_name | varchar(30)  | NO   |     | NULL    |       |
| manager_id      | decimal(6,0) | NO   | PRI | 0       |       |
| location_id     | decimal(4,0) | YES  |     | NULL    |       |
+-----------------+--------------+------+-----+---------+-------+
```
``Assuming employee table stuctures``
```sql
CREATE TABLE employee(
    `employee_name` VARCHAR(40),
    `employee_id` INT PRIMARY KEY,
    `department_id` decimal(4,0),
    `manager_id` decimal(6,0),
    FOREIGN KEY(department_id) REFERENCES departments(department_id),
    FOREIGN KEY(manager_id) REFERENCES departments(manager_id)
);
```
``Table stuctures is ``
```SQL
mysql> desc employee;
+---------------+--------------+------+-----+---------+-------+
| Field         | Type         | Null | Key | Default | Extra |
+---------------+--------------+------+-----+---------+-------+
| employee_id   | int(11)      | NO   | PRI | NULL    |       |
| employee_name | varchar(40)  | YES  |     | NULL    |       |
| department_id | decimal(4,0) | YES  | MUL | NULL    |       |
| manager_id    | decimal(6,0) | NO   | MUL | NULL    |       |
+---------------+--------------+------+-----+---------+-------+
```

``insert data into department table ``
```sql
 INSERT INTO departments VALUES(1,'COMPUTER',1,23);
```
``output is : ``
```SQL
mysql> SELECT * FROM departments;
+---------------+-----------------+------------+-------------+
| department_id | department_name | manager_id | location_id |
+---------------+-----------------+------------+-------------+
|             1 | COMPUTER        |          1 |          23 |
+---------------+-----------------+------------+-------------+
```
`insert data into department table ``
```sql
INSERT INTO employee VALUES(1,'Rahul',1,1);
```
``output is : ``
```SQL
mysql> select * from employee;
+-------------+---------------+---------------+------------+
| employee_id | employee_name | department_id | manager_id |
+-------------+---------------+---------------+------------+
|           1 | Rahul         |             1 |          1 |
+-------------+---------------+---------------+------------+
```
``error when department_id or manager_id not availabe in departments table``
```SQL
mysql> INSERT INTO employee VALUES(2,'Rahul',2,3);
ERROR 1452 (23000): Cannot add or update a child row: a foreign key constraint fails (`dml`.`employee`, CONSTRAINT `employee_ibfk_1` FOREIGN KEY (`department_id`) REFERENCES `departments` (`department_id`))
```

#### 14. Write a SQL statement to insert rows into the table employees in which a set of columns department_id and job_id contains the values which must have exists into the table departments and jobs.


#### Answer :-
``Assuming Departments table stuctures``
```sql
 CREATE TABLE departments(
 department_id decimal(4,0) NOT NULL DEFAULT '0',
 department_name varchar(30) NOT NULL,
 manager_id decimal(6,0) NOT NULL DEFAULT '0',
 location_id decimal(4,0),
 PRIMARY KEY(department_id, manager_id)
 );
```
``Table stuctures is ``
```SQL
mysql> desc departments;
+-----------------+--------------+------+-----+---------+-------+
| Field           | Type         | Null | Key | Default | Extra |
+-----------------+--------------+------+-----+---------+-------+
| department_id   | decimal(4,0) | NO   | PRI | 0       |       |
| department_name | varchar(30)  | NO   |     | NULL    |       |
| manager_id      | decimal(6,0) | NO   | PRI | 0       |       |
| location_id     | decimal(4,0) | YES  |     | NULL    |       |
+-----------------+--------------+------+-----+---------+-------+
```
``Assuming JOBS table stuctures``
```sql
 CREATE TABLE `jobs` (
  `job_id` int(11) NOT NULL,
  `job_title` varchar(50) DEFAULT NULL,
  `min_salalry` int(11) DEFAULT NULL,
  `max_salary` int(11) DEFAULT NULL,
  PRIMARY KEY (`job_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```
``Table stuctures is ``
```SQL
mysql> DESC jobs;
+-------------+-------------+------+-----+---------+-------+
| Field       | Type        | Null | Key | Default | Extra |
+-------------+-------------+------+-----+---------+-------+
| job_id      | int(11)     | NO   | PRI | NULL    |       |
| job_title   | varchar(50) | YES  |     | NULL    |       |
| min_salalry | int(11)     | YES  |     | NULL    |       |
| max_salary  | int(11)     | YES  |     | NULL    |       |
+-------------+-------------+------+-----+---------+-------+
```
``Assuming employee table stuctures``
```sql
CREATE TABLE employee(
    `employee_name` VARCHAR(40),
    `employee_id` INT PRIMARY KEY,
    `department_id` decimal(4,0),
    `manager_id` decimal(6,0),
    `job_id` int(11) NOT NULL,
    FOREIGN KEY(department_id) REFERENCES departments(department_id),
    FOREIGN KEY(manager_id) REFERENCES departments(manager_id),
    FOREIGN KEY(job_id) REFERENCES jobs(job_id)
);
```
``Table stuctures is ``
```SQL
mysql> DESC EMPLOYEE;
+---------------+--------------+------+-----+---------+-------+
| Field         | Type         | Null | Key | Default | Extra |
+---------------+--------------+------+-----+---------+-------+
| employee_id   | int(11)      | NO   | PRI | NULL    |       |
| employee_name | varchar(40)  | YES  |     | NULL    |       |
| department_id | decimal(4,0) | YES  | MUL | NULL    |       |
| manager_id    | decimal(6,0) | NO   | UNI | NULL    |       |
| job_id        | int(11)      | YES  | MUL | NULL    |       |
+---------------+--------------+------+-----+---------+-------+
```
`insert data into department table ``
```sql
INSERT INTO employee values(1,'rahul',1,1,1);
```
``output is : ``
```SQL
mysql> select * from employee;
+-------------+---------------+---------------+------------+--------+
| employee_id | employee_name | department_id | manager_id | job_id |
+-------------+---------------+---------------+------------+--------+
|           1 | rahul         |             1 |          1 |      1 |
+-------------+---------------+---------------+------------+--------+
```
``error when department_id or job_id not availabe in departments table or jobs table``
```SQL
mysql> INSERT INTO employee VALUES(2,'Rahul',2,3,2);
ERROR 1452 (23000): Cannot add or update a child row: a foreign key constraint fails (`dml`.`employee`, CONSTRAINT `employee_ibfk_1` FOREIGN KEY (`department_id`) REFERENCES `departments` (`department_id`))
```
