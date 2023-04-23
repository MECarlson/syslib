# Wordpress Installation

**Purpose** To install an open-source content
management system that is commonly used by libraries
to build and maintain their websites.

**Tasks**

1. Confim system requirements and install additional PHP modules.

''' 
php -version
mysql -version
sudo apt install php-curl php-xml php-imagick php-mbstring php-sip php-intl
sudo systemctl restart apache2
sudo systemctl restart mysql
'''

2. Change to the var/www/html directory. Download and extract Wordpress.

'''
cd /var/www/html

sudo wget https://wordpress.org/latest.tar.gz

sudo tar -xzyf latest.tar.gz
'''

3. Switch to root user and log into mysql. 

'''
sudo su
mysql -u root
'''

4. Create database and user

'''
create user 'wordpress@localhost' identified by 'XXXXXXX';
create database wordpress;
grant all privileges on wordpress.* to 'wordpress'@'localhost';
show databases;
\q
'''

5. Change to WordPress directory

'''
cd /var/www/html/wordpress
'''

6. Copy and rename the wp-config-sample.php file to wp-config.php.

'''
sudo cp wp-config-sample.php wp-config.php
'''

7. Edit file and enter database name, username, and password
using Nano. Use fields for DB_NAME, DB_USER, and DB_PASSWORD.

'''
sudo nano wp-config.php
'''

8. Disable FTP uploads by adding code below at end of file.

9. Change file ownership so that WP can
write files in base directory. 

'''
sudo chown -R www-data:www-data *
'''

10. Run install script using my IP address. 

http://xx.xxx.xxx.xx/wordpress/wp-admin/install.php
define {'FS_METHOD', 'direct');

 

