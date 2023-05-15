---
title: Matomo PHP Settings
description:
date: 2023-01-24
tags:
  - web analytics
  - troubleshooting
layout: layouts/post.njk
---

## The Problem  
I turned on Matomo and the dashboard had dozens of PHP function deprecation notices.  Typical:  
  

WARNING: /plugins/Events/Archiver.php(82): Deprecated - Creation of dynamic property Piwik\Plugins\Events\Archiver::$maximumRowsInSubDataTable is deprecated - Matomo 4.13.1 - Please report this message in the Matomo forums: https://forum.matomo.org (please do a search first as it might have been reported already) (Module: API, Action: get, Method: VisitsSummary.get, In CLI mode: false)  
  
WARNING: /core/DataAccess/ArchiveWriter.php(102): Deprecated - Creation of dynamic property Piwik\DataAccess\ArchiveWriter::$idArchive is deprecated - Matomo 4.13.1 - Please report this message in the Matomo forums: https://forum.matomo.org (please do a search first as it might have been reported already) (Module: API, Action: get, Method: VisitsSummary.get, In CLI mode: false)  
  
WARNING: /core/DataAccess/ArchiveWriter.php(103): Deprecated - Creation of dynamic property Piwik\DataAccess\ArchiveWriter::$idSite is deprecated - Matomo 4.13.1 - Please report this message in the Matomo forums: https://forum.matomo.org (please do a search first as it might have been reported already) (Module: API, Action: get, Method: VisitsSummary.get, In CLI mode: false)  
  
WARNING: /core/DataAccess/ArchiveWriter.php(104): Deprecated - Creation of dynamic property Piwik\DataAccess\ArchiveWriter::$segment is deprecated - Matomo 4.13.1 - Please report this message in the Matomo forums: https://forum.matomo.org (please do a search first as it might have been reported already) (Module: API, Action: get, Method: VisitsSummary.get, In CLI mode: false)  
    
This is caused by Matomo being written for a PHP version that I am not running. Matomo is usually up to date with one minor version back. So check what your *server* is running (not your terminal/CLI, your Apache2 apache.conf, or httpd.conf -- those often are running different PHP versions!).
    
## The Apache settings in Ubuntu look like this
  
It is split into several files forming the configuration hierarchy outlined
below, all located in the /etc/apache2/ directory:
  
       /etc/apache2/
       |-- apache2.conf
       |       `--  ports.conf
       |-- mods-enabled
       |       |-- *.load
       |       `-- *.conf
       |-- conf-enabled
       |       `-- *.conf
       `-- sites-enabled
               `-- *.conf

## To be continued

