
```Bash
curl --request GET \
  --url 'https://www.tenable.com/downloads/api/v2/pages/nessus/files/Nessus-10.6.2-ubuntu1404_amd64.deb' \
  --output 'Nessus-10.6.2-ubuntu1404_amd64.deb'
```

```Bash
sudo dpkg -i Nessus-10.6.2-ubuntu1404_amd64.deb 
```

```Bash
sudo systemctl start nessusd
```

```Bash
sudo systemctl enable nessusd
```

```Bash
firefox https://127.0.0.1:8834
```

