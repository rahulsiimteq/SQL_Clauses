## *SQL DDL clauses*

* `CREATE`: [To create databases and database objects](https://www.w3schools.com/sql/sql_create_table.asp)


### Excersise

#### 1.1. Write a SQL statement to rename the table countries to country_new.
#### Answer :-  
```no-highlight
ALTER TABLE `countries` RENAME `countries` to `country_new`;
```
#### 2. Write a SQL statement to add a column region_id to the table locations.

#### Answer :-  
```no-highlight
ALTER TABLE `location` ADD COLUMN `region_id` INT;
```
#### 3. Write a SQL statement to add a columns ID as the first column of the table locations.

#### Answer :-  
```no-highlight
ALTER TABLE `location` ADD COLUMN `id` INT FIRST;
```
#### 4. Write a SQL statement to add a column region_id after state_province to the table locations.

#### Answer :-  
```no-highlight
ALTER TABLE `location` ADD COLUMN `region_id` AFTER `state_province`;
```
#### 5. Write a SQL statement change the data type of the column country_id to integer in the table locations.

#### Answer :-  
```no-highlight
ALTER TABLE `loocation` MODIFY COLUMN `country_id` INT;
```
#### 6. Write a SQL statement to drop the column city from the table locations.

#### Answer :-  
```no-highlight
ALTER TABLE `location` DROP COLUMN `city`;
```
#### 7. Write a SQL statement to change the name of the column state_province to state, keeping the data type and size same

#### Answer :-  
```no-highlight
ALTER TABLE `location` RENAME COLUMN `state_province` TO `state`;

```
#### 8. Write a SQL statement to add a primary key for the columns location_id in the locations table.

#### Answer :-  
```no-highlight
ALTER TABLE `location' ADD CONSTRAINT(`location_id_pk`) PRIMARY KEY(`loation_id`);
```
#### 9. Write a SQL statement to add a primary key for a combination of columns location_id and country_id.

#### Answer :-  
```no-highlight
ALTER TABLE `location' ADD CONSTRAINT(`location_id_pk`) PRIMARY KEY(`loation_id`) PRIMARY KEY(`country_id`);
```
#### 10. Write a SQL statement to drop the existing primary from the table locations on a combination of columns location_id and country_id.

#### Answer :-  
```no-highlight
ALTER TABLE `location' DROP CONSTRAINT(`location_id_pk`);
```
#### 11. Write a SQL statement to add a foreign key on job_id column of job_history table referencing to the primary key job_id of jobs table.

#### Answer :-  
```no-highlight
ALTER TABLE `job_history' ADD CONSTRAINT(`job_id_fk`) FOREIGN KEYjobs(`job_id`);

```
#### 12. Write a SQL statement to add a foreign key constraint named fk_job_id on job_id column of job_history table referencing to the primary key job_id of jobs table.

#### Answer :-  
```no-highlight
ALTER TABLE `job_history' ADD CONSTRAINT(`fk_job_id`) FOREIGN KEYjobs(`job_id`);

```
#### 13. Write a SQL statement to drop the existing foreign key fk_job_id from job_history table on job_id column which is referencing to the job_id of jobs table.

#### Answer :-  
```no-highlight
ALTER TABLE `job_history` DROP CONSTRAINT(`fk_job_id`);
```
#### 14. Write a SQL statement to add an index named indx_job_id on job_id column in the table job_history.

#### Answer :-  
```no-highlight
CREATE INDEX `indx_job_id` on job_history(job_id);
```
#### 15. Write a SQL statement to drop the index indx_job_id from job_history table.

#### Answer :-  
```no-highlight
ALTER TABLE `job_history` DROP INDEX `indx_job_id`;
```
