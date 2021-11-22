---
title: Great SQL data set for SQL Challenges
description:
date: 2021-11-17
tags:
  - SQL

layout: layouts/post.njk
---

Caveat: __This is just a messy grab bag of mySQL notes.__

Here are some specific exercises for warming up or staying practiced SQL! I am using MySQL but this all seems agnostic: the following should work with PostGreSQL, SQLite, MariaDB, et al. 

# Activity 1: Try the Test db *Employees* from the DataCharmer repository

A good sample database is here: [Employee Test DB](https://github.com/datacharmer/test_db). (This is a large db; scroll down to Activity 2 if you need something smaller.)

This db has 300,000 example employees and 1 million salary records. A README in this repository gives one caveat: *This data was generated, and as such there are inconsistencies and subtle problems. Rather than removing them, we decided to leave the contents untouched, and use these issues as data cleaning exercises.*  When you use the db you may notice that for a given last name there will be 150 people with that last name. Always.  So the data really is just a bunch of dice being rolled.  

To get started, clone the repo [https://github.com/datacharmer/test_db](https://github.com/datacharmer/test_db) and then run from the CLI, as super user like this.  
```
$ sudo mysql < employees.sql
```

## Exercises

Solve each SQL challenge using a SQL query.  (Scroll down for solutions.)

1. Get a list of employees whose last names start with a J, sorted by age.  
2. Show a list of all __department numbers__ and employees per department, with them ranked by the departments with the most employees first.  Show the departments by their department numbers only.
3. Rank the departments by average age of their employees, show the departments by their department number only.    
4. Use a self join.  Find pairs of employees where they have the same first name and same last name, i.e. "Jimmy Johnson" and "Jimmy Johnson" would match but not "Ted Johnson" and "Fran Johnson".
Hint: Look up how to do a self join.
Hint: Here is a way to find only pairs of same first name:

(Limit 10 is in there in case you want to try it. It still takes almost a minute.)

## My Solutions

1. `mysql> SELECT first_name, last_name, birth_date FROM employees WHERE last_name LIKE 'g%' ORDER BY birth_date  ASC;`
2. `mysql> SELECT count(d.dept_no) AS employees, d.dept_no from employees AS e JOIN dept_emp AS d ON e.emp_no = d.emp_no  GROUP BY d.dept_no ORDER BY employees DESC;`
3. THIS DOES NOT QUITE WORK  
`mysql> SELECT count(d.dept_no) AS employees, d.dept_no, DATEDIFF(curdate(),  '1965-01-27')/365  from employees AS e JOIN dept_emp AS d ON e.emp_no = d.emp_no  GROUP BY d.dept_no ORDER BY employees DESC;`
4.  `SELECT A.first_name, A.last_name, A.emp_no, B.first_name, B.last_name, B.emp_no FROM employees A, employees B WHERE A.emp_no <> B.emp_no AND A.first_name = B.first_name AND A.last_name = B.last_name ORDER BY A.first_name LIMIT 10;`
which gives
```
+------------+------------+--------+------------+------------+--------+
| first_name | last_name  | emp_no | first_name | last_name  | emp_no |
+------------+------------+--------+------------+------------+--------+
| Aamer      | Gyorkos    |  50757 | Aamer      | Gyorkos    |  29981 |
| Aamer      | Demke      | 412361 | Aamer      | Demke      | 241701 |
| Aamer      | Gill       | 104915 | Aamer      | Gill       | 227392 |
| Aamer      | Nishimukai | 264839 | Aamer      | Nishimukai | 493013 |
| Aamer      | Soloway    | 269870 | Aamer      | Soloway    | 284027 |
| Aamer      | Gill       | 227392 | Aamer      | Gill       | 104915 |
| Aamer      | Nishimukai | 493013 | Aamer      | Nishimukai | 264839 |
| Aamer      | Soloway    | 284027 | Aamer      | Soloway    | 269870 |
| Aamer      | Bahl       | 283280 | Aamer      | Bahl       |  60922 |
| Aamer      | Gyorkos    |  29981 | Aamer      | Gyorkos    |  50757 |
+------------+------------+--------+------------+------------+--------+
10 rows in set (0.53 sec)

```


# General notes for MySQL

## Describe ALL tables in EXAMPLE
This is my favorite command. Working in the terminal these two lines give a flyby of the data schema.

```
SELECT TABLE_NAME, COLUMN_NAME  FROM information_schema.columns WHERE table_schema = 'employees' ;

SELECT TABLE_NAME, COLUMN_NAME FROM information_schema.columns WHERE table_schema = 'employees' ORDER BY COLUMN_NAME;
```

### Find the gap between two dates.  

Find the gap between two dates. Return the answer in days.

`DATEDIFF(date1, date2)`

This function returns the difference in days.  

Example```select DATEDIFF(curdate(), birth_date)/365 AS "age in years" from employees LIMIT 3 ;```
will return 
```

+--------------+
| age in years |
+--------------+
|      68.2575 |
|      57.5014 |
|      62.0027 |
+--------------+
3 rows in set (0.00 sec)
```



### Subtracting! Dates!
Get a new date by removing some interval out of a given date

This is interesting functionality, because I *think* dates are strings. Or are they stored as an integer, like Epoch? Anyway this feels pretty deluxe.

`DATE_SUB(date, INTERVAL value interval)`  
  
where the parameters are:  

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
  
    

# Activity 2: Try the employees db at SQLTutorial website

Here is a database (but for now, no exercises).  

The database of employees is at [sqltutorial.org](https://www.sqltutorial.org/sql-sample-database/). It is small and can be loaded by just cut and paste, in case that is easier for you than using the gigantic db in Activity 1.


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

# Activity 3: Zoo Animals

Here are some questions but no db to go with them yet.  

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

# Amy Friend's Four Friends  
My sister works with giant databases.  She says in the real world, these are her quotidian:  
1. EXISTS qualifying things without the load of bringing back actual data
2. NOT EXISTS finds records that dont have a match
3. IN
4. GROUP BY is great for getting counts and other aggregate data

# Creating a db and a user  
Remember these when starting a new LAMP site, such as a Drupal or Symfony project:
```
mysql> CREATE DATABASE golden_slumbers;
Query OK, 1 row affected (0.02 sec)

mysql> GRANT ALL PRIVILEGES ON golden_slumbers.* to 'lennonMcCartney'@localhost;
Query OK, 0 rows affected (0.01 sec)
```
# One SQL Assessment I took in 2019

Robert Half Associates (a recruiter) let me take a SQL test in 2019. Here's a screenshot of my results.  

Caveat: I was told to anticipate a generalized test of SQL but a fifth of the questions were specific to the Microsoft SQL server, such as "What is the maximum string length allowed?". At that time I had never even *heard* of SQL Server...  

In the test score below I have circled the parts that were based on SQL Server.  If you ignore those parts I think this test shows general competency in SQL.

{% image "sql-test-but-for-sql-server.png", "Test Score Results of Evan Genest, in 2019, taking a test of SQL Server knowledge even though he did not ever use SQL Server" %}

# Trivial Artifacts of using fake data

For Activity 1 when I ran a query for *Show employees with both first and last name the same* typically about 4 of 20 people had someone in the company with the exact same first + last name.  That seems like double the rate I would expect.

Here we see the number of Ymte's with a *twin* where the last name starts with P is 4.  The total number of Ymte's with a P last name is 20.

```
mysql> SELECT count(*) FROM employees WHERE first_name = "Ymte" AND last_name LIKE "P%";+----------+
| count(*) |
+----------+
|       20 |
+----------+
1 row in set (0.08 sec)

mysql> SELECT A.emp_no, A.first_name, A.last_name, B.emp_no, B.first_name, B.last_name 
    -> FROM employees A, employees B 
    -> WHERE A.emp_no <> B.emp_no 
    -> AND A.first_name = B.first_name 
    -> AND A.last_name = B.last_name 
    -> AND A.first_name = "Ymte" 
    -> AND A.last_name LIKE "P%" 
    -> ORDER BY A.last_name;
+--------+------------+-----------+--------+------------+-----------+
| emp_no | first_name | last_name | emp_no | first_name | last_name |
+--------+------------+-----------+--------+------------+-----------+
| 499935 | Ymte       | Perelgut  |  89488 | Ymte       | Perelgut  |
| 252012 | Ymte       | Perelgut  |  89488 | Ymte       | Perelgut  |
| 499935 | Ymte       | Perelgut  | 252012 | Ymte       | Perelgut  |
|  89488 | Ymte       | Perelgut  | 252012 | Ymte       | Perelgut  |
| 252012 | Ymte       | Perelgut  | 499935 | Ymte       | Perelgut  |
|  89488 | Ymte       | Perelgut  | 499935 | Ymte       | Perelgut  |
| 499567 | Ymte       | Potthoff  | 463804 | Ymte       | Potthoff  |
| 463804 | Ymte       | Potthoff  | 499567 | Ymte       | Potthoff  |
+--------+------------+-----------+--------+------------+-----------+
8 rows in set (0.16 sec)
```

# Appendix
For reference when doing Activity 1 here is the Employees database  
```
+----------------------+-------------+
| TABLE_NAME           | COLUMN_NAME |
+----------------------+-------------+
| employees            | birth_date  |
| departments          | dept_name   |
| current_dept_emp     | dept_no     |
| departments          | dept_no     |
| dept_emp             | dept_no     |
| dept_manager         | dept_no     |
| current_dept_emp     | emp_no      |
| dept_manager         | emp_no      |
| employees            | emp_no      |
| dept_emp_latest_date | emp_no      |
| salaries             | emp_no      |
| dept_emp             | emp_no      |
| titles               | emp_no      |
| employees            | first_name  |
| salaries             | from_date   |
| titles               | from_date   |
| dept_manager         | from_date   |
| dept_emp_latest_date | from_date   |
| dept_emp             | from_date   |
| current_dept_emp     | from_date   |
| employees            | gender      |
| employees            | hire_date   |
| employees            | last_name   |
| salaries             | salary      |
| titles               | title       |
| dept_manager         | to_date     |
| dept_emp_latest_date | to_date     |
| dept_emp             | to_date     |
| salaries             | to_date     |
| current_dept_emp     | to_date     |
| titles               | to_date     |
+----------------------+-------------+
31 rows in set (0.00 sec)

mysql> SELECT TABLE_NAME, COLUMN_NAME FROM information_schema.columns WHERE table_schema = 'employees';
+----------------------+-------------+
| TABLE_NAME           | COLUMN_NAME |
+----------------------+-------------+
| current_dept_emp     | dept_no     |
| current_dept_emp     | emp_no      |
| current_dept_emp     | from_date   |
| current_dept_emp     | to_date     |
| departments          | dept_name   |
| departments          | dept_no     |
| dept_emp             | dept_no     |
| dept_emp             | emp_no      |
| dept_emp             | from_date   |
| dept_emp             | to_date     |
| dept_emp_latest_date | emp_no      |
| dept_emp_latest_date | from_date   |
| dept_emp_latest_date | to_date     |
| dept_manager         | dept_no     |
| dept_manager         | emp_no      |
| dept_manager         | from_date   |
| dept_manager         | to_date     |
| employees            | birth_date  |
| employees            | emp_no      |
| employees            | first_name  |
| employees            | gender      |
| employees            | hire_date   |
| employees            | last_name   |
| salaries             | emp_no      |
| salaries             | from_date   |
| salaries             | salary      |
| salaries             | to_date     |
| titles               | emp_no      |
| titles               | from_date   |
| titles               | title       |
| titles               | to_date     |
+----------------------+-------------+
31 rows in set (0.00 sec)

```