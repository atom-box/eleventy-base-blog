---
title: SQL Examples
description:
date: 2020-06-17
tags:
  - SQL
  - linux

layout: layouts/post.njk
---
# Creating a db and a user  
Remember these when starting a new LAMP site, such as a Drupal or Symfony project:
```
mysql> CREATE DATABASE golden_slumbers;
Query OK, 1 row affected (0.02 sec)

mysql> GRANT ALL PRIVILEGES ON golden_slumbers.* to 'lennonMcCartney'@localhost;
Query OK, 0 rows affected (0.01 sec)
```
# Get a fly by of the db
This is my quick way to describe every table.
```
SELECT TABLE_NAME, COLUMN_NAME  FROM information_schema.columns WHERE table_schema = 'employees' ;

SELECT TABLE_NAME, COLUMN_NAME FROM information_schema.columns WHERE table_schema = 'employees' ORDER BY COLUMN_NAME;
```

# The cool thing about GROUP BY
Functions get applied *after* the grouping.  So avg(), count(), max(), min(), sum(), all are applied to an entire column usually, except if there is a GROUP BY, they are applied to the group.  It's as if each group is a table of its own and it gets COUNT() locally applied to just it.

# Amy Friend's Four Friends  
My sister works with giant databases.  She says in the real world, these are her quotidian:  
1. EXISTS qualifying things without the load of bringing back actual data
2. NOT EXISTS finds records that dont have a match
3. IN
4. GROUP BY is great for getting counts and other aggregate data

# One SQL Assessment I took in 2019

Robert Half Associates (a recruiter) let me take a SQL test in 2019. Here's a screenshot of my results.  

Caveat: I was told to anticipate a generalized test of SQL but a fifth of the questions were specific to the Microsoft SQL server, such as "What is the maximum string length allowed?". At that time I had never even *heard* of SQL Server...  

In the test score below I have circled the parts that were based on SQL Server.  If you ignore those parts I think this test shows general competency in SQL.

{% image "sql-test-but-for-sql-server.png", "Test Score Results of Evan Genest, in 2019, taking a test of SQL Server knowledge even though he did not ever use SQL Server" %}



# Microsoft SQL Server
Install Microsoft SQL Server on Linux:  
https://docs.microsoft.com/en-us/sql/linux/quickstart-install-connect-ubuntu  


# Orphaned SQL question examples

Here are some questions but no db to go with them yet.  I saved the following practice questions for SQL in an old Udacity notebook from 2017 so I'm archiving them here.  

Get a list of only orangutangs, sorted by their age.  
Get a list of the 5 youngest zebras.  
Get a table that lists the nicknames of the animals and how many have that name. So it should show there are 4 Bobs, 4 Fidos, 2 Sammy's, et cetera.  
For each species, show the date of birth for the youngest member.    
Give just the nicknames of the ferrets, sorted by age, oldest first.  
Use Count(), Sum(), and Min().  
Give all of the animals, a species at a time, sorted by age.  
Add a new cheetah: Pablo, born yesterday.  
Find the animals that are non-aquatic and eat fish.  
