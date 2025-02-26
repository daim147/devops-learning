# Linux

Linux is a family of open-source Unix-like operating systems based on the Linux kernel, first released on September 17, 1991, by Linus Torvalds. Linux is typically packaged in a Linux distribution.

## Table of Contents

- [Linux](#linux)
  - [Table of Contents](#table-of-contents)
  - [History](#history)
  - [Linux Architecture](#linux-architecture)
  - [Distributions](#distributions)
  - [Linux vs. Unix](#linux-vs-unix)
  - [Debian vs. Fedora](#debian-vs-fedora)
  - [Flavor vs. Distribution](#flavor-vs-distribution)
  - [Package Managers: Debian, Fedora, and RPM](#package-managers-debian-fedora-and-rpm)
  - [Package Manager vs. Package Repository Manager](#package-manager-vs-package-repository-manager)
  - [File System Hierarchy More Here](#file-system-hierarchy-more-here)
  - [Types of Files in Linux](#types-of-files-in-linux)
  - [File Permissions](#file-permissions)
    - [Permission Types](#permission-types)
    - [Permission Categories](#permission-categories)
    - [Changing Permissions](#changing-permissions)
    - [Special Permissions](#special-permissions)
  - [Basic Linux Commands More Here](#basic-linux-commands-more-here)
    - [File and Directory Operations](#file-and-directory-operations)
    - [Text Processing](#text-processing)
    - [System Information](#system-information)
  - [Process Management](#process-management)
    - [Process Monitoring](#process-monitoring)
    - [Process Control](#process-control)
    - [Job Control](#job-control)
  - [User Management](#user-management)
    - [User Commands](#user-commands)
    - [Group Commands](#group-commands)
    - [User Information](#user-information)
  - [Shell Scripting](#shell-scripting)
    - [Key Components](#key-components)
    - [Example Simple Script](#example-simple-script)
  - [Networking in Linux](#networking-in-linux)
    - [Network Configuration](#network-configuration)
    - [Remote Access](#remote-access)
  - [Security Features](#security-features)
    - [Access Control](#access-control)
    - [Encryption](#encryption)
    - [Auditing](#auditing)

## History

Linux was originally developed for personal computers based on the Intel x86 architecture but has since been ported to more platforms than any other operating system. It is the leading operating system on servers and other big iron systems such as mainframe computers and the only OS used on TOP500 supercomputers.

## Linux Architecture

The Linux operating system consists of several important components:

1. **Kernel**: The core of the operating system that manages hardware resources and provides essential services.
2. **System Libraries**: Special programs that applications use to access kernel features.
3. **System Utilities**: Programs responsible for specialized, individual management tasks.
4. **Shell**: The command-line interface that interprets user commands.
5. **Display Server**: System that displays the graphical interface.
6. **Window Manager**: Controls the placement and appearance of windows.
7. **Desktop Environment**: The complete graphical user interface.

## Distributions

Linux is packaged in a form known as a **Linux distribution** (or _distro_ for short) for both desktop and server use. Some popular mainstream Linux distributions include:

- Debian (and its derivatives such as Ubuntu)
- Fedora
- openSUSE
- Arch Linux
- CentOS/RHEL
- Linux Mint
- Manjaro
- Elementary OS

Linux distributions include the Linux kernel, supporting utilities and libraries, and usually a large amount of application software to fulfill the distribution's intended use.

## Linux vs. Unix

Linux is a Unix-like operating system. Other Unix-like operating systems exist, such as Solaris and BSD. Linux is a Unix-like operating system but was developed without any Unix code, unlike BSD and its variants.

Key differences:

- Unix is older (developed in the 1970s) while Linux was created in 1991
- Unix was originally proprietary while Linux has always been open source
- Unix has stricter certification standards while Linux is more flexible
- Unix typically runs on specific hardware while Linux runs on virtually anything

## Debian vs. Fedora

Debian and Fedora are two of the most popular Linux distributions:

- **Debian:**

  - Known for its stability and used as a base for many other distributions
  - Uses the APT package manager
  - Conservative release cycle focused on stability
  - Very large software repository
  - Community-driven development

- **Fedora:**
  - Known for its bleeding-edge software and is the basis for Red Hat Enterprise Linux
  - Uses DNF (formerly YUM) package manager
  - Faster release cycle with frequent updates
  - Often serves as a testing ground for features that may later appear in RHEL
  - Backed by Red Hat

## Flavor vs. Distribution

A Linux distribution is a flavor of Linux, but a flavor of Linux is not necessarily a distribution. A flavor of Linux is a particular distribution of Linux that has been customized for a particular purpose or set of users.

## Package Managers: Debian, Fedora, and RPM

Debian uses the **Advanced Packaging Tool (APT)** to manage packages. Fedora uses the **Yellowdog Updater, Modified (YUM)** and **RPM Package Manager (RPM)**. RPM is also used in Red Hat Enterprise Linux and CentOS.

The main difference between APT and YUM is that APT is a single package manager, while YUM is both a package manager and a package repository manager.

Other package managers include:

- **Pacman**: Used by Arch Linux and derivatives
- **DNF**: The next-generation version of YUM
- **Snap**: Universal package manager developed by Canonical
- **Flatpak**: Another universal package management system

## Package Manager vs. Package Repository Manager

- **Package Manager:** A tool that automates the process of installing, upgrading, configuring, and removing software packages.
- **Package Repository Manager:** A tool that manages software packages in a repository, which is a collection of software packages.

  _Example:_ Npm is a package manager, and the Npm registry is a package repository manager.

## File System Hierarchy [More Here](./LinuxFolderStructure.md)

Linux follows the Filesystem Hierarchy Standard (FHS) with directories serving specific purposes:

- **/bin**: Essential user command binaries
- **/boot**: Boot loader files, kernel, and initrd
- **/dev**: Device files
- **/etc**: System configuration files
- **/home**: User home directories
- **/lib**: Essential shared libraries
- **/media**: Mount points for removable media
- **/mnt**: Mount point for temporary filesystems
- **/opt**: Add-on application software packages
- **/proc**: Virtual filesystem for process and kernel information
- **/root**: Home directory for the root user
- **/run**: Run-time variable data
- **/sbin**: System binaries
- **/srv**: Data for services provided by the system
- **/sys**: Virtual filesystem for system information
- **/tmp**: Temporary files
- **/usr**: Secondary hierarchy for user data
- **/var**: Variable files (logs, spool files, caches)

## Types of Files in Linux

In Linux, files can be classified into different types based on their contents and usage. The `file` command can be used to determine the type of a file.

- **Regular files:** Normal files that contain data (e.g., text files, images, executables). Represented by `-` in file permissions.
- **Directories:** Files that contain other files and directories. Represented by `d` in file permissions.
- **Symbolic links:** Files that point to another file or directory. Represented by `l` in file permissions.
- **Device files:** Files that represent hardware devices (e.g., hard drives, printers). Represented by `b` (block devices) and `c` (character devices) in file permissions.
- **Named pipes:** Files that allow inter-process communication. Represented by `p` in file permissions.
- **Sockets:** Files that allow communication between processes on the same or different systems. Represented by `s` in file permissions.
- **Special files:** Files that represent special devices or filesystems. Represented by `s` in file permissions.
- **Executable files:** Files that contain executable code (e.g., scripts, binaries). Represented by `x` in file permissions.
- **Hidden files:** Files hidden from normal directory listings. Start with a `.` at the beginning of the filename.
- **Configuration files:** Files that contain configuration settings for applications and the system. Typically have a `.conf` or `.cfg` extension.
- **Log files:** Files that contain log messages generated by the system and applications. Typically have a `.log` extension.
- **Temporary files:** Files used to store temporary data. Typically have a `.tmp` or `.temp` extension.
- **Archive files:** Files that contain compressed data. Typically have a `.tar`, `.zip`, or `.gz` extension.
- **Image files:** Files that contain images. Typically have a `.jpg`, `.png`, or `.gif` extension.
- **Audio files:** Files that contain audio data. Typically have a `.mp3`, `.wav`, or `.flac` extension.
- **Video files:** Files that contain video data. Typically have a `.mp4`, `.avi`, or `.mkv` extension.
- **Document files:** Files that contain text or document data. Typically have a `.txt`, `.docx`, or `.pdf` extension.
- **Binary files:** Files that contain binary data. Typically have a `.bin`, `.exe`, or `.dll` extension.
- **Source code files:** Files that contain source code for programs. Typically have a `.c`, `.java`, or `.py` extension.
- **Library files:** Files that contain shared libraries used by programs. Typically have a `.so` or `.dll` extension.
- **System files:** Files that are part of the operating system. Typically have a `.sys`, `.dll`, or `.cfg` extension.
- **User files:** Files created and managed by users. Can have extensions like `.txt`, `.docx`, or `.jpg`.

## File Permissions

Linux implements a permission model to control access to files and directories:

### Permission Types

- **Read (r)**: Permission to read a file or list directory contents
- **Write (w)**: Permission to modify a file or create/delete files in a directory
- **Execute (x)**: Permission to execute a file or access a directory

### Permission Categories

- **User (u)**: The file owner
- **Group (g)**: Users who are members of the file's group
- **Others (o)**: All other users

### Changing Permissions

- **chmod**: Changes the permissions of files or directories
  - Symbolic mode: `chmod u+x file.sh`
  - Numeric mode: `chmod 755 file.sh`

### Special Permissions

- **SUID (Set User ID)**: When set on an executable file, it runs with the permissions of the file owner
- **SGID (Set Group ID)**: When set on an executable file, it runs with the permissions of the file group
- **Sticky Bit**: When set on a directory, only the file owner can delete or rename files

## Basic Linux Commands [More Here](./LinuxCommands.md)

### File and Directory Operations

- **ls**: List directory contents
- **cd**: Change directory
- **pwd**: Print working directory
- **mkdir**: Create a directory
- **rmdir**: Remove empty directory
- **cp**: Copy files or directories
- **mv**: Move or rename files or directories
- **rm**: Remove files or directories
- **touch**: Create empty files or update timestamps

### Text Processing

- **cat**: Concatenate and display files
- **less/more**: Display file content one screen at a time
- **head/tail**: Display the beginning/end of a file
- **grep**: Search for patterns in files
- **sed**: Stream editor for filtering and transforming text
- **awk**: Pattern scanning and processing language

### System Information

- **uname**: Print system information
- **who/w**: Show who is logged on
- **uptime**: Show how long the system has been running
- **df**: Report file system disk space usage
- **du**: Estimate file space usage
- **free**: Display amount of free and used memory

## Process Management

### Process Monitoring

- **ps**: Report process status
- **top/htop**: Dynamic real-time view of processes
- **pgrep**: Look up processes based on name and other attributes

### Process Control

- **kill**: Send a signal to a process
- **pkill**: Signal processes based on name and other attributes
- **killall**: Kill processes by name
- **nice/renice**: Run a program with modified scheduling priority

### Job Control

- **bg**: Place jobs in the background
- **fg**: Bring jobs to the foreground
- **jobs**: List active jobs
- **nohup**: Run a command immune to hangups

## User Management

### User Commands

- **useradd**: Create a new user
- **usermod**: Modify a user account
- **userdel**: Delete a user account
- **passwd**: Change user password
- **su**: Substitute user identity
- **sudo**: Execute a command as another user

### Group Commands

- **groupadd**: Create a new group
- **groupmod**: Modify a group
- **groupdel**: Delete a group

### User Information

- **id**: Print user and group IDs
- **whoami**: Print effective userid
- **groups**: Print groups a user is in
- **finger**: User information lookup program

## Shell Scripting

Shell scripting allows automation of tasks in Linux:

### Key Components

- **Shebang**: `#!/bin/bash` - Tells the system which interpreter to use
- **Variables**: `name="John"` - Store and manipulate data
- **Control structures**: if-else, for loops, while loops, case statements
- **Functions**: Reusable code blocks
- **Input/output redirection**: `>`, `>>`, `<`, pipes

### Example Simple Script

```bash
#!/bin/bash
# This is a comment
echo "Hello, World!"
for i in {1..5}; do
  echo "Count: $i"
done
```

## Networking in Linux

### Network Configuration

- **ifconfig/ip**: Configure network interfaces
- **ping**: Test network connectivity
- **traceroute**: Print the route packets trace to a network host
- **netstat/ss**: Network statistics
- **dig/nslookup**: DNS lookup utility

### Remote Access

- **ssh**: Secure shell remote login
- **scp**: Secure copy (remote file copy)
- **rsync**: Remote file synchronization
- **wget/curl**: Non-interactive network downloader

## Security Features

### Access Control

- **SELinux**: Security-Enhanced Linux provides mandatory access controls
- **AppArmor**: Application security system that restricts programs' capabilities
- **iptables/nftables**: Firewall utilities
- **fail2ban**: Ban IPs that show malicious signs

### Encryption

- **OpenSSL**: Toolkit for the Transport Layer Security (TLS) protocols
- **GnuPG**: Complete and free implementation of the OpenPGP standard
- **LUKS**: Linux Unified Key Setup for disk encryption

### Auditing

- **auditd**: System call auditing
- **logrotate**: Rotate, compress, and mail system logs
- **journalctl**: Query the systemd journal
