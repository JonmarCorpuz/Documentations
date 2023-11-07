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

# Secure SHell

## Generate a Pair of SSH Keys

1. empty
```Bash
ssh-keygen -t rsa -b 4096 -C "<COMMENT>"
```

## Copy a Pair of SSH Keys onto Another Machine

1. empty
```Bash
ssh-copy-id <TARGET USER>@<TARGET IP ADDRESS>
```

## Disable SSH Access Via Password

1. empty
```Bash
sudo vim /etc/ssh/sshd_config
```

```Bash
# Change from:
PasswordAuthentication yes

# Change to:
PasswordAuthentication no
```

2. Restart the SSH service to apply the new configuration
```Bash
sudo systemctl restart sshd
```

# Uncomplicated Firewall 

# Sources

Uncomplicated Firewall:
- https://wiki.ubuntu.com/UncomplicatedFirewall
