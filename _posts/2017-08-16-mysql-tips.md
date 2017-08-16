---
layout: post
title: MySQL Tips
tags:  [MySQL]
categories: [first_categories]
author: wpwang
---

Some tips of using MySQL.

Test Environment:
{% highlight bash %}
OS: CentOS 6.8
{% endhighlight %}
+ Initialize MySQL

Start mysql daemon:
{% highlight bash %}
sudo /sbin/service mysqld start
{% endhighlight %}
Set a password for the MySQL root user:
{% highlight bash %}
/usr/bin/mysqladmin -u root password 'new-password'
/usr/bin/mysqladmin -u root -h slc09wox password 'new-password'
{% endhighlight %}
Grant privilege for remote user:
{% highlight bash %}
mysql -uroot -p
use mysql;
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' WITH GRANT OPTION;
SET PASSWORD FOR 'root'@'%' = PASSWORD('tm@tier4');
{% endhighlight %}
 
+ Export and import database:
{% highlight bash %}
mysql -u root -h localhost -p
mysqldump --databases --user=root --password your_db_name > export_into_db.sql
{% endhighlight %}
{% highlight bash %}
sudo yum install mysql-server
CREATE DATABASE <DATABASENAME>;
mysql -u <username> -p <databasename> < <filename.sql>
sudo yum install mysql-devel
{% endhighlight %}
 
+ Mysql Log Path: 
{% highlight bash %}
/var/log/mysqld.log
{% endhighlight %}

+ MySQL Common Error
{% highlight bash %}
MySQL Error 1153 - Got a packet bigger than 'max_allowed_packet' bytes
{% endhighlight %}
For the client, you can specify it on the command line:
{% highlight bash %}
mysql --max_allowed_packet=100M -u root -p database < dump.sql
{% endhighlight %}
Also, change the my.cnf or my.ini file under the mysqld section and set:
{% highlight bash %}
max_allowed_packet=100M
{% endhighlight %}
 
{% highlight bash %}
mysql start error: Can't open the mysql.plugin table
{% endhighlight %}
You need to execute following command:
{% highlight bash %}
mysql_install_db --user=mysql --ldata=/var/lib/mysql/
{% endhighlight %}
{% highlight bash %}
Another MySQL daemon already running with the same unix socket.
{% endhighlight %}
{% highlight bash %}
mv /var/lib/mysql/mysql.sock /var/lib/mysql/mysql.sock.bak
service mysqld start
{% endhighlight %}
To prevent the problem from occurring, you must perform a graceful shutdown of the server from the command line rather than powering off the server.
{% highlight bash %}
shutdown -h now
{% endhighlight %}
This will stop the running services before powering down the machine.
