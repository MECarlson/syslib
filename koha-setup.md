# Koha Installation

**Purpose:** To install an open-source
integrated library system. 

**Tasks:**

1. Create a new virtual machine using Series E2
and Machine Type 2 vCPU, 4 GB Memory. 

2. Create a firewall rule to allow web traffic to port 8080.

Click on hamburger menu
Click VPN Network
Click Firewall
Choose Create Firewall Rule
Add Name: Koha
Add description: open port 8080
Next to Targes select All instances in the network
Source IPv4 ranges - add 0.0.0.0/0
Click Specified protocols and ports
Clock on TCP
Add 8080 in the Ports box
Click Create

3. Log onto new server and update local repositories.
Add gnupg2 and reboot. 

'''
sudo apt update
sudo apt upgrade
sudo apt autoremove -y && sudo apt clean
sudo apt install gnupg2
sudo reboot now
'''

4. Switch to root user.

'''
sudo su
'''

5. Add Koha repository and add digital
signature to verify repository.

'''
echo 'deb http://debian.koha-community.org/koha stable main' | sudo tee /etc/apt/sources.list.d/koha.list

wget -q -O- https://debian.koha-community.org/koha/gpg.asc | sudo apt-key add -
'''

6. Install Koha.

'''
apt update
apt install koha-common
'''

7. Configure Koha. Edit koha-sites.conf file

'''
nano /etc/koha/koha-sites.conf
'''

Change INTRAPORT="80" to INTRAPORT="8080"

8. Install and setup mysql server.

'''
apt install mysql-server
'''

9. Set root mysql password.

'''
mysqladmin -u root passwrod bibliolib1
'''

10. Enable URL rewriting and CGI functionality in Apache2

'''
a2enmod rewrite
a2enmod cgi
systemctl restart Apache2
'''

11. Create database for Koha.

'''
koha-create --create-db bibliolib
'''

12. Edit Apache2 to listen on port 8080.

'''
nano /etc/apache2/ports.conf
'''

Add listen 8080

13. Ensure configuration is valid and restart.

'''
apachectl configtest
systemctl restart apache2
'''

14. Disable default Apache2, enable traffic compression,
and bibliolib. Reload and restart Apache2.

'''
a2dissite 000-default
a2enmod deflate
a2ensite bibliolib
systemctl reload apache2
systemctl restart apache2
'''

15. Complete Koha installation using web installer.

Locate username and password in Nano.

'''
nano /etc/koha/sites/bibliolib/koha-conf.xml
'''

Look for the config stanza (line number 252) and
the line beginning with user (line number 257).
Password is on the line after (line number 258).

Visit http://IP_ADDRESS:8080 and complete setup. 
