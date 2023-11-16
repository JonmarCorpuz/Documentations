# Procedures

## Setting Up Ubuntu Server 

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt1.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt2.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt3.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt4.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt5.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt6.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt7.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt8.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt9.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt11.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt12.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt13.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt14.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt15.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt16.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt17.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt18.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt19.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt20.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt21.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt22.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt23.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt24.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt25.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt26.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt27.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt28.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt29.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt30.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt31.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt32.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt33.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt34.png)

![](https://github.com/JonmarCorpuz/Documentations/blob/main/Assets/Ubuntu%20Server%20pt35.png)

```Bash
sudo vim /etc/netplan/00-installer-config.yaml
```

```Bash
sudo netpan apply
```

## 

```Bash
sudo vim /etc/hosts/
```

```Bash
sudo vim /etc/resolv.conf
```

##

```Bash
sudo wget https://files.zimbra.com/downloads/8.8.15_GA/zcs-8.8.15_GA_4179.UBUNTU20_64.20211118033954.tgz
```

```Bash
tar xvf zcs-8.8.15_GA_4179.UBUNTU20_64.20211118033954.tgz
```

```Bash
mv zcs-8.8.15_GA_4179.UBUNTU20_64.20211118033954 zimbra
```

```Bash
cd zimbra
```

```Bash
sudo ./install.sh
```

```Bash
sudo su
```

```Bash
su - zimbra
```

```Bash
zmcontrol restart
```

# Sources

## Installing Zimbra on Ubuntu Server
- https://www.youtube.com/watch?v=BtPKDznlip0
- http://docs.zimbra.com/docs/ne/6.0.8/administration_guide/A_app-command-line.20.18.html

## Linking Zimbra to Active Directory
- https://wiki.zimbra.com/wiki/Configure_authentication_with_Active_Directory
- https://prohoster.info/en/blog/administrirovanie/avtomaticheskoe-sozdanie-akkauntov-iz-ad-v-zimbra-collaboration-suite
- https://www.youtube.com/watch?v=L5JprVARqLc

## Secure Authentication
- https://wiki.zimbra.com/wiki/Secure_Authentication_between_Zimbra_and_AD#:~:text=Click%20Start%20%3E%20Run%20%3E%20type%20ldp,FQDN%20of%20the%20AD%20server.&text=Then%2C%20you%20can%20Bind%20to%20AD.

## Error Solutions
- https://www.ricmedia.com/tutorials/set-permanent-dns-nameservers-ubuntu-debian-resolv-conf
- https://wiki.zimbra.com/wiki/Email_doesn%27t_show_up_immediately_in_the_inbox
- https://wiki.zimbra.com/wiki/Email_doesn%27t_show_up_immediately_in_the_inbox

