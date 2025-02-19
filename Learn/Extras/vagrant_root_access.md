# Setting Up Root Access for Vagrant VM in VS Code

## Step 1: Set Root Password

1. SSH into your Vagrant VM:

```bash
vagrant ssh
```

2. Switch to root and set a password:

```bash
sudo -i
passwd
```

Enter and confirm your desired root password.

## Step 2: Enable Root SSH Access

1. Edit the SSH configuration:

```bash
sudo nano /etc/ssh/sshd_config
```

2. Find and modify these lines:

```
PermitRootLogin yes
PasswordAuthentication yes
```

3. Restart SSH service:

```bash
sudo systemctl restart sshd
```

## Step 3: Configure VS Code

1. Open VS Code
2. Press `Cmd+Shift+P` (Mac) or `Ctrl+Shift+P` (Windows/Linux)
3. Type "Remote-SSH: Add New SSH Host"
4. Enter the SSH command (use your Vagrant VM's port from `vagrant ssh-config`):

```
ssh root@localhost -p 2222
```

5. Choose the SSH config file location
6. Connect to the host using "Remote-SSH: Connect to Host"
7. Enter the root password when prompted

You can now edit files with root privileges in VS Code!

Note: Remember to be careful when working as root, as you can accidentally damage the system.
