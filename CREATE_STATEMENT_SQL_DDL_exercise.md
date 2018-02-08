## *SQL DDL clauses*

#### Data Definition Language (DDL) commands are used to define or alter the structure of the database.

* `CREATE`: [To create databases and database objects](https://www.w3schools.com/sql/sql_create_table.asp)
* `ALTER` : [To alter existing database objects](https://www.w3schools.com/sql/sql_alter.asp)
* `DROP`  : [To drop databases and databases objects](https://www.w3schools.com/sql/sql_drop_table.asp)
* `TRUNCATE` : [To remove all records from a table but not its database structure]()
* `COMMENT`: [To add comments to the data dictionary]()
* `RENAME` : [To rename database objects](tables/views/procedures)


* `CREATE`: [To create databases and database objects](https://www.w3schools.com/sql/sql_create_table.asp)

### Excersise

#### 1. Write a SQL statement to create a simple table countries including columns country_id,country_name and region_id

#### Answer :-  
```no-highlight
CREATE TABLE `countries` (
      `country_id` INT,
      `country_name` VARCHAR(30),
      `region_id` INT );
      ```
#### Output :

```no-highlight

 mysql> desc countries;
+--------------+-------------+------+-----+---------+-------+
| Field        | Type        | Null | Key | Default | Extra |
+--------------+-------------+------+-----+---------+-------+
| country_id   | int(11)     | YES  |     | NULL    |       |
| country_name | varchar(30) | YES  |     | NULL    |       |
| region_id    | int(11)     | YES  |     | NULL    |       |
+--------------+-------------+------+-----+---------+-------+

```


#### 2. Write a SQL statement to create a simple table countries including columns country_id,country_name and region_id which is already exists.

#### Answer :-  
```no-highlight
DROP TABLE IF EXISTS `countries`;
CREATE TABLE `countries` (
      `country_id` INT,
      `country_name` VARCHAR(30),
      `region_id` INT );
      ```
#### Output :

```no-highlight
 mysql> desc countries;
+--------------+-------------+------+-----+---------+-------+
| Field        | Type        | Null | Key | Default | Extra |
+--------------+-------------+------+-----+---------+-------+
| country_id   | int(11)     | YES  |     | NULL    |       |
| country_name | varchar(30) | YES  |     | NULL    |       |
| region_id    | int(11)     | YES  |     | NULL    |       |
+--------------+-------------+------+-----+---------+-------+
```

#### 3. Write a SQL statement to create the structure of a table dup_countries similar to countries.

#### Answer :-  
```no-highlight
   CREATE TABLE `dup_countries` LIKE `countries`;

  ```
#### Output :

```no-highlight
mysql> desc dup_countries;
+--------------+-------------+------+-----+---------+-------+
| Field        | Type        | Null | Key | Default | Extra |
+--------------+-------------+------+-----+---------+-------+
| country_id   | int(11)     | YES  |     | NULL    |       |
| country_name | varchar(30) | YES  |     | NULL    |       |
| region_id    | int(11)     | YES  |     | NULL    |       |
+--------------+-------------+------+-----+---------+-------+
```

#### 4. Write a SQL statement to create the structure of a table dup_countries similar to countries.
#### Answer :-
```no-highlight
  CREATE TABLE `dup_countries` AS SELECT * FROM `countries`;
```
#### Output :
```no-highlight
mysql> desc dup_countries;
+--------------+-------------+------+-----+---------+-------+
| Field        | Type        | Null | Key | Default | Extra |
+--------------+-------------+------+-----+---------+-------+
| country_id   | int(11)     | YES  |     | NULL    |       |
| country_name | varchar(30) | YES  |     | NULL    |       |
| region_id    | int(11)     | YES  |     | NULL    |       |
+--------------+-------------+------+-----+---------+-------+

mysql> select * from dup_countries;
+------------+--------------+-----------+
| country_id | country_name | region_id |
+------------+--------------+-----------+
|          1 | India        |         1 |
|          2 | USA          |         2 |
+------------+--------------+-----------+

```

#### 5. Write a SQL statement to create a table countries set a constraint NULL.

#### Answer :-
```no-highlight
    CREATE TABLE `countries` (
      `country_id` INT DEFAULT NULL,
      `country_name` VARCHAR(30) DEFAULT NULL,
      `region_id` INT DEFAULT NULL
      );

```
#### Output :
```no-highlight
mysql> desc countries;
+--------------+-------------+------+-----+---------+-------+
| Field        | Type        | Null | Key | Default | Extra |
+--------------+-------------+------+-----+---------+-------+
| country_id   | int(11)     | YES  |     | NULL    |       |
| country_name | varchar(30) | YES  |     | NULL    |       |
| region_id    | int(11)     | YES  |     | NULL    |       |
+--------------+-------------+------+-----+---------+-------+
```

#### 6. Write a SQL statement to create a table named jobs including columns job_id, job_title, min_salary, max_salary and check whether the max_salary amount exceeding the upper limit 25000.

#### Answer :-
```no-highlight
   CREATE TABLE `jobs` (
     `job_id` INT,
     `job_title` VARCHAR(50),
     `min_salalry` INT,
     `max_salary` INT CHECK(max_salary < 25000)
     );
```
#### Output :
```no-highlight
mysql> desc jobs;
+-------------+-------------+------+-----+---------+-------+
| Field       | Type        | Null | Key | Default | Extra |
+-------------+-------------+------+-----+---------+-------+
| job_id      | int(11)     | YES  |     | NULL    |       |
| job_title   | varchar(50) | YES  |     | NULL    |       |
| min_salalry | int(11)     | YES  |     | NULL    |       |
| max_salary  | int(11)     | YES  |     | NULL    |       |
+-------------+-------------+------+-----+---------+-------+
```

#### 7. Write a SQL statement to create a table named countries including columns country_id, country_name and region_id and make sure that no countries except Italy, India and China will be entered in the table.
#### Answer :-
```no-highlight
    CREAT TABLE `countries`(
    	`country_id` INT,
    	`country_name` ENUM('Italy',"India','China'),
    	`region_id` INT
    	);
```

#### 8. Write a SQL statement to create a table named job_history including columns employee_id, start_date, end_date, job_id and department_id and make sure that the value against column end_date will be entered at the time of insertion to the format like '--/--/----'.

#### Answer :-
```no-highlight
    CREATE TABLE `job_history`(
    	`employee_id` INT,
    	`start_date` DATE,
    	`end_date` DATE NOT NULL CHECK(`end_date` LIKE `--/--/----`),
    	`job_id` INT,
    	`department_id` INT
    	);
```

#### 9. Write a SQL statement to create a table named countries including columns country_id,country_name and region_id and make sure that no duplicate data against column country_id will be allowed at the time of insertion.
#### Answer :-
```no-highlight
    CREAT TABLE `countries`(
    	`country_id` INT UNIQUE,
    	`country_name` ENUM('Italy',"India','China'),
    	`region_id` INT
    	);  
```
#### ```OR```
```no-highlight
CREAT TABLE `countries`(
 `country_id` INT PRIMARY KEY,
 `country_name` ENUM('Italy',"India','China'),
 `region_id` INT
 );  
```
#### 10. Write a SQL statement to create a table named jobs including columns job_id, job_title, min_salary and max_salary, and make sure that, the default value for job_title is blank and min_salary is 8000 and max_salary is NULL will be entered automatically at the time of insertion if no value assigned for the specified columns.
#### Answer :-
```no-highlight
CREATE TABLE `jobs` (
     `job_id` INT,
     `job_title` VARCHAR(50) DEFAULT NULL,
     `min_salalry` INT DEFAULT 8000,
     `max_salary` INT DEFAULT NULL CHECK(max_salary < 25000)
     );
```
#### 11. Write a SQL statement to create a table named countries including columns country_id, country_name and region_id and make sure that the country_id column will be a key field which will not contain any duplicate data at the time of insertion.
#### Answer :-
```no-highlight
      CREAT TABLE `countries`(
      	`country_id` INT PRIMARY KEY,
      	`country_name` ENUM('Italy',"India','China'),
      	`region_id` INT
      	);  
```
#### 12. Write a SQL statement to create a table countries including columns country_id, country_name and region_id and make sure that the column country_id will be unique and store an auto incremented value.
#### Answer :-
```no-highlight
CREAT TABLE `countries`(
	`country_id` INT PRIMARY KEY AUTO_INCREMENT,
	`country_name` ENUM('Italy',"India','China'),
	`region_id` INT
	);  
```

#### 13. Write a SQL statement to create a table countries including columns country_id, country_name and region_id and make sure that the combination of columns country_id and region_id will be unique.

#### Answer :-
```no-highlight
      CREAT TABLE `countries`(
      	`country_id` INT PRIMARY KEY AUTO_INCREMENT,
      	`country_name` ENUM('Italy',"India','China'),
      	`region_id` INT UNIQUE
      	);  
```

#### 14. Write a SQL statement to create a table job_history including columns employee_id, start_date, end_date, job_id and department_id and make sure that, the employee_id column does not contain any duplicate value at the time of insertion and the foreign key column job_id contain only those values which are exists in the jobs table.
```no-highlight
Here is the structure of the table jobs;

+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| JOB_ID     | varchar(10)  | NO   | PRI |         |       |
| JOB_TITLE  | varchar(35)  | NO   |     | NULL    |       |
| MIN_SALARY | decimal(6,0) | YES  |     | NULL    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+
```
#### Answer :-
```no-highlight
      CREATE TABLE `job_history`(
       `employee_id` INT UNIQUE,
       `start_date` DATE,
       `end_date` DATE FORMAT 'DD/MM/YYYY',
       `job_id` INT,
       `department_id` INT,
       FOREIGN KEY(`job_id`) REFERENCES jobs(`job_id`)
       );

```

#### 15. Write a SQL statement to create a table employees including columns employee_id, first_name, last_name, email, phone_number hire_date, job_id, salary, commission, manager_id and department_id and make sure that, the employee_id column does not contain any duplicate value at the time of insertion and the foreign key columns combined by department_id and manager_id columns contain only those unique combination values, which combinations are exists in the departments table.
```no-highlight
Assume the structure of departments table below.

+-----------------+--------------+------+-----+---------+-------+
| Field           | Type         | Null | Key | Default | Extra |
+-----------------+--------------+------+-----+---------+-------+
| DEPARTMENT_ID   | decimal(4,0) | NO   | PRI | 0       |       |
| DEPARTMENT_NAME | varchar(30)  | NO   |     | NULL    |       |
| MANAGER_ID      | decimal(6,0) | NO   | PRI | 0       |       |
| LOCATION_ID     | decimal(4,0) | YES  |     | NULL    |       |
+-----------------+--------------+------+-----+---------+-------+
```
#### Answer :-
```no-highlight
CREATE TABLE `employees`(
	`employee_id` INT PRIMARY KEY,
	`first_name` VARCHAR(50),
	`last_name` VARCHAR(50),
	`email` VARCHAR(30),
	`phone_number` BIGINT(10),
	`hire_date` DATE,
	`job_id` INT,
	`salary` INT,
	`commission` INT,
	`manager_id` INT,
	`departmnet_id` INT,
	FOREIGN KEY(`department_id`) REFERENCES department

(`department_id`),
	FOREIGN KEY(`manager_id`) REFERENCES department

(`manager_id`),
	FOREIGN KEY(`job_id`) REFERENCES jobs(`job_id`)

);
-----------------------------------------------
CREATE TABLE `departments` (
	`department_id` INT PRIMARY KEY,
	`department_name` VARCHAR(30) NOT NULL,
	`manager_id` INT UNIQUE,
 	`location_id` INT
);

```

#### 16. Write a SQL statement to create a table employees including columns employee_id, first_name, last_name, email, phone_number hire_date, job_id, salary, commission, manager_id and department_id and make sure that, the employee_id column does not contain any duplicate value at the time of insertion, and the foreign key column department_id, reference by the column department_id of departments table, can contain only those values which are exists in the departments table and another foreign key column job_id, referenced by the column job_id of jobs table, can contain only those values which are exists in the jobs table. The InnoDB Engine have been used to create the tables.

#### "A foreign key constraint is not required merely to join two tables. For storage engines other than InnoDB, it is possible when defining a column to use a REFERENCES tbl_name(col_name) clause, which has no actual effect, and serves only as a memo or comment to you that the column which you are currently defining is intended to refer to a column in another table." - Reference [dev.mysql.com](dev.mysql.com)
```no-highlight
Assume that the structure of two tables departments and jobs.

+-----------------+--------------+------+-----+---------+-------+
| Field           | Type         | Null | Key | Default | Extra |
+-----------------+--------------+------+-----+---------+-------+
| DEPARTMENT_ID   | decimal(4,0) | NO   | PRI | 0       |       |
| DEPARTMENT_NAME | varchar(30)  | NO   |     | NULL    |       |
| MANAGER_ID      | decimal(6,0) | YES  |     | NULL    |       |

| LOCATION_ID     | decimal(4,0) | YES  |     | NULL    |       |
+-----------------+--------------+------+-----+---------+-------+

+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| JOB_ID     | varchar(10)  | NO   | PRI |         |       |
| JOB_TITLE  | varchar(35)  | NO   |     | NULL    |       |
| MIN_SALARY | decimal(6,0) | YES  |     | NULL    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+
```

#### Answer :-
```no-highlight
      CREATE TABLE `employees`(
      `employee_id` INT PRIMARY KEY,
      `first_name` VARCHAR(50),
      `last_name` VARCHAR(50),
      `email` VARCHAR(30),
      `phone_number` BIGINT(10),
      `hire_date` DATE,
      `job_id` INT,
      `salary` INT,
      `commission` INT,
      `manager_id` INT,
      `departmnet_id` INT,
      FOREIGN KEY(`department_id`) REFERENCES department
      (`department_id`),
      FOREIGN KEY(`job_id`) REFERENCES jobs(`job_id`)
      )ENGINE=InnoDB;

```

#### 17. Write a SQL statement to create a table employees including columns employee_id, first_name, last_name, job_id, salary and make sure that, the employee_id column does not contain any duplicate value at the time of insertion, and the foreign key column job_id, referenced by the column job_id of jobs table, can contain only those values which are exists in the jobs table. The InnoDB Engine have been used to create the tables. The specialty of the statement is that, The ON UPDATE CASCADE action allows you to perform cross-table update and ON DELETE RESTRICT action reject the deletion. The default action is ON DELETE RESTRICT.

#### Assume that the structure of the table jobs and InnoDB Engine have been used to create the table jobs.

```no-highlight
CREATE TABLE IF NOT EXISTS jobs (
JOB_ID integer NOT NULL UNIQUE PRIMARY KEY,
JOB_TITLE varchar(35) NOT NULL DEFAULT ' ',
MIN_SALARY decimal(6,0) DEFAULT 8000,
MAX_SALARY decimal(6,0) DEFAULT NULL
)ENGINE=InnoDB;

+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| JOB_ID     | int(11)      | NO   | PRI | NULL    |       |
| JOB_TITLE  | varchar(35)  | NO   |     |         |       |
| MIN_SALARY | decimal(6,0) | YES  |     | 8000    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+

```
#### Answer :-
```no-highlight
  CREATE TABLE `employees`(
       `employee_id` INT PRIMARY KEY,
       `first_name` VARCHAR(50),
       `last_name` VARCHAR(50),
       `job_id` INT,
       `salary` INT,
       FOREIGN KEY(`job_id`) REFERENCES jobs(`job_id`)
      )ENGINE=InnoDB;
```

#### 18.  Write a SQL statement to create a table employees including columns employee_id, first_name, last_name, job_id, salary and make sure that, the employee_id column does not contain any duplicate value at the time of insertion, and the foreign key column job_id, referenced by the column job_id of jobs table, can contain only those values which are exists in the jobs table. The InnoDB Engine have been used to create the tables. The specialty of the statement is that, The ON DELETE CASCADE that lets you allow to delete records in the employees(child) table that refer to a record in the jobs(parent) table when the record in the parent table is deleted and the ON UPDATE RESTRICT actions reject any updates.
```no-highlight
Assume that the structure of the table jobs and InnoDB Engine have been used to create the table jobs.

CREATE TABLE IF NOT EXISTS jobs (
JOB_ID integer NOT NULL UNIQUE PRIMARY KEY,
JOB_TITLE varchar(35) NOT NULL DEFAULT ' ',
MIN_SALARY decimal(6,0) DEFAULT 8000,
MAX_SALARY decimal(6,0) DEFAULT NULL
)ENGINE=InnoDB;

+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| JOB_ID     | int(11)      | NO   | PRI | NULL    |       |
| JOB_TITLE  | varchar(35)  | NO   |     |         |       |
| MIN_SALARY | decimal(6,0) | YES  |     | 8000    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+
```


#### Answer :-
```no-highlight
  CREATE TABLE `employees`(
      `employee_id` INT PRIMARY KEY,
      `first_name` VARCHAR(50),
      `last_name` VARCHAR(50),
      `job_id` INT,
      `salary` INT,
      FOREIGN KEY(`job_id`) REFERENCES jobs(`job_id`)
      )ENGINE=InnoDB;;

```
#### 19.  Write a SQL statement to create a table employees including columns employee_id, first_name, last_name, job_id, salary and make sure that, the employee_id column does not contain any duplicate value at the time of insertion, and the foreign key column job_id, referenced by the column job_id of jobs table, can contain only those values which are exists in the jobs table. The InnoDB Engine have been used to create the tables. The specialty of the statement is that, The ON DELETE SET NULL action will set the foreign key column values in the child table(employees) to NULL when the record in the parent table(jobs) is deleted, with a condition that the foreign key column in the child table must accept NULL values and the ON UPDATE SET NULL action resets the values in the rows in the child table(employees) to NULL values when the rows in the parent table(jobs) are updated.
```no-highlight
Assume that the structure of two table jobs and InnoDB Engine have been used to create the table jobs.

CREATE TABLE IF NOT EXISTS jobs (
JOB_ID integer NOT NULL UNIQUE PRIMARY KEY,
JOB_TITLE varchar(35) NOT NULL DEFAULT ' ',
MIN_SALARY decimal(6,0) DEFAULT 8000,
MAX_SALARY decimal(6,0) DEFAULT NULL
)ENGINE=InnoDB;

+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| JOB_ID     | int(11)      | NO   | PRI | NULL    |       |
| JOB_TITLE  | varchar(35)  | NO   |     |         |       |
| MIN_SALARY | decimal(6,0) | YES  |     | 8000    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+

```
#### Answer :-
```no-highlight
  CREATE TABLE `employees`(
       `employee_id` INT PRIMARY KEY,
       `first_name` VARCHAR(50),
       `last_name` VARCHAR(50),
       `job_id` INT,
       `salary` INT,
       FOREIGN KEY(`job_id`) REFERENCES jobs(`job_id`)
       ON UPDATE SET NULL
       ON DELETE SET NULL
      )ENGINE=InnoDB;;
```

#### 20. Write a SQL statement to create a table employees including columns employee_id, first_name, last_name, job_id, salary and make sure that, the employee_id column does not contain any duplicate value at the time of insertion, and the foreign key column job_id, referenced by the column job_id of jobs table, can contain only those values which are exists in the jobs table. The InnoDB Engine have been used to create the tables. The specialty of the statement is that, The ON DELETE NO ACTION and the ON UPDATE NO ACTION actions will reject the deletion and any updates.
```no-highlight

Assume that the structure of two table jobs and InnoDB Engine have been used to create the table jobs.

CREATE TABLE IF NOT EXISTS jobs (
JOB_ID integer NOT NULL UNIQUE PRIMARY KEY,
JOB_TITLE varchar(35) NOT NULL DEFAULT ' ',
MIN_SALARY decimal(6,0) DEFAULT 8000,
MAX_SALARY decimal(6,0) DEFAULT NULL
)ENGINE=InnoDB;

+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| JOB_ID     | int(11)      | NO   | PRI | NULL    |       |
| JOB_TITLE  | varchar(35)  | NO   |     |         |       |
| MIN_SALARY | decimal(6,0) | YES  |     | 8000    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+

```

#### Answer :-
```no-highlight
CREATE TABLE `employees`(
 `employee_id` INT PRIMARY KEY,
 `first_name` VARCHAR(50),
 `last_name` VARCHAR(50),
 `job_id` INT,
 `salary` INT,
 FOREIGN KEY(`job_id`) REFERENCES jobs(`job_id`)
 ON DELETE NO ACTION
 ON UPDATE NO ACTION
)ENGINE=InnoDB;;
```
