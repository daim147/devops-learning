# Linux Folder Structure

## Table of Contents

- [Linux Folder Structure](#linux-folder-structure)
  - [Table of Contents](#table-of-contents)
  - [/etc](#etc)
  - [/root](#root)
  - [/home](#home)
  - [/bin](#bin)
  - [/sbin](#sbin)
  - [/usr](#usr)
  - [/var](#var)
  - [/tmp](#tmp)
  - [/dev](#dev)
  - [/proc](#proc)
  - [/sys](#sys)
  - [/boot](#boot)
  - [/mnt](#mnt)
  - [/media](#media)
  - [/opt](#opt)
  - [/lib](#lib)
  - [/lib64](#lib64)
  - [/srv](#srv)
  - [/run](#run)
  - [/lost+found](#lostfound)

All the files and directories in Linux are arranged in a hierarchical structure. The root directory `/` is the top-level directory in the file system, and all other directories are subdirectories of the root directory. The Linux file system follows the Filesystem Hierarchy Standard (FHS), which defines the structure and contents of the file system. The files _can vary from one distribution to another_, but the basic structure remains the same.

These are some of the common directories found in a Linux file system:

## /etc

`/etc` stands for "et cetera" and is used to store system configuration files. It contains configuration files for the system and applications, as well as scripts and other files used by the system. This directory is crucial for system administration as it controls how the system behaves.

**Use Cases:**

- Configuring system-wide settings
- Setting up services like web servers, databases, SSH
- Managing user authentication and authorization
- Configuring network interfaces and firewall rules

**Tips:**

- Always make backups before editing files in `/etc`: `sudo cp /etc/file /etc/file.bak`
- Use version control for tracking changes: `git init && git add . && git commit -m "Initial configuration"`
- Set proper permissions to prevent unauthorized changes
- Use configuration management tools like Ansible, Puppet, or Chef for managing configurations at scale

**Examples:**

```bash
# Edit SSH server configuration
sudo nano /etc/ssh/sshd_config

# Configure hostname
sudo hostnamectl set-hostname new-hostname

# Configure network interfaces
sudo nano /etc/network/interfaces

# Manage systemd service
sudo systemctl edit nginx.service
```

<details>
  <summary>Common files and directories in /etc</summary>

- `/etc/os-release` - Contains information about the operating system release.
- `/etc/passwd` - Contains information about user accounts.
- `/etc/group` - Contains information about user groups.
- `/etc/shadow` - Contains encrypted password information for user accounts.
- `/etc/hostname` - Contains the hostname of the system.
- `/etc/hosts` - Contains IP addresses and hostnames for the system.
- `/etc/resolv.conf` - Contains DNS resolver configuration.
- `/etc/fstab` - Contains file system mount information.
- `/etc/mtab` - Contains a list of currently mounted file systems.
- `/etc/crontab` - Contains scheduled tasks for the system.
- `/etc/profile` - Contains system-wide shell settings.
- `/etc/sudoers` - Contains sudo configuration settings.
- `/etc/init.d/` - Contains system startup scripts (legacy, often replaced by systemd).
- `/etc/systemd/` - Contains systemd configuration files.
- `/etc/apt/` - Contains APT package manager configuration files (Debian/Ubuntu).
- `/etc/yum/` - Contains YUM package manager configuration files (CentOS/RHEL).
- `/etc/nginx/` - Contains Nginx web server configuration files.
- `/etc/apache2/` - Contains Apache web server configuration files.
- `/etc/ssh/` - Contains SSH server configuration files.
- `/etc/samba/` - Contains Samba server configuration files.
- `/etc/mysql/` - Contains MySQL database server configuration files.
- `/etc/postfix/` - Contains Postfix mail server configuration files.
- `/etc/ssl/` - Contains SSL certificate and key files.
- `/etc/logrotate.d/` - Contains log rotation configuration files.
- `/etc/rsyslog.d/` - Contains rsyslog configuration files.
- `/etc/sysctl.conf` - Contains kernel parameters configuration.
- `/etc/modprobe.d/` - Contains kernel module configuration files.
- `/etc/network/` - Contains network configuration files (Debian/Ubuntu).
- `/etc/apache2/sites-available/` - Contains Apache virtual host configuration files.
- `/etc/apache2/sites-enabled/` - Contains enabled Apache virtual host configuration files.
- `/etc/nginx/sites-available/` - Contains Nginx server block configuration files.
- `/etc/nginx/sites-enabled/` - Contains enabled Nginx server block configuration files.
- `/etc/php/` - Contains PHP configuration files.
- `/etc/php/php.ini` - Contains PHP configuration settings.

  Example: `/etc/hosts`

  ```bash
  127.0.0.1   localhost
  127.0.1.1   your-hostname

  # The following lines are desirable for IPv6 capable hosts
  ::1     localhost ip6-localhost ip6-loopback
  ff02::1 ip6-allnodes
  ff02::2 ip6-allrouters
  ```

  Example: `/etc/nginx/nginx.conf`

  ```nginx
  user www-data;
  worker_processes auto;
  pid /run/nginx.pid;
  include /etc/nginx/modules-enabled/*.conf;

  events {
    worker_connections 768;
    # multi_accept on;
  }

  http {
    sendfile on;
    tcp_nopush on;
    tcp_nodelay on;
    keepalive_timeout 65;
    types_hash_max_size 2048;
    # ... more configuration ...
  }
  ```

  </details>

## /root

The `/root` directory is the home directory for the root user. The root user is the superuser with full administrative privileges on the system. The root user can perform any operation on the system, including modifying system files and configurations.

**Use Cases:**

- Store root-specific configuration files
- Keep scripts and tools for system administration
- Store backup files and recovery tools

**Tips:**

- Keep this directory organized to easily find administrative tools
- Don't store sensitive information in plaintext
- Restrict access to this directory (default permissions are typically 700)
- Consider using sudo instead of working directly as root

**Examples:**

```bash
# Access root's home directory (requires root privileges)
sudo -i
cd ~

# Create an administration script in root's home
sudo nano /root/system_backup.sh

# Check what's in root's directory
sudo ls -la /root
```

## /home

The `/home` directory contains home directories for regular users. Each user on the system has a separate home directory located within `/home`. The home directory is the default location where users store their personal files and configurations.

**Use Cases:**

- Storing user documents, downloads, and personal files
- Keeping user-specific configurations in dot files (like .bashrc)
- Running user applications and scripts
- Managing user environment settings

**Tips:**

- Set disk quotas to prevent individual users from consuming all disk space
- Implement regular backups of user home directories
- Consider separating `/home` to a different partition or disk
- Use ACLs for fine-grained permission control

**Examples:**

```bash
# Create a new user with home directory
sudo useradd -m newuser

# Set disk quota for a user
sudo setquota -u username 5G 6G 0 0 /home

# Backup a user's home directory
sudo rsync -av /home/username /backup/

# Check disk usage by user
du -sh /home/*
```

## /bin

The `/bin` directory contains essential system binaries (executable files) that are required for the system to function properly. These binaries are available to all users and are used for common system operations.

**Use Cases:**

- Executing basic commands like ls, cp, mv
- Running shell scripts with bash/sh
- Supporting basic system functionality
- Essential tools for system recovery

**Tips:**

- Don't modify or delete files in this directory
- These commands are available to all users
- In modern distributions, /bin is often a symbolic link to /usr/bin
- Essential for rescue/recovery operations when other directories might not be mounted

**Examples:**

```bash
# List common binaries
ls -la /bin | head -10

# Check where a command is located
which bash
which ls

# Find all shell scripts in /bin
find /bin -type f -exec file {} \; | grep "shell script"
```

## /sbin

The `/sbin` directory contains system binaries that are used for system administration tasks. These binaries are typically used by the root user for system maintenance and configuration.

**Use Cases:**

- System initialization and shutdown
- Network configuration (ifconfig, route)
- Disk and file system management (fdisk, mkfs)
- System maintenance tasks

**Tips:**

- Commands here typically require root privileges
- Regular users may see these commands but can't execute them effectively
- On some systems, these commands are in root's PATH but not in regular users' PATH
- In modern distributions, /sbin is often a symbolic link to /usr/sbin

**Examples:**

```bash
# Network interface configuration
sudo ifconfig eth0 192.168.1.100 netmask 255.255.255.0 up

# Create a filesystem on a partition
sudo mkfs.ext4 /dev/sdb1

# Check/repair filesystem
sudo fsck /dev/sda1

# View system initialization details
sudo systemctl status
```

## /usr

The `/usr` directory contains user-related system files and programs. It is divided into several subdirectories and is one of the largest directories in the file system, containing the majority of user utilities and applications.

**Use Cases:**

- Installing and running user applications
- Storing documentation and manual pages
- Keeping shared libraries for applications
- Storing development tools and header files

**Tips:**

- This directory is often the largest and may be placed on a separate partition
- It's mostly read-only during normal operation
- Most package managers install software here by default
- Can be shared among multiple systems through read-only mounting

**Examples:**

```bash
# List installed applications
ls /usr/bin

# Find manual pages for a command
man -k search_term

# Install software to user directory when you don't have root
./configure --prefix=$HOME/.local && make && make install

# Find libraries that an executable depends on
ldd /usr/bin/firefox
```

<details>
  <summary>Common files and directories in /usr</summary>

- `/usr/bin` - Contains user binaries (executable files).
- `/usr/sbin` - Contains system binaries for system administration tasks.
- `/usr/lib` - Contains shared libraries used by programs.
- `/usr/include` - Contains header files used for software development.
- `/usr/share` - Contains shared data used by programs.
- `/usr/local` - Contains locally installed files and programs.
- `/usr/src` - Contains source code for the Linux kernel and other programs.
- `/usr/share/doc` - Contains documentation files for installed programs.
- `/usr/share/man` - Contains manual pages for installed programs.
- `/usr/share/info` - Contains info pages for installed programs.
- `/usr/share/locale` - Contains locale-specific data for programs.
- `/usr/share/fonts` - Contains font files used by programs.
- `/usr/share/applications` - Contains desktop application launchers.
- `/usr/share/icons` - Contains icon files used by programs.
- `/usr/share/themes` - Contains theme files used by programs.
- `/usr/share/backgrounds` - Contains desktop background images.
- `/usr/share/sounds` - Contains sound files used by programs.
- `/usr/share/mime` - Contains MIME type definitions.
- `/usr/share/zoneinfo` - Contains time zone data.
- `/usr/share/games` - Contains game data files.
- `/usr/share/emacs` - Contains Emacs editor configuration files.
- `/usr/share/vim` - Contains Vim editor configuration files.
- `/usr/share/bash-completion` - Contains bash completion scripts.
- `/usr/share/terminfo` - Contains terminal information files.
- `/usr/share/ssl` - Contains SSL certificate files.
- `/usr/share/certs` - Contains certificate authority certificates.
- `/usr/share/ca-certificates` - Contains trusted CA certificates.
- `/usr/share/gnupg` - Contains GnuPG configuration files.
- `/usr/share/gtk-doc` - Contains GTK documentation files.
- `/usr/share/xml` - Contains XML data files.
- `/usr/share/sgml` - Contains SGML data files.
- `/usr/share/httpd` - Contains Apache HTTP server data files.
- `/usr/share/httpd/icons` - Contains Apache HTTP server icon files.
- `/usr/share/httpd/manual` - Contains Apache HTTP server manual files.
- `/usr/share/httpd/noindex` - Contains Apache HTTP server noindex files.

  Example: `/usr/bin/git` (Git executable)

  ```bash
  #!/bin/sh
  #
  # Git wrapper script
  #
  exec /usr/lib/git-core/git "$@"
  ```

  Example: `/usr/share/man/man1/ls.1.gz` (Manual page for `ls` command)
  </details>

## /var

The `/var` directory contains variable data files that are expected to change in size and content during normal system operation. It is divided into several subdirectories and is used for storing logs, caches, and other dynamic content.

**Use Cases:**

- Storing log files for system and service monitoring
- Managing print and mail queues
- Hosting websites with web servers like Apache or Nginx
- Storing databases for services like MySQL/MariaDB

**Tips:**

- Consider placing `/var` on a separate partition to prevent log files from filling the root partition
- Set up log rotation to manage log file sizes
- Monitor disk usage in `/var/log` regularly
- Use specialized tools like logrotate for managing logs

**Examples:**

```bash
# View system logs
sudo tail -f /var/log/syslog

# Check web server access logs
sudo tail -f /var/log/nginx/access.log

# Set up a new website in Apache
sudo mkdir -p /var/www/mynewsite
sudo chown -R $USER:www-data /var/www/mynewsite

# Check disk usage of log files
sudo du -sh /var/log/*
```

<details>
  <summary>Common files and directories in /var</summary>

- `/var/log` - Contains log files generated by the system and services.
- `/var/spool` - Contains spool files for services such as mail and printing.
- `/var/cache` - Contains cached data for applications.
- `/var/lib` - Contains persistent data files for applications.
- `/var/run` - Contains runtime data files for running processes.
- `/var/lock` - Contains lock files used to prevent multiple instances of a process.
- `/var/tmp` - Contains temporary files that are preserved between system reboots.
- `/var/www` - Contains web server files and data.
- `/var/mail` - Contains user mailboxes.
- `/var/log/audit` - Contains audit log files.
- `/var/log/journal` - Contains systemd journal log files.
- `/var/log/nginx` - Contains Nginx web server log files.
- `/var/log/apache2` - Contains Apache web server log files.
- `/var/log/mysql` - Contains MySQL database server log files.
- `/var/log/postgresql` - Contains PostgreSQL database server log files.

  Example: `/var/log/syslog` (System log file)

  Example: `/var/cache/apt/archives/` (APT package archive cache)
  </details>

## /tmp

The `/tmp` directory is used to store temporary files that are created by system and applications. The contents of this directory are not preserved between system reboots and are automatically deleted when the system restarts.

**Use Cases:**

- Storing temporary files during program execution
- Sharing files between processes temporarily
- Creating temporary workspaces for applications
- Storing session data for applications

**Tips:**

- Don't store important data here as it's cleaned on reboot
- Some distributions clean files older than X days automatically
- You can configure tmpfs to keep /tmp in RAM for better performance
- Set proper permissions when creating files here in scripts

**Examples:**

```bash
# Create a temporary file that gets auto-deleted
tmpfile=$(mktemp)
echo "data" > $tmpfile
cat $tmpfile
# File disappears after system reboot

# Create a temporary directory
tmpdir=$(mktemp -d)
cd $tmpdir
# Work with temporary files
rm -rf $tmpdir  # Clean up manually if needed before reboot

# Configure /tmp as tmpfs (RAM-based)
echo "tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0" | sudo tee -a /etc/fstab
```

## /dev

The `/dev` directory contains device files that represent hardware devices connected to the system. These device files are used by the system to interact with hardware devices such as hard drives, USB devices, and network interfaces.

**Use Cases:**

- Accessing raw storage devices
- Interacting with hardware interfaces
- Getting random numbers or null data
- Accessing terminal devices

**Tips:**

- Device files are created and managed by the udev system
- Block devices (b) represent storage devices, character devices (c) represent other devices
- Use /dev/null to discard unwanted output
- Use /dev/urandom or /dev/random for cryptographic purposes

**Examples:**

```bash
# List all block devices
lsblk

# Write an image to a USB drive
sudo dd if=ubuntu.iso of=/dev/sdb bs=4M status=progress

# Discard command output
command > /dev/null 2>&1

# Get random data
head -c 16 /dev/urandom | hexdump -C

# Access a USB serial device
sudo cat /dev/ttyUSB0
```

## /proc

The `/proc` directory is a virtual file system that provides information about running processes and system resources. It contains files and directories that represent system processes, memory, CPU information, and other system resources. This directory is dynamically generated by the kernel.

**Use Cases:**

- Monitoring system performance
- Inspecting running processes
- Adjusting kernel parameters at runtime
- Gathering system information for diagnostics

**Tips:**

- Files in /proc are not real files but interfaces to the kernel
- Changes to sysctl parameters can be made permanent in /etc/sysctl.conf
- Great for scripting and system monitoring
- Process-specific information is in numbered directories matching PIDs

**Examples:**

```bash
# View system memory information
cat /proc/meminfo

# Check CPU information
cat /proc/cpuinfo

# See mounted filesystems
cat /proc/mounts

# Tune kernel parameter temporarily
echo 1 | sudo tee /proc/sys/net/ipv4/ip_forward

# View process information
ls -la /proc/1/
cat /proc/1/cmdline

# Find out which process is using a port
sudo lsof -i :80
```

<details>
  <summary>Common files and directories in /proc</summary>

- `/proc/cpuinfo` - Contains information about the CPU.
- `/proc/meminfo` - Contains information about memory usage.
- `/proc/loadavg` - Contains system load average information.
- `/proc/uptime` - Contains system uptime information.
- `/proc/version` - Contains kernel version information.
- `/proc/sys` - Contains kernel parameters and settings.
- `/proc/net` - Contains network-related information.
- `/proc/fs` - Contains file system-related information.
- `/proc/self` - Contains information about the current process.
- `/proc/[pid]` - Contains information about a specific process.
- `/proc/sys/kernel` - Contains kernel-related settings.
- `/proc/sys/net` - Contains network-related settings.
- `/proc/sys/vm` - Contains virtual memory settings.
- `/proc/sys/fs` - Contains file system settings.
- `/proc/sys/dev` - Contains device-related settings.
- `/proc/sys/fs/inode-nr` - Contains inode number information.
- `/proc/sys/fs/file-nr` - Contains file number information.
- `/proc/sys/fs/file-max` - Contains maximum file limit information.
- `/proc/sys/fs/dentry-state` - Contains dentry state information.
- `/proc/sys/fs/inode-state` - Contains inode state information.
- `/proc/sys/fs/quota` - Contains quota settings.
- `/proc/sys/fs/xfs` - Contains XFS file system settings.
- `/proc/sys/fs/ext4` - Contains ext4 file system settings.
- `/proc/sys/fs/cifs` - Contains CIFS file system settings.
- `/proc/sys/fs/nfs` - Contains NFS file system settings.
- `/proc/sys/fs/nfsd` - Contains NFS server settings.
- `/proc/sys/fs/nfsd/nfsv4` - Contains NFSv4 server settings.

  Example: `/proc/cpuinfo`

  ```
  processor       : 0
  vendor_id       : GenuineIntel
  cpu family      : 6
  model           : 158
  model name      : Intel(R) Core(TM) i7-8700K CPU @ 3.70GHz
  stepping        : 10
  microcode       : 0xde
  cpu MHz         : 4700.144
  cache size      : 12288 KB
  physical id     : 0
  siblings        : 12
  core id         : 0
  cpu cores       : 6
  apicid          : 0
  initial apicid  : 0
  fpu             : yes
  fpu_exception   : yes
  cpuid level     : 22
  wp              : yes
  flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid dca sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm3 support_lockstep cpufreq
  bugs            :
  bogomips        : 7400.28
  clflush size    : 64
  cache_alignment : 64
  address sizes   : 39 bits physical, 48 bits virtual
  power management:
  ```

  </details>

## /sys

The `/sys` directory is a virtual file system that provides information about the Linux kernel and kernel modules. It contains files and directories that represent kernel parameters, hardware devices, and other kernel-related information.

**Use Cases:**

- Managing device parameters
- Configuring hardware features
- Monitoring hardware status
- Scripting hardware interactions

**Tips:**

- Like /proc, these are not real files but kernel interfaces
- Useful for hardware troubleshooting and automation
- Changes are typically not persistent across reboots
- Used extensively by udev for device management

**Examples:**

```bash
# Control LED brightness (on laptops)
echo 50 | sudo tee /sys/class/leds/input4::scrolllock/brightness

# Get information about block devices
ls /sys/block/

# Check battery status
cat /sys/class/power_supply/BAT0/capacity
cat /sys/class/power_supply/BAT0/status

# Control CPU frequency scaling
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo "performance" | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
```

## /boot

The `/boot` directory contains boot loader files and the Linux kernel. It is used by the system to boot into the Linux operating system.

**Use Cases:**

- Storing kernel images
- Keeping bootloader configuration (GRUB)
- Storing initial RAM disk (initrd/initramfs)
- Managing kernel modules

**Tips:**

- Keep multiple kernel versions for fallback options
- Backup this directory before kernel upgrades
- Consider having /boot on a separate partition
- Be cautious when cleaning old kernels to ensure at least one working kernel remains

**Examples:**

```bash
# List kernel images
ls -la /boot/vmlinuz*

# Check GRUB configuration
cat /boot/grub/grub.cfg

# View available disk space in /boot
df -h /boot

# Backup bootloader configuration
sudo cp /boot/grub/grub.cfg /boot/grub/grub.cfg.bak

# Update bootloader configuration
sudo update-grub
```

## /mnt

The `/mnt` directory is used as a mount point for temporary file systems. It is typically used to mount external storage devices such as USB drives and network shares.

**Use Cases:**

- Mounting external hard drives
- Accessing network file systems
- Temporarily mounting disk images
- Manual mounting of storage devices

**Tips:**

- Create subdirectories for different mount points
- Use descriptive names for mount points
- Can be used for temporary mounts, while /media is often used for automounted devices
- Manual mounts here don't persist across reboots unless added to /etc/fstab

**Examples:**

```bash
# Create a mount point
sudo mkdir -p /mnt/usb_drive

# Mount a USB drive
sudo mount /dev/sdb1 /mnt/usb_drive

# Mount an NFS share
sudo mount -t nfs server:/shared /mnt/nfs_share

# Mount an ISO image
sudo mount -o loop ubuntu.iso /mnt/iso

# Unmount when done
sudo umount /mnt/usb_drive
```

## /media

The `/media` directory is used as a mount point for removable media devices such as CD-ROMs and DVDs. When a removable media device is inserted, it is automatically mounted under the `/media` directory.

**Use Cases:**

- Auto-mounting USB drives
- Accessing CD/DVD content
- Working with removable storage
- Interacting with digital cameras and phones

**Tips:**

- Modern desktop environments automatically mount removable media here
- Device names are typically based on the volume label or device ID
- Safely eject media with commands or GUI tools before physically removing
- File managers typically provide easy access to mounted media

**Examples:**

```bash
# List mounted media devices
ls -la /media/$USER/

# Safely eject a USB drive
sudo eject /media/$USER/USB_DRIVE

# Copy files from a CD-ROM
cp -r /media/$USER/CDROM_LABEL/files ~/destination/

# Create an alias to a commonly used media directory
echo "alias myusb='cd /media/$USER/MY_USB_DRIVE'" >> ~/.bashrc
```

## /opt

The `/opt` directory is used to store optional software packages that are not part of the standard Linux distribution. It is typically used for third-party software installations.

**Use Cases:**

- Installing commercial software
- Deploying self-contained application packages
- Installing software that doesn't follow FHS standards
- Keeping isolated application environments

**Tips:**

- Each application typically gets its own subdirectory
- Good for software that doesn't integrate well with system package managers
- Applications here usually don't depend on other software outside their directory
- May need to add binary paths to your PATH environment variable

**Examples:**

```bash
# Install software to /opt
sudo tar -xzf software.tar.gz -C /opt/

# Add an /opt binary directory to your PATH
echo 'export PATH=$PATH:/opt/application/bin' >> ~/.bashrc
source ~/.bashrc

# Create a symbolic link to a binary
sudo ln -s /opt/application/bin/app /usr/local/bin/app

# List installed optional packages
ls -la /opt/
```

## /lib

The `/lib` directory contains shared libraries used by programs on the system. These libraries are essential for running programs and are loaded by the system when needed.

**Use Cases:**

- Providing shared code for applications
- Supporting essential system functions
- Loading kernel modules
- Running programs that depend on specific libraries

**Tips:**

- In modern systems, /lib may be a symlink to /usr/lib
- Adding custom libraries may require running ldconfig
- Be cautious when modifying this directory
- Libraries are typically managed by the package system

**Examples:**

```bash
# Find which shared libraries a program uses
ldd /usr/bin/firefox

# Update the shared library cache after adding libraries
sudo ldconfig

# Find which package a library belongs to
dpkg -S /lib/x86_64-linux-gnu/libc.so.6   # Debian/Ubuntu
rpm -qf /lib64/libc.so.6                  # CentOS/RHEL

# Check for broken library dependencies
sudo ldconfig -p | grep "not found"
```

## /lib64

The `/lib64` directory contains 64-bit shared libraries used by programs on the system. It is used on 64-bit systems to store 64-bit libraries.

**Use Cases:**

- Supporting 64-bit applications
- Providing architecture-specific libraries
- Running applications that require 64-bit libraries

**Tips:**

- Present only on 64-bit systems
- Often a symlink to /usr/lib64 in modern distributions
- Similar functionality to /lib but for 64-bit architecture
- Contains architecture-dependent libraries

**Examples:**

```bash
# Check if a library exists in lib64
ls -la /lib64/libc.so.6

# Find packages that installed files in lib64
find /lib64 -type f -name "*.so*" | xargs dpkg -S 2>/dev/null   # Debian/Ubuntu
find /lib64 -type f -name "*.so*" | xargs rpm -qf 2>/dev/null   # CentOS/RHEL

# Compare 32-bit and 64-bit libraries
ls -la /lib/libc.so.6 /lib64/libc.so.6 2>/dev/null

# Check which architecture a library is built for
file /lib64/libc.so.6
```

## /srv

The `/srv` directory is used to store data files for services provided by the system. It is typically used to store web server data, such as website files and configuration files.

**Use Cases:**

- Hosting website content
- Storing FTP server files
- Managing data for other network services
- Keeping service-specific data

**Tips:**

- Organize by service name (e.g., /srv/www, /srv/ftp)
- Good location for service data that's accessible to non-root users
- Consider placing on a separate partition for easier management
- Use proper permissions for security

**Examples:**

```bash
# Set up a website directory
sudo mkdir -p /srv/www/mywebsite
sudo chown -R www-data:www-data /srv/www/mywebsite

# Configure a web server to use /srv
sudo nano /etc/nginx/sites-available/mywebsite
# server {
#    listen 80;
#    root /srv/www/mywebsite;
#    ...
# }

# Set up an FTP directory
sudo mkdir -p /srv/ftp/public
sudo chmod 755 /srv/ftp/public

# Back up service data
sudo rsync -av /srv/www/ /backup/www/
```

## /run

The `/run` directory is used to store runtime data files for running processes. It is a temporary file system that is created at boot time and is used to store system information during the system's runtime.

**Use Cases:**

- Storing PID files for services
- Maintaining socket files for IPC
- Keeping temporary service state
- Managing lock files

**Tips:**

- Contents are stored in memory (tmpfs)
- Cleared on reboot
- A modern alternative to /var/run (which is often a symlink to /run now)
- Often used by system services to communicate

**Examples:**

```bash
# Check which services are running
ls -la /run/systemd/units/

# View lock files
ls -la /run/lock/

# Check socket files
ls -la /run/dbus/

# View PID files to see which processes are running
find /run -name "*.pid"

# See mounted filesystems related to /run
mount | grep '/run'
```

## /lost+found

The `/lost+found` directory is used to store recovered files and directories that were found during a file system check. If the file system check detects errors, it may recover lost files and store them in the `/lost+found` directory.

**Use Cases:**

- Recovering data after system crashes
- Retrieving files after filesystem corruption
- Finding data after improper shutdowns
- Restoring partially written files

**Tips:**

- Each filesystem has its own lost+found directory
- Files here may have generic names (numbers) without original filenames
- Use file command to identify file types
- Regular users cannot access this directory without sudo

**Examples:**

```bash
# Check if there are any recovered files
sudo ls -la /lost+found/

# Run filesystem check to find corrupted files
sudo fsck -f /dev/sda1

# Try to identify recovered files by content
sudo file /lost+found/*

# View text content of a recovered file
sudo cat /lost+found/#12345

# Try to restore original filenames when possible
sudo grep -r "unique string" /lost+found/
```
