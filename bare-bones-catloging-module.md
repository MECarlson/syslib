# Creating a Bare Bones Cataloging Module

**Purpose** The purpose of this assignment is to expand our bare bones OPAC
by adding a cataloging functionality. This provides a new means of entering data.

**Tasks**

1. Create a new directory. 

```
cd /var/www/html

sudo mkdir cataloging
``` 

2. Use Nano to create index.html file and add content.

```
cd cataloging
sudo nano index.html
```

3. Create a PHP script to facilitate the communication of
data from the cataloging module to the database. Add content from 
manual into Nano. 

4. Ensure the web form is secure by using Apache2
authorization mechanism.

5. Create authentication file in etc/apache2 directory.

```
sudo htpasswd -c /etc/apache2/.htpasswd libcat
```

6. Insruct Apache2 to use htpasswd to limit access to
the cataloging module using Nano.

```
sudo nano /etc/apache2/apache2.conf
```

7. Change **None** to **All** in the third stanza.

8. Change the cataloging directory and use Nano
to create a file called .htaccess.

```
cd /var/www/html/cataloging
sudo nano .htaccess
```

9. Add the following content:
AuthType Basic
AuthName "Athorization Required"
AuthUserFile /etc/apache2/.htpasswd
Require valid-user

10. Check configuration and restart Apache2.

```
apachectl configtest
sudo systemctl restart apache2
systemctl status apache2
```

11. Revisit the cataloging module which
should now require a username and password. 


 
