# Installing Apache

```Bash
# 1. Set up an Ubuntu server: https://github.com/JonmarCorpuz/Documentations/blob/main/Ubuntu%20Server.md

# 2. Update the server's local packages and upgrade them to their latest versions
sudo apt update && sudo apt upgrade

# 3. Install the Apache HTTP server
sudo apt -y install apache2

# 4. Start the Apache web server
sudo systemctl start apache2
```

# WebDAV

```Bash
# 1. Update the server's local packages and upgrade them to their latest versions
sudo apt update && sudo apt upgrade

# 2. Enable the required Apache modules for WebDAV
sudo a2enmod dav && sudo a2enmod dav_fs

# 3. Restart the Apache web server to apply the changes
sudo systemctl restart apache2

# 4. Create a directory to be shared via WebDAV
sudo mkdir /var/www/<WEBDAV DIRECTORY>

# 5. Change the ownership of the newly created WebDAV dedicated directory to the **www-data** group
sudo chown -R www-data:www-data /var/www/<WEBDAV DIRECTORY>

# 6. Set the necessary permissions for the WebDAV directory
sudo chmod -R 755 /var/www/<WEBDAV DIRECTORY>

# 7. Create a configuration file for the newly created WebDAV directory
sudo cp /etc/apache2/site-available/000-default.conf /etc/apache2/site-available/000-<WEBDAV HOST>.conf

# 8. Specify the **DocumentRoot** in the configuration file to point to the previously created WebDAV dedicated directory
sudo vim 000-<WEBDAV HOST>.conf

# 9. empty
sudo mv /etc/apache2/sites-available/000-default.conf 000-default.conf.bak

# 10. empty
sudo a2ensite 000-<WEBDAV HOST>.conf

# 11. empty
sudo apache2ctl configtest

#12. Restart the Apache web server
sudo systemctl restart apache2
```

# etckeeper

```Bash
# 1. Update the server's local packages and upgrade them to their latest versions
sudo apt update && sudo apt upgrade

# 2. Install etckeeper
sudo apt -y install etckeeper

# 3. Initialize etckeeper
sudo etckeeper init
```

# Keepalived

```Bash
# 1. Update the server's local packages and upgrade them to their latest versions
sudo apt update && sudo apt upgrade

# 2. Install Keepalived
sudo apt -y install keepalived

# 3. empty
sudo vim /etc/keepalived/<KEETALIVED CONFIGURATION FILE NAME>.conf

#vrrp_instance VI_1 {
    #state <STATE>  # The state of the instance (MASTER or BACKUP)
    #interface <INTERFACE>  # The network interface to be used
    #virtual_router_id <VIRTUAL ROUTER ID>  # The VRRP identifier (unique per VRRP instance)
    #priority <PRIORITY NUMBER>  # The priority of this server in the VRRP group
    #advert_int <INTERVAL SECONDS>  # Advertisement interval in seconds

    #authentication {
        #auth_type <AUTHENTICATION TYPE>  # Authentication type (PASS for plain text)
        #auth_pass <PASSWORD>  # Password for authentication
    #}

    #virtual_ipaddress {
        #<IP ADDRESS>  # Virtual IP address to be shared among the servers
    #}
#}

# 4. empty
sudo ufw allow in on <INTERFACE> from <IP ADDRESS> to 224.0.0.18 proto ah comment "<COMMENT>" 

# 5. empty
sudo systemctl restart ufw && sudo systemctl restart keepalived

# 6. empty
sudo systemctl status ufw && sudo systemctl status keepalived
```

# JMeter

```Bash
# 1. Update the server's local packages and upgrade them to their latest versions
sudo apt update && sudo apt upgrade

# 2. Install Java
sudo apt -y install openjdk-19-jre
#sudo apt-get purge openjdk*

# 3. empty
wget https://dlcdn.apache.org//jmeter/binaries/apache-jmeter-5.6.2.tgz

# 4. emtpy
tar xvf apache-jmeter-5.6.2.tgz

# 5. empty
mv apache-jmeter-5.6.2 JMeter

# 6. empty
cd JMeter/bin

# 7. empty
./jmeter
```

# SSL 

## Create a Self-Signed SSL Certificate for Apache

```Bash
# 1. Update the server's local packages and upgrade them to their latest versions
sudo apt update && sudo apt upgrade

# 2. empty
sudo ufw allow "Apache Full"

# 3. Activate Apache's `mod_ssl` module
sudo a2enmod ssl

# 4. Restart Apache
sudo systemctl restart apache2

# 5. empty
openssl genrsa -out <FILENAME1>.key <BITS>

# 6. empty
openssl req -new -key <FILENAME1>.key -out <FILENAME2>.csr

# 7. empty
openssl x509 -req -days 365 -in <FILENAME2>.csr -signkey <FILENAME1>.key -out <FILENAME3>.crt

#Country Name (2 letter code) [XX]: <COUNTRY NAME>
#State or Province Name (full name) []: <STATE OR PROVINCE>
#Locality Name (eg, city) [Default City]: <CITY NAME> 
#Organization Name (eg, company) [Default Company Ltd]: <ORGANIZATION NAME>
#Organizational Unit Name (eg, section) []: <DEPARTMENT NAME>
#Common Name (eg, your name or your server's hostname) []: <FQDN>
#Email Address []: <EMAIL ADDRESS>

8. empty
vm <FILENAME1>.key /etc/ssl/private

9. empty
vm <FILENAME2>.csr /etc/ssl/certs

10. empty
vm <FILENAME3>.crt /etc/ssl/certs

# 11. empty
sudo vim /etc/apache2/sites-available/<WEBDAV DIRECTORY>.conf

#<VirtualHost *:443>
   #DocumentRoot /var/www/<WEBDAV DIRECTORY>

   #SSLEngine on
   #SSLCertificateFile /etc/ssl/certs/<FILENAME3>.crt
   #SSLCertificateKeyFile /etc/ssl/private/<FILENAME1>.key
#</VirtualHost>

# 12. empty
sudo apache2ctl configtest

# 13. empty
sudo systemctl reload apache2
```

# Hardening the Apache Web Server

## Hide Apache Version and Operating System

```Bash
# 1. empty
sudo vim /etc/apache2/conf-enabled/security.conf

#ServerSignature Off 
#ServerTokens Prod

# 2. Reload the Apache Web Server
sudo systemctl restart apache2
```

# Sources

Keepalived:
- https://tecadmin.net/setup-ip-failover-on-ubuntu-with-keepalived/

JMeter:
- https://askubuntu.com/questions/1443555/cant-run-jmeter-on-ubuntu-no-x11-display-variable-was-set
- https://www.youtube.com/watch?v=bJRPTHCVDUg

SSL:
- https://www.digitalocean.com/community/tutorials/how-to-create-a-self-signed-ssl-certificate-for-apache-in-ubuntu-20-04-fr

Hardening the Apache Web Server:
- https://hostadvice.com/how-to/web-hosting/ubuntu/how-to-harden-your-apache-web-server-on-ubuntu-18-04/
