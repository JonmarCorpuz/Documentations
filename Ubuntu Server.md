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

# Configurating Ubuntu Server

## Netplan

1. sudo vim /etc/netplan/<CONFIGURATION FILE>
```Bash
network:
  ethernets:
    <NIC>:
      [OPTIONS]
version: <VERSION>
```

2. Apply the changes
```Bash
sudo netplan apply
```

## SSH Keys

### Generate a Pair of SSH Keys

1. empty
```Bash
ssh-keygen -t rsa -b 4096 -C "<COMMENT>"
```

### Copy a Pair of SSH Keys to Another Machine

1. empty
```Bash
ssh-copy-id <TARGET USER>@<TARGET IP ADDRESS>
```

## ufw



# Sources

ufw:
- https://wiki.ubuntu.com/UncomplicatedFirewall

