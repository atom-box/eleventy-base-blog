---
title: Great SQL data set for SQL Challenges
description:
date: 2021-11-17
tags:
  - SQL

layout: layouts/post.njk
---

Stay sharp by practicing SQL! This is a good introduction to getting started with MySQL but it works with PostGreSQL, SQLite, et al.  __This is just a messy grab bag of mySQL notes.__

## Download some test data to use with the challenges in the next section

A good sample database is [Employee Test DB](https://github.com/datacharmer/test_db). It has 300,000 example employees and 1 million salary records. A readme with the data has a small qualifier. It says *The data was generated, and as such there are inconsistencies and subtle problems. Rather than removing them, we decided to leave the contents untouched, and use these issues as data cleaning exercises.*  Regarding this, I did notice that for a given last name there will be 150 people with that last name.

To get the SQL example data, clone the above repo, and then run from the CLI, as super user like this.  
```
$ sudo mysql < employees.sql
```

## Challenges

Solve each SQL challenge using a SQL query.  (Scroll down for solutions.)

1. Get a list of employees whose last names start with a J, sorted by age.  
2. Show a list of all __department numbers__ and employees per department, with them ranked by the departments with the most employees first.  Show the departments by their department numbers only.
3. Rank the departments by average age of their employees, show the departments by their department number only.    

## Solutions

1. `mysql> SELECT first_name, last_name, birth_date FROM employees WHERE last_name LIKE 'g%' ORDER BY birth_date  ASC;`
2. `mysql> SELECT count(d.dept_no) AS employees, d.dept_no from employees AS e JOIN dept_emp AS d ON e.emp_no = d.emp_no  GROUP BY d.dept_no ORDER BY employees DESC;`
3. THIS DOES NOT QUITE WORK  
```mysql> SELECT count(d.dept_no) AS employees, d.dept_no, DATEDIFF(curdate(),  '1965-01-27')/365  from employees AS e JOIN dept_emp AS d ON e.emp_no = d.emp_no  GROUP BY d.dept_no ORDER BY employees DESC;```


## Handy commands

### Describe ALL tables in EXAMPLE

`SELECT TABLE_NAME, COLUMN_NAME  FROM information_schema.columns WHERE table_schema = 'employees' ;`

### Find the gap between two dates.  

Find the gap between two dates. Return the answer in days.

`DATEDIFF(date1, date2)`

date1, date2 (Required). Two dates to calculate the number of days between. (date1 - date2)

### Get a new date by removing some interval out of a given date

This is interesting functionality, because I *think* dates are strings. Or are they stored as an integer, like Epoch? Anyway this feels pretty deluxe.

`DATE_SUB(date, INTERVAL value interval)`

#### Parameter Values

- date (Required). The date to be modified
- value (Required). The value of the time/date interval to subtract. Both positive and negative values are allowed
- interval (Required). The type of interval to subtract. Can be one of the following values: 


    * MICROSECOND
    * SECOND
    * MINUTE
    * HOUR
    * DAY
    * WEEK
    * MONTH
    * QUARTER
    * YEAR
    * SECOND_MICROSECOND
    * MINUTE_MICROSECOND
    * MINUTE_SECOND
    * HOUR_MICROSECOND
    * HOUR_SECOND
    * HOUR_MINUTE
    * DAY_MICROSECOND
    * DAY_SECOND
    * DAY_MINUTE
    * DAY_HOUR
    * YEAR_MONTH

## Resources

There is a smaller database of employees at [sqltutorial.org](https://www.sqltutorial.org/sql-sample-database/). It is loaded by just cut an d paste, in case that is easier for you.


## Example rows from the EMPLOYEES database

```
*************************** employees ***************************
    emp_no: 498767
birth_date: 1964-11-15
first_name: Hironobu
 last_name: Ghandeharizadeh
    gender: M
 hire_date: 1987-08-09

*************************** salaries ***************************
   emp_no: 10009
   salary: 85875
from_date: 1997-02-15
  to_date: 1998-02-15

*************************** titles ***************************
   emp_no: 10001
    title: Senior Engineer
from_date: 1986-06-26
  to_date: 9999-01-01
1 row in set (0.01 sec)

*************************** dept_manager ***************************
   emp_no: 110022
  dept_no: d001
from_date: 1985-01-01
  to_date: 1991-10-01

*************************** dept_emp_latest_date*****************
   emp_no: 10001
from_date: 1986-06-26
  to_date: 9999-01-01

*************************** dept_emp ***************************
   emp_no: 10001
  dept_no: d005
from_date: 1986-06-26
  to_date: 9999-01-01

*************************** departments ***************************
  dept_no: d001
dept_name: Marketing


********************* current_dept_emp ***************************
   emp_no: 10011
  dept_no: d009
from_date: 1990-01-22
  to_date: 1996-11-09
```

## SQL Challenges, Zoo Animals

I saved the following practice questions for SQL in an old notebook from 2017 so I'm archiving them here.  They were from a great Udacity course on Relational Databases. They dealt with a zoo inventory example but can be easily used with other example databases I think. I no longer have the example data though!

Get a list of only orangutangs, sorted by their age.  
Get a list of the 5 youngest zebras.  
Get a table that lists the nicknames of the animals and how many have that name. So it should show there are 4 Bobs, 4 Fidos, 2 Sammy's, et cetera.  
For each species, show the date of birth for the youngest member.    
Give just the nicknames of the ferrets, sorted by age, oldest first.  
Use Count(), Sum(), and Min().  
Give all of the animals, a species at a time, sorted by age.  
Add a new cheetah: Pablo, born yesterday.  
Find the animals that are non-aquatic and eat fish.  

## Some mysql examples

```
mysql> CREATE DATABASE golden_slumbers;
Query OK, 1 row affected (0.02 sec)

mysql> GRANT ALL PRIVILEGES ON golden_slumbers.* to 'lennonMcCartney'@localhost;
Query OK, 0 rows affected (0.01 sec)
```
