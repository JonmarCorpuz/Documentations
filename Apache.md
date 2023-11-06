# Ubuntu Procedures

## Installing an Apache Web Server

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

## Apache Extensions and Tools 

### WebDAV

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

9. Restart the Apache web server
```Bash
sudo systemctl restart apache2
```

### etckeeper

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

4. Commit any changes made
```Bash
sudo etckeeper commit
```

### JMeter


