---
title: Matomo Error Messages, A General Introduction
description: Take 12 different courses over 5 months to gain a comprehensive understanding of Drupal
date: 2022-04-03
tags:
  - matomo
  - troubleshooting
layout: layouts/post.njk
---

## How does Matomo work; introduction to Matomo for beginners
Matomo is a direct competitor to Google Analytics.  Matomo allows you to see how users get to your site and what happens while they are on your site.  What is its market share? Matomo is installed on about 10% of the world's largest sites, according to [BuiltWith](https://trends.builtwith.com/analytics/Matomo). 

This is an article about what to do when you make a mistake with Matomo.  But first let's start here with an explanation of what Matomo does *when everything is going right*, so we have something to aspire to!  
  
Matomo comes in [three flavors](https://matomo.org/what-is-on-premise/).  We will assume in this article that you are running On Premise.  Before troubleshooting, take some time to know the rudiments of what Matomo is doing.  

In the most simple Matomo set up, Matomo will give you a  somewhat generic short six line script to paste into the top of any web page you want to monitor.  The script twlls that web page: *"create a Javascript variable to store data in the browser. Then download a fairly large Javascript program from www.example.com/matomo, where _example.com_ is replaced by your website domain."*  
  
This payload is sized 2kB to 20kB depending on how many bells and whistles you have turned on in your Matomo dashboard.  (It's a common misconception: people ask "How large is the Matomo download? Why is it so much bigger than Plausible, et al?" But the payload is controlled by you; it can be made pretty small if you minimize what you are tracking. Do that in the user interface if you wish.)  If you open and read the payload, this downloaded JS has lots of event listeners and selectors.  There's nothing magical going on.  

Matomo has a much better description of all this at the [Matomo Developer Documentation](https://developer.matomo.org/).  

## Troubleshooting in the front end
If the problem is subtle, it's useful to start by seeing what is happening in the browser first.  

In devtools, click the network tab to confirm what scripts are loading.  Start by looking for the payload in files named matomo.js or piwik.js.

Then, as you click and interact with your site, keep watching the devtools. The network will show you the headers and content of the http requests and responses. The client in this case is your browser and it is talking to the [Matomo tracking API](https://developer.matomo.org/guides/apis).  

## Troubleshooting the http traffic
The traffic to the API can be checked first by looking at the Apache server (or similarly in nGinx).

__/var/log/apache2/access*.log__
This is not exactly errors. This is *all* of the http reqs. As a fun bonus, this one can be read into Matomo later with a log reader.py (in case you ever have Matomo go down and you lose data)

__/var/log/apache2/error*.log__
This is where you look during Matomo troubleshooting


## Troubleshooting in the back end
The back end, written in PHP, will of course not be viewed in your browser.  For the PHP errors, look in your logs for two things: 
* failed PHP 
* bad SQL queries  

In my experience, 90% of the useful errors will be in the logs.   
  
If you want to be proactive, go into the user interface (dashboard) and select `admin > systems check`
Or in the CLI:  
`./console diagnostics:run`
  
If you are running a cron job for report archiving, the crontab errors arrive via email.  

Find your php.ini file.  Set this if it is not already:  
`log_errors = On`  
`display_errors=Off`

Find your matomo/config/common.config.ini.php  Put the line `logger_file_path = tmp/logs/matomo.log`  
Now when trouble strikes (and it will) you can peruse your matomo/tmp/logs/matomo.log
This shows how `./console core:archive` is succeeding or not. This is an audit of all Matomo Rawdata -> ReportArchiving.  
  
Enable the slow log for monitoring for weird slowness in the SQL database  First, find the config file for mysql.  In Linux, search here in descending priority, SQL loads the first file found in this list:  
/etc/my.cnf  
/etc/mysql/my.cnf  
$MYSQL_HOME/my.cnf  
  
Add this, including the square brackets line  
```
[mysqld]
# threshold for what is considered slow
long_query_time=3
# location to log to
slow_query_log_file=/var/log/mysql-slow.log
# Enable slow query logging
slow-query-log=1
```
Restart mysql.
Now queries taking more than 3 seconds will be logged. 
To view that log, the command is mysqldumpslow -t 10 mysql-slow.log > mysqldumpslow.out
This would give the top 10 queries, sorted by time they took


## Errors I got today, January 11, 2023
These happened after I performed the Matomo Three Step Update 
1. Permissions of ownership  
These were fixed by following the interface suggestions for chown and chmod  
2. DB update needed
This was also solved when the interface suggested I use 
```
$ sudo php /var/www/littlefurnace.com/matomo/console core:update
```
3. The directory "/var/www/littlefurnace.com/matomo/tmp/cache/tracker/" does not exist and could not be created.
This is the classic one we receive once a day at work in Contact Matomo inbox.  
Solve with `$ sudo chown -R www-data:www-data /var/www/littlefurnace.com/matomo/tmp/*`


