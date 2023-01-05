---
title: SQL Exercises for a 299,938 Line Database
description:
date: 2021-11-17
tags:
  - SQL
  - linux

layout: layouts/post.njk
---
```
            _      
           | |     
  ___  __ _| |     
 / __|/ _` | |     
 \__ \ (_| | |____ 
 |___/\__, |______|
         | |       
         |_|       
```

If you want to practice SQL queries, you need a local database and some exercises to get you started. This post describes how to install a database with millions of lines. I then share some exercises to get you started on playing with the database.

# Clone and use the db *Employees* 
*Employees* is a machine generated db from the DataCharmer repository. It has 299938 employees and 2843227 salary records. Its schema is shown at the end of this article. (You can try a much smaller practice DB described in my article: __SQL Exercises for a 40 Line Database__.)

To get started, clone the repo at [https://github.com/datacharmer/test_db](https://github.com/datacharmer/test_db)

```
git clone https://github.com/datacharmer/test_db
```
 and then run from the CLI, as super user   
```
$ sudo mysql < employees.sql
```

# Exercises  

Now that you have the data set, try these exercieses.  

Solve each SQL challenge using a SQL query.  (Scroll down for solutions.)

1. Get a list of employees whose last names start with a J, sorted by age.  
2. Show a list of all __department numbers__ and employees per department, with them ranked by the departments with the most employees first.  Show the departments by their department numbers only.
3. Rank the departments by average age of their employees, show the departments by their department number only.    
4. Use a self join.  Find pairs of employees where they have the same first name and same last name, i.e. "Jimmy Johnson" and "Jimmy Johnson" would match but not "Ted Johnson" and "Fran Johnson".  
__Hint__: Look up how to do a self join.  

5. Count how many employees are named Georgi or Parto
6. Find the employees with last name starting with "T" whose salaries fall in a narrow range.  Play around to get the range small enough that just a handful of results are found.
7. Create a _stored_ procedure!  
Your stored procedure should return first and last name and emp # for employees who have been managers for more than X number of years, where X is the only inputtable value.

## My Solutions

1. `SELECT first_name, last_name, birth_date FROM employees WHERE last_name LIKE 'g%' ORDER BY birth_date  ASC;`
2. `SELECT count(d.dept_no) AS employees, d.dept_no from employees AS e JOIN dept_emp AS d ON e.emp_no = d.emp_no  GROUP BY d.dept_no ORDER BY employees DESC;`
3.  `SELECT  d.dept_no, avg( DATEDIFF(curdate(), e.birth_date))/365 AS age
FROM employees AS e JOIN dept_emp AS d ON e.emp_no = d.emp_no  
GROUP BY d.dept_no  
ORDER BY age;`  
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
5. SELECT count(first_name), first_name  
FROM employees  
WHERE first_name="parto" OR first_name="georgi"  
GROUP BY first_name;  
```
+-------------------+------------+
| count(first_name) | first_name |
+-------------------+------------+
|               253 | Georgi     |
|               228 | Parto      |
+-------------------+------------+
2 rows in set (0.19 sec)

```

6. SELECT first_name, last_name, e.emp_no, max(s.salary)  
FROM employees as e JOIN salaries as s ON e.emp_no=s.emp_no   
WHERE s.salary > 40048 AND s.salary < 40050  
AND e.last_name LIKE "t%"   
GROUP BY e.emp_no  
ORDER BY e.last_name;  
  
__note: the *group by* is neccessary because there's a *max()*__  
__note: the *max()* was neccessary because most employees have had multiple salaries during their time with the company__  
```
+------------+----------------+--------+---------------+
| first_name | last_name      | emp_no | max(s.salary) |
+------------+----------------+--------+---------------+
| Tran       | Tanemo         | 240242 |         40049 |
| Katsuyuki  | Theuretzbacher |  87678 |         40049 |
| Nitsan     | Trystram       |  81920 |         40049 |
+------------+----------------+--------+---------------+
3 rows in set (0.37 sec)
```
7. (WORK-IN-PROGRESS)
THIS WORKS
```
SELECT emp_no, from_date FROM dept_manager WHERE  DATEDIFF(curdate(), from_date)/365 > 3;
+--------+------------+
| emp_no | from_date  |
+--------+------------+
| 110022 | 1985-01-01 |
| 110039 | 1991-10-01 |
| 110085 | 1985-01-01 |
| 110114 | 1989-12-17 |
```

BUT THIS FAILS
```
CREATE PROCEDURE LongtimeManagers @Years smallint 
AS 
SELECT emp_no, from_date FROM dept_manager WHERE DATEDIFF(curdate(), from_date)/365 > @Years 
 GO;
```
# Trivial Artifacts of this auto-generated db

If you run a query, you can see *how many employees have both first and last name the same* typically about 4 of 20 people had someone in the company with the exact same first + last name.  Is that too high? 


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

A README in the employees repository notes the same thing, giving a caveat: *This data was generated, and as such there are inconsistencies and subtle problems. Rather than removing them, we decided to leave the contents untouched, and use these issues as data cleaning exercises.*  When you use the db you may notice that for a given last name there will be 150 people with that last name. Always.  So the data really is just a bunch of dice being rolled.  


    
# Appendix 1
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

# Appendix 2
Install Microsoft SQL Server on Linux:  
https://docs.microsoft.com/en-us/sql/linux/quickstart-install-connect-ubuntu  

