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

## /home

The `/home` directory contains home directories for regular users. Each user on the system has a separate home directory located within `/home`. The home directory is the default location where users store their personal files and configurations.

## /bin

The `/bin` directory contains essential system binaries (executable files) that are required for the system to function properly. These binaries are available to all users and are used for common system operations.

## /sbin

The `/sbin` directory contains system binaries that are used for system administration tasks. These binaries are typically used by the root user for system maintenance and configuration.

## /usr

The `/usr` directory contains user-related system files and programs. It is divided into several subdirectories and is one of the largest directories in the file system, containing the majority of user utilities and applications.

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

## /dev

The `/dev` directory contains device files that represent hardware devices connected to the system. These device files are used by the system to interact with hardware devices such as hard drives, USB devices, and network interfaces.

## /proc

The `/proc` directory is a virtual file system that provides information about running processes and system resources. It contains files and directories that represent system processes, memory, CPU information, and other system resources. This directory is dynamically generated by the kernel.

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

## /boot

The `/boot` directory contains boot loader files and the Linux kernel. It is used by the system to boot into the Linux operating system.

## /mnt

The `/mnt` directory is used as a mount point for temporary file systems. It is typically used to mount external storage devices such as USB drives and network shares.

## /media

The `/media` directory is used as a mount point for removable media devices such as CD-ROMs and DVDs. When a removable media device is inserted, it is automatically mounted under the `/media` directory.

## /opt

The `/opt` directory is used to store optional software packages that are not part of the standard Linux distribution. It is typically used for third-party software installations.

## /lib

The `/lib` directory contains shared libraries used by programs on the system. These libraries are essential for running programs and are loaded by the system when needed.

## /lib64

The `/lib64` directory contains 64-bit shared libraries used by programs on the system. It is used on 64-bit systems to store 64-bit libraries.

## /srv

The `/srv` directory is used to store data files for services provided by the system. It is typically used to store web server data, such as website files and configuration files.

## /run

The `/run` directory is used to store runtime data files for running processes. It is a temporary file system that is created at boot time and is used to store system information during the system's runtime.

## /lost+found

The `/lost+found` directory is used to store recovered files and directories that were found during a file system check. If the file system check detects errors, it may recover lost files and store them in the `/lost+found` directory.
