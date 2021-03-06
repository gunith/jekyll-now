---
layout: post
published: true
title: How to get the file path of a Log4J log file in Java level?
author:
  display_name: Gunith
  login: admin
  email: gunith@gmail.com
  url: ''
author_login: admin
author_email: gunith@gmail.com
wordpress_id: 8
wordpress_url: http://www.beta.gunith.com/?p=8
date: '2010-11-20 18:55:26 +0530'
date_gmt: '2010-11-20 13:25:26 +0530'
categories:
- Java
tags:
- programming
- Java
- logging
- log4j
- code
- jee

---

Assume the log4j.properties file is as below,

```
log4j.logger.migrationlog = INFO, migration
log4j.appender.migration = org.apache.log4j.RollingFileAppender
log4j.appender.migration.File = C:/work/log/migration.log
log4j.appender.migration.MaxFileSize=20MB
log4j.appender.migration.MaxBackupIndex=1
log4j.appender.migration.layout = org.apache.log4j.PatternLayout
log4j.appender.migration.layout.conversionPattern = %d %-5p %c - %m%n
```

In such case, your Java code should be as follows,

```java
Logger logger = Logger.getLogger("migrationlog"); //Defining the LoggerFileAppender
appender = (FileAppender)logger.getAppender("migration");
return new File(appender.getFile());
```

Note that its not `migrationlog` which was used when making the logger object is used when retrieving the file name, but `migration`

_Migrated from gunith.com_
