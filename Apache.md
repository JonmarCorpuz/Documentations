# Apache for Ubuntu Server

1. Set up an Ubuntu server: [Ubuntu Server Procedures](https://github.com/JonmarCorpuz/Documentations/blob/main/Ubuntu%20Server.md)

2. Update the server's local packages adn upgrade them to their latest versions
```Bash
sudo apt update && sudo apt upgrade
```

3. Install the Apache HTTP server
```Bash
sudo apt install apache2
```

4. Start the Apache web server
```Bash
sudo systemctl start apache2
```
