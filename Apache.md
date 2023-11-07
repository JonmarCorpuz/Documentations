# Installing Apache

1. Set up an Ubuntu server: [Ubuntu Server Procedures](https://github.com/JonmarCorpuz/Documentations/blob/main/Ubuntu%20Server.md)

2. Update the server's local packages and upgrade them to their latest versions
```Bash
sudo apt update && sudo apt upgrade
```

3. Install the Apache HTTP server
```Bash
sudo apt -y install apache2
```

4. Start the Apache web server
```Bash
sudo systemctl start apache2
```

# WebDAV

1. Update the server's local packages and upgrade them to their latest versions
```Bash
sudo apt update && sudo apt upgrade
```

2. Enable the required Apache modules for WebDAV
```Bash
sudo a2enmod dav && sudo a2enmod dav_fs
```

3. Restart the Apache web server to apply the changes
```Bash
sudo systemctl restart apache2
```

4. Create a directory to be shared via WebDAV
```Bash
sudo mkdir /var/www/<WEBDAV DIRECTORY>
```

5. Change the ownership of the newly created WebDAV dedicated directory to the **www-data** group
```Bash
sudo chown -R www-data:www-data /var/www/<WEBDAV DIRECTORY>
```

6. Set the necessary permissions for the WebDAV directory
```Bash
sudo chmod -R 755 /var/www/<WEBDAV DIRECTORY>
```

7. Create a configuration file for the newly created WebDAV directory
```Bash
sudo cp /etc/apache2/site-available/000-default.conf /etc/apache2/site-available/000-<WEBDAV HOST>.conf
```

8. Specify the **DocumentRoot** in the configuration file to point to the previously created WebDAV dedicated directory
```Bash
sudo vim 000-<WEBDAV HOST>.conf
```

9. empty
```Bash
sudo mv /etc/apache2/sites-available/000-default.conf 000-default.conf.bak
```

10. empty
```Bash
sudo a2ensite 000-<WEBDAV HOST>.conf
```

11. empty
```Bash
sudo apache2ctl configtest
```

12. Restart the Apache web server
```Bash
sudo systemctl restart apache2
```

# etckeeper

1. Update the server's local packages and upgrade them to their latest versions
```Bash
sudo apt update && sudo apt upgrade
```

2. Install etckeeper
```Bash
sudo apt -y install etckeeper
```

3. Initialize etckeeper
```Bash
sudo etckeeper init
```

# Keepalived

1. Update the server's local packages and upgrade them to their latest versions
```Bash
sudo apt update && sudo apt upgrade
```

2. Install Keepalived
```Bash
sudo apt -y install keepalived
```

3. empty
```Bash
sudo vim /etc/keepalived/<KEETALIVED CONFIGURATION FILE NAME>.conf
```

```Bash
vrrp_instance VI_1 {
    state <STATE>  # The state of the instance (MASTER or BACKUP)
    interface <INTERFACE>  # The network interface to be used
    virtual_router_id <VIRTUAL ROUTER ID>  # The VRRP identifier (unique per VRRP instance)
    priority <PRIORITY NUMBER>  # The priority of this server in the VRRP group
    advert_int <INTERVAL SECONDS>  # Advertisement interval in seconds

    authentication {
        auth_type <AUTHENTICATION TYPE>  # Authentication type (PASS for plain text)
        auth_pass <PASSWORD>  # Password for authentication
    }

    virtual_ipaddress {
        <IP ADDRESS>  # Virtual IP address to be shared among the servers
    }
}
```

4. empty
```Bash
sudo ufw allow in on <INTERFACE> from <IP ADDRESS> to 224.0.0.18 proto ah comment "<COMMENT>" 
```

5. empty
```Bash
sudo systemctl restart ufw && sudo systemctl restart keepalived
```

6. empty
```Bash
sudo systemctl status ufw && sudo systemctl status keepalived
```

# JMeter

1. Update the server's local packages and upgrade them to their latest versions
```Bash
sudo apt update && sudo apt upgrade
```

2. Install Java
```Bash
sudo apt -y install openjdk-19-jre-headless
```


# SSL 

## Create a Self-Signed SSL Certificate for Apache

1. Update the server's local packages and upgrade them to their latest versions
```Bash
sudo apt update && sudo apt upgrade
```

2. empty
```Bash
sudo ufw allow "Apache Full"
```

3. Activate Apache's `mod_ssl` module
```Bash
sudo a2enmod ssl
```

4. Restart Apache
```Bash
sudo systemctl restart apache2
```

5. Generate a self-signed SSL certificate using OpenSSL
```Bash
sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/apache-selfsigned.key -out /etc/ssl/certs/apache-selfsigned.crt
```
```Bash
Country Name (2 letter code) [XX]:US
State or Province Name (full name) []:Example
Locality Name (eg, city) [Default City]:Example 
Organization Name (eg, company) [Default Company Ltd]:Example Inc
Organizational Unit Name (eg, section) []:Example Dept
Common Name (eg, your name or your server's hostname) []:<
Email Address []:webmaster@example.com
```

6. Create a new configuration file
```Bash
sudo vim /etc/apache2/sites-available/<CONFIGURATION FILE NAME>.conf
```
```Bash
<VirtualHost *:443>
   ServerName your_domain_or_ip
   DocumentRoot /var/www/your_domain_or_ip

   SSLEngine on
   SSLCertificateFile /etc/ssl/certs/apache-selfsigned.crt
   SSLCertificateKeyFile /etc/ssl/private/apache-selfsigned.key
</VirtualHost>
```

7. empty
```Bash
sudo a2ensite your_domain_or_ip.conf
```

8. empty
```Bash
sudo apache2ctl configtest
```

9. empty
```Bash
sudo systemctl reload apache2
```

### Redirect Apache from HTTP to HTTPS

1. empty
```Bash
sudo vim /etc/apache2/sites-available/your_domain_or_ip.conf
```
```Bash
<VirtualHost *:80>
	ServerName your_domain_or_ip
	Redirect / https://your_domain_or_ip/
</VirtualHost>
```

2. empty
```Bash
sudo apachectl configtest
```

3. empty
```Bash
sudo systemctl reload apache2
```

# Hardening the Apache Web Server

## Hide Apache Version and Operating System

1. empty
```Bash
sudo vim /etc/apache2/conf-enabled/security.conf
```
```Bash
ServerSignature Off 
ServerTokens Prod
```

2. Reload the Apache Web Server
```Bash
sudo systemctl restart apache2
```

# Sources

Keepalived:
- https://tecadmin.net/setup-ip-failover-on-ubuntu-with-keepalived/

SSL:
- https://www.digitalocean.com/community/tutorials/how-to-create-a-self-signed-ssl-certificate-for-apache-in-ubuntu-20-04-fr

Hardening the Apache Web Server:
- https://hostadvice.com/how-to/web-hosting/ubuntu/how-to-harden-your-apache-web-server-on-ubuntu-18-04/
