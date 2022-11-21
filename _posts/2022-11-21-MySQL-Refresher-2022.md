---
title: "MySQL Refresher 2022"
date: 2022-11-21
layout: default
---

I've not looked at MySQL lately, so time for a refresh!

# Learn SQL (using MySQL) in One Day and Learn It Well - Jamie Chan

## Common Data Types

### Textual

**CHAR(size)** - fixed length string up to 255 - gets padded with spaces  
**VARCHAR(size)** - variable length string - no spaces added - uses less storage but can be slower ** so should use char if fixed length **  

### Numeric

**INT** -2147483648 to 2147483647  
**INT UNSIGNED** - just positive  
**FLOAT(m total digits,d decimal places)** - non integers - stored as approximate values - 4 bytes - accurate up to 7 decimal places  
**DOUBLE(m total digits,d decimal places)** - 8 bytes so better precision - accurate up to 14 decimal places  

**DECIMAL(m total digits,d decimal places)** - exact values- monetary data where precision is important  

### Date and Time
**YEAR** - 2 or 4 digit format  
**DATE** - YYYY-MM-DD  
**TIME** - HH:MI:SS  
**DATETIME** - YYYY-MM-DD HH:MI:SS  
**TIMESTAMP** - converted to UTC and then back to local  

## Column Constraints
**NOT NULL**  
**UNIQUE**  
**DEFAULT**  - default value when none specified  
**PRIMARY KEY**  - by default UNIQUE and UNIQUE.  
**AUTO_INCREMENT**  - starts at 1, table can have only 1  

**Foreign Keys** 


FOREIGN KEY(mentor_id) REFERENCES co_employees(id) ON DELETE
CASCADE ON UPDATE RESTRICT

**DELETE CASCADE** - delete a parent and these records will also go
**DELETE RESTRICT** - parent cannot be deleted
**DELETE SET NULL** - child is set to NULL when parent deleted
**DELETE SET DEFAULT** -- child is set to default is parent deleted
Can also be used on updates.
**ON UPDATE RESTRICT** -- cannot update the parent, if it has children

**UNIQUE(mentor_id, mentee_id)**

Named Constraints (easier to reference when updating or deleting):

CONSTRAINT fk1 FOREIGN KEY(mentor_id) REFERENCES co_employees(id)
ON DELETE CASCADE ON UPDATE RESTRICT


### Comparison
**!= > < **  
**BETWEEN**  
**LIKE** - LIKE '%er' or '%er%' or _ to specify the number of chars  
**IN()**  
**NOT IN()**  
**AND/OR**  

### Subqueries
 
Filter the results of of one query based on the results of another:
SELECT em_name from employees WHERE id IN
(SELECT mentor_id FROM mentorships WHERE project = 'SQF
Limited');

### Sorting Rows
**ORDER BY** - ORDER BY gender , em_name - ORDER BY DESC 

### Functions

**CONCAT()**  
**SUBSTRING()** -- SELECT SUBSTRING('Programming', 2); or  
SELECT SUBSTRING('Programming', 2, 6);  

**NOW()** - current date and time  
**CURDATE()** - 2018-08-28  
**CURTIME()**  

### Aggregate Functions

**COUNT()*** - * all rows but with column name returns only non  -- null  
SELECT COUNT(DISTINCT gender) FROM employees; will remove duplicates   
 
**AVG()**  
**ROUND(x,y)**  
**MIN()**  
**MAX()**  
**SUM()**  
**GROUP BY** -- SELECT gender, MAX(salary) FROM employees GROUP BY gender;  
**HAVING** -- Filter the result of the grouped data  

SELECT gender, MAX(salary) FROM employees GROUP BY gender HAVING
MAX(salary) > 10000;

**Here we are filtering by the result of MAX(salary)**


### JOINS

**INNER JOIN** -- matching rows  
**LEFT JOIN** -- all from left  
**RIGHT JOIN** -- all from right  
**UNION** -- removes duplicates  
**UNION ALL** -- does not remove duplicates  
****
****
