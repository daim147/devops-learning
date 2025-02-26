# SSH (Secure Shell) Guide

SSH is a protocol for securely connecting to remote systems over an unsecured network. This guide covers SSH key management, configuration, and common operations.

## Table of Contents

- [SSH Key Generation](#ssh-key-generation)
- [Managing SSH Keys](#managing-ssh-keys)
- [SSH Authentication](#ssh-authentication)
- [SSH Configuration](#ssh-configuration)
- [SSH Commands and Usage](#ssh-commands-and-usage)
- [File Transfer with SSH](#file-transfer-with-ssh)
- [Port Forwarding](#port-forwarding)
- [Best Practices](#best-practices)
- [Troubleshooting](#troubleshooting)

## SSH Key Generation

SSH keys provide a secure way to authenticate with remote servers without using passwords.

### Generating an SSH Key Pair

```bash
# Generate an RSA key pair (4096 bits recommended for security)
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

# Generate an Ed25519 key (modern, more secure alternative)
ssh-keygen -t ed25519 -C "your_email@example.com"
```

During key generation, you'll be prompted to:

1. Choose a file location (default: `~/.ssh/id_rsa` or `~/.ssh/id_ed25519`)
2. Enter a passphrase (optional but recommended for security)

### Key Files Created

- **Private key**: `~/.ssh/id_rsa` or `~/.ssh/id_ed25519` (KEEP THIS SECRET)
- **Public key**: `~/.ssh/id_rsa.pub` or `~/.ssh/id_ed25519.pub` (share this)

## Managing SSH Keys

### Listing Your SSH Keys

```bash
# List files in your SSH directory
ls -la ~/.ssh
```

### Adding Keys to SSH Agent

The SSH agent keeps your keys in memory so you don't have to enter the passphrase every time.

```bash
# Start the SSH agent in the background
eval "$(ssh-agent -s)"

# Add your private key to the SSH agent
ssh-add ~/.ssh/id_rsa

# List keys added to the agent
ssh-add -l
```

## SSH Authentication

### Copying Your Public Key to a Remote Server

Method 1: Using `ssh-copy-id` (simplest method):

```bash
ssh-copy-id username@remote-server
```

Method 2: Manual copy (if `ssh-copy-id` is not available):

```bash
# Display your public key
cat ~/.ssh/id_rsa.pub

# Copy the output and add it to ~/.ssh/authorized_keys on the remote server
```

Method 3: Using a one-liner:

```bash
cat ~/.ssh/id_rsa.pub | ssh username@remote-server "mkdir -p ~/.ssh && chmod 700 ~/.ssh && cat >> ~/.ssh/authorized_keys && chmod 600 ~/.ssh/authorized_keys"
```

### Testing SSH Connection

```bash
# Basic connection test
ssh username@remote-server

# Verbose mode for troubleshooting
ssh -v username@remote-server
```

## SSH Configuration

SSH configuration files allow you to customize SSH client behavior.

### Client Configuration File

The main SSH client configuration file is `~/.ssh/config`. Creating and configuring this file enables aliases and custom settings.

Example configuration:

```
# Default settings for all hosts
Host *
    AddKeysToAgent yes
    IdentityFile ~/.ssh/id_rsa
    ServerAliveInterval 60

# Specific host configuration
Host dev-server
    HostName dev.example.com
    User developer
    Port 2222
    IdentityFile ~/.ssh/dev_key

# Jump host configuration
Host prod-server
    HostName prod.example.com
    User admin
    ProxyJump jumphost
```

### Using Host Aliases

With the config file above, you can simply use:

```bash
# Instead of ssh developer@dev.example.com -p 2222 -i ~/.ssh/dev_key
ssh dev-server
```

## SSH Commands and Usage

### Basic Connection

```bash
# Connect to a remote server
ssh username@hostname

# Connect on a specific port
ssh -p 2222 username@hostname

# Use a specific identity file
ssh -i ~/.ssh/specific_key username@hostname
```

### Running Remote Commands

```bash
# Run a single command on the remote server
ssh username@hostname "ls -la /var/log"

# Run multiple commands
ssh username@hostname "cd /var/log && grep -i error apache2/error.log"
```

## File Transfer with SSH

### SCP (Secure Copy Protocol)

Copy files and directories between hosts securely.

```bash
# Copy a local file to a remote server
scp /path/to/local/file username@hostname:/path/to/remote/directory

# Copy a remote file to local system
scp username@hostname:/path/to/remote/file /path/to/local/directory

# Copy directory recursively
scp -r /path/to/local/directory username@hostname:/path/to/remote/directory

# Copy using a specific port
scp -P 2222 /path/to/file username@hostname:/path/to/destination
```

### SFTP (SSH File Transfer Protocol)

An interactive file transfer program.

```bash
# Start an SFTP session
sftp username@hostname

# SFTP commands (once connected):
# pwd           - Print working directory on remote
# lpwd          - Print working directory on local
# cd            - Change directory on remote
# lcd           - Change directory on local
# ls            - List files on remote
# lls           - List files on local
# get file      - Download file
# put file      - Upload file
# mget *.txt    - Download multiple files
# mput *.txt    - Upload multiple files
# exit          - Quit SFTP
```

## Port Forwarding

SSH can create secure tunnels for traffic forwarding.

### Local Port Forwarding

Forward a local port to a remote destination through an SSH connection.

```bash
# Forward local port 8080 to remote server's port 80
ssh -L 8080:localhost:80 username@hostname

# Forward local port 3307 to a database server via the SSH host
ssh -L 3307:database-server:3306 username@ssh-host
```

After executing the command, you can access the remote service by connecting to `localhost:8080`.

### Remote Port Forwarding

Forward a remote port to a local destination.

```bash
# Forward remote port 8080 to local port 80
ssh -R 8080:localhost:80 username@hostname
```

### Dynamic Port Forwarding (SOCKS Proxy)

Create a SOCKS proxy on your local system.

```bash
# Create a SOCKS proxy on port 1080
ssh -D 1080 username@hostname
```

## Best Practices

1. **Use strong keys**: Use RSA (4096 bits) or Ed25519 keys.
2. **Protect your private key**: Never share it and use a strong passphrase.
3. **Use the SSH config file**: Maintain settings for different servers in `~/.ssh/config`.
4. **Disable password authentication** on servers when possible.
5. **Use non-standard ports** for public-facing servers.
6. **Limit user access**: Configure `AllowUsers` in the server's `sshd_config`.
7. **Use key rotation**: Periodically generate new keys and update authorized_keys.
8. **Keep SSH software updated**: Apply security patches regularly.

## Troubleshooting

### Common Issues and Solutions

1. **Permission errors**:

   ```bash
   # Fix permissions for SSH files
   chmod 700 ~/.ssh
   chmod 600 ~/.ssh/id_rsa
   chmod 644 ~/.ssh/id_rsa.pub
   chmod 600 ~/.ssh/config
   ```

2. **Connection refused**:

   - Verify SSH service is running on the remote host
   - Check firewall settings
   - Ensure correct hostname and port

3. **Host key verification failed**:

   ```bash
   # Remove the problematic key
   ssh-keygen -R hostname
   ```

4. **Debug connection issues**:

   ```bash
   # Verbose connection information
   ssh -vvv username@hostname
   ```

5. **Agent forwarding issues**:

   ```bash
   # Ensure agent forwarding is enabled in your SSH config
   Host *
     ForwardAgent yes
   ```

### SSH Logs

Check SSH logs for troubleshooting:

```bash
# On most Linux systems
sudo tail -f /var/log/auth.log

# On Red Hat/CentOS/Fedora
sudo tail -f /var/log/secure
```

These logs often contain detailed information about SSH connection attempts and failures.
