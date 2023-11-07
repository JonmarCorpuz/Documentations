# Netplan

1. empty

```Bash
sudo vim /etc/netplan/<CONFIGURATION FILE>
```

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

# SSH Keys

## Generate a Pair of SSH Keys

1. empty
```Bash
ssh-keygen -t rsa -b 4096 -C "<COMMENT>"
```

## Copy a Pair of SSH Keys to Another Machine

1. empty
```Bash
ssh-copy-id <TARGET USER>@<TARGET IP ADDRESS>
```

# Uncomplicated Firewall 

# Sources

Uncomplicated Firewall:
- https://wiki.ubuntu.com/UncomplicatedFirewall
