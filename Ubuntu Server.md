# Installing Ubuntu Server with RAID 10

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt1.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt2.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt3.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt4.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt5.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt6.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt7.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt8.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt9.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt10.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt11.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt12.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt13.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt14.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt15.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt16.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt17.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt18.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt19.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt20.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt21.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt22.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt23.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt24.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt25.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt26.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt27.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt28.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt29.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt30.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt31.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt32.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt33.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt34.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt35.png)

![](https://github.com/JonmarCorpuz/Procedures/blob/main/Assets/Ubuntu%20Server%20pt36.png)

# Configuring Ubuntu Server

## Netplan

```Bash
# 1. empty
sudo vim /etc/netplan/<CONFIGURATION FILE>

#network:
  #ethernets:
    #<NIC>:
      #[OPTIONS]
#version: <VERSION>

# 2. Apply the changes
sudo netplan apply
```

## SSH

### Generate a Pair of SSH Keys

```Bash
# 1. empty
ssh-keygen -t rsa -b 4096 -C "<COMMENT>"
```

### Copy a Pair of SSH Keys onto Another Machine

```Bash
# 1. empty
ssh-copy-id <TARGET USER>@<TARGET IP ADDRESS>
```

### Disable SSH Access Via Password

```Bash
# 1. empty
sudo vim /etc/ssh/sshd_config

#PasswordAuthentication no
#ChallengeResponseAuthentication no
#UsePAM no

# 2. Restart the SSH service to apply the new configuration
sudo systemctl restart sshd
```

## Uncomplicated Firewall 

### Blocking ICMP

```Bash
# 1. Block incoming ICMP
sudo ufw deny in proto icmp
```

### Blocking IPv6

```Bash
# 1. Block IPv6
sudo ufw deny from any to any proto ipv6
```

# Sources

Uncomplicated Firewall:
- https://wiki.ubuntu.com/UncomplicatedFirewall
