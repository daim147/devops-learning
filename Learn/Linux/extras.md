# Linux Commands and System Information

## Command Prompt Explained

The default Vagrant command prompt `[vagrant@localhost ~]$` consists of:

- **Username**: `vagrant`
- **Hostname**: `localhost`
- **Directory**: `~` (home directory)
- **Privilege indicator**:
  - `$` for normal user
  - `#` for root user

## Useful Commands

### File Operations

Create multiple files in sequence:

```bash
touch file{1..5}.txt
```

This creates: `file1.txt`, `file2.txt`, `file3.txt`, `file4.txt`, `file5.txt`

### Working with /dev/null

`/dev/null` is a special file that:

- Discards all data written to it
- Used for output suppression
- Common usage:

  ```bash
  command > /dev/null    # Suppress command output
  cat /dev/null > file   # Clear file contents
  ```

## System Configuration

### Hostname Management

**Temporary Change (until reboot)**

```bash
sudo hostname new-hostname
```

**Permanent Change**

```bash
sudo hostnamectl set-hostname new-hostname
```

**Manual Configuration**

1. Edit hostname file:

   ```bash
   sudo vim /etc/hostname
   ```

2. Update hosts file:

   ```bash
   sudo vim /etc/hosts
   ```

## File Creation with Content

### Creating HTML File Using Heredoc

```bash
cat > file.html <<EOF
<!DOCTYPE html>
<html>
<head>
    <title>My Webpage</title>
</head>
<body>
    <h1>Welcome to my webpage!</h1>
</body>
</html>
EOF
```

> **Note**: When using heredoc (`<<EOF`), ensure there are no spaces between `<<` and `EOF` or around `EOF`

## IF cant login with passwd

open the file `/etc/ssh/sshd_config` and change the line `PasswordAuthentication no` to `PasswordAuthentication yes`

than restart the sshd service with `sudo systemctl restart sshd` or `sudo service ssh restart`

## Key Based Authentication

### Generate SSH Key Pair

```bash
# -t rsa: Specifies the type of key to create (RSA)
# -b 4096: Specifies the number of bits in the key (4096 bits)
# -C "your_email@example.com": Provides a comment or label for the key
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

#### Copy Public Key to Remote Host

```bash
ssh-copy-id user@hostname
```
