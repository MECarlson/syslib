# LAMP Setup

**Purpose** The purpose of the LAMP process is to
learn how to install and configure Apache, PHP, and
MySQL on a Linux Server. 

**Tasks**

1. Install Apache2

```
sudo apt install apache2
```

2. Install and Configure PHP


To install PHP:

```
sudo apt install php libapache2-mod-php
```

```
sudo systemctl restart apach2
```

To Configure PHP:
Edit the dir.conf file so that
 Apache2 will default to index.php
instead of index.html. First create
a copy of the original and use nano
 to edit.

```
cd /etc/apache2/mods-enabled/
sudo cp dir.conf dir.conf.back
sudo nano dir.conf
```

Using nano, change the line to this:

```
DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
```

Next check the configuration
```
apachectl configtest
```

Restart the service:

```
sudo systemctl reload apache2
sudo systemctl restart apache2
```

3. Install and Configure MySQL

To install MySQL

```
sudo apt install mysql-server
```

Install PHP and MySQL Support

```
sudo apt install php-mysql php-mysqli
```

Next restart Apache2 and MySQL

```
sudo systemctl restart apache2
sudo systemctl restart mysql
```


