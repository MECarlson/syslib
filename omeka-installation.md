# Omeka Installation

**Purpose** The purpose of this exercise is to
install an open-source content management
system for digital collections and exhibits.

**Tasks**

1. Install prerequisites - ImageMagick.

'''
sudo apt install imagemagick
'''

2. Enable Apache mod_rewrite module to rewrite URLs.

'''
sudo a2enmod rewrite
'''

3. Restart Apache2

'''
sudo systemctl restart apache2
'''

4. Switch to root user.

'''
sudo su
'''

5. Log into MySQL and create a new database for Omeka.

'''
mysql -u root
create user 'omeka'@'localhost' identified by "XXXXXX';
create database omeka;
grant all privileges on omeka.* to 'omeka'@'localhost';
show databases;
\q
'''

6. Download and unzip Omeka.

'''
cd /var/www/html

sudo wget https://github.com/omeka/Omeka/releases/download/v3.1/omeka-3.1.zip

sudo unzip omeka-3.1
'''

7. Edit file using Nano to enter database
credentials in the XXXXXX fields. 

'''
cd /var/www/html/omeka

sudo nano db.ini
'''

8. Rename

'''
cd /var/www/html
sudo mv omeka-3.1 omeka
'''

9. Change ownership

'''
sudo chown -R www-data:www-data*
'''

10. Restart Apache2 and MySQL

'''
sudo systemctl restart apache2
sudo systemctl restart mysql
'''

11. Go to http://MY-IP-ADDRESS/omeka to finish Omeka setup. 
