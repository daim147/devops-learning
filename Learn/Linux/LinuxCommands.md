# Linux Commands

`man` displays the manual page for a **command**. It can be used to view information about a command, including its syntax, options, and usage examples.

`--help` displays help information for a command. It can be used to view a brief description of a command, its options, and how to use it.

`pwd` displays the current working directory. It can be used to view the full path of the current directory and navigate to other directories. Use `-L` to follow symbolic links and `-P` to use the physical directory structure without following symbolic links.

`mkdir` creates a new directory. It can be used to create directories in the current directory or specify a path to create directories in a specific location. Use the `-p` flag to create parent directories if they do not exist.

`cd` changes the current working directory. It can be used to navigate to different directories on the system. Use `cd -` to switch to the previous directory, and `cd ~` to go to the home directory.

`ls` lists the contents of a directory. It can be used to view files and directories in the current directory, as well as their permissions, ownership, and size. `-l` flag displays detailed information about files and directories, `-a` flag displays hidden files and directories, `-h` flag displays file sizes in a human-readable format. `-t` flag sorts files and directories by modification time. `-r` flag reverses the order of the sorting.

`touch` creates a new empty file. It can be used to create files in the current directory or specify a path to create files in a specific location.

`cp` copies files and directories. It can be used to make copies of files and with `-r` flag directories in the current directory or specify a source and destination path.

`mv` moves or renames files and directories. It can be used to move files and directories to a different location or rename them.

`rm` removes files and directories. It can be used to delete files and directories in the current directory or specify a path to delete files and directories in a specific location. `-r` flag is used to delete directories. `-rf` is used to force delete files and directories.

`echo` displays text on the terminal. It can be used to print messages, variables, and command output. Use `-e` to enable interpretation of backslash escapes, `-n` to suppress the trailing newline, and `-E` to disable interpretation of backslash escapes.

`date` displays the current date and time. It can be used to view the system date and time, format the output, and perform date and time calculations. Use `+%format` to specify the output format. `-d` flag is used to display a specific date and time. `-u` flag is used to display the date and time in UTC.

`cal` displays a calendar for a specific month or year. It can be used to view the calendar for the current month, a specific month, or a specific year. Use `-3` to display the previous, current, and next month. `-y` to display the calendar for the current year.

`cat` displays the contents of a file. It can be used to view the contents of text files, concatenate multiple files, and create new files. Use `cat file1 file2 > file3` to concatenate files.

`less` displays the contents of a file one page at a time. It can be used to view the contents of text files and navigate through them using keyboard shortcuts. Use `-N` to show line numbers.

`more` displays the contents of a file one page at a time. It can be used to view the contents of text files and navigate through them using keyboard shortcuts. in percentage.

`head` displays the first few or 10 lines of a file. It can be used to view the beginning of text files and specify the number of lines to display. Use `-n` to specify the number of lines (e.g., `head -n 10 file`).

`tail` displays the last few or 10 lines of a file. It can be used to view the end of text files and specify the number of lines to display. Use `-n` to specify the number of lines (e.g., `tail -n 10 file`). `-f` flag is used to follow the output of a file in real-time.

`hostname` displays the hostname of the system. It can be used to view the system's hostname and change it if needed.

`who` displays information about users who are currently logged in. It can be used to view the usernames, terminal names, login times, and IP addresses of users who are logged in.

`whoami` displays the username of the current user. It can be used to view the username of the current user and determine the permissions and privileges associated with that user.

    difference between hostname and whoami is that hostname displays the system's hostname, while whoami displays the username of the current user.

    system hostname is the name that identifies a system on a network. It is used to uniquely identify the system and allow other systems to communicate with it. The hostname is typically set during the system installation process and can be changed later if needed.

    vagrant@localhost is the default hostname for a Vagrant virtual machine. It consists of the username "vagrant" and the hostname "localhost" The hostname "localhost" is used to refer to the local system, while the username "vagrant" is the default username for a Vagrant virtual machine.s

`ping` sends ICMP echo requests to a target host and waits for a response. It can be used to test network connectivity between two hosts and diagnose network-related issues.

`file` determines the type of a file. It can be used to identify the file type, such as text, binary, or executable, and provide information about the file's contents and usage.

`ln` creates links between files. It can be used to create hard links and symbolic links to files and directories. `-s` flag is used to create symbolic links.

`unlink` removes links between files. It can be used to delete hard links and symbolic links to files and directories.

    Hard Link vs Symbolic Link

     Hard links are direct pointers to the file's inode on disk. They share the same inode number and data blocks as the original file. If the original file is deleted, the hard link still points to the data blocks, and the file's contents are preserved.

     Symbolic links are indirect pointers to the file's path on disk. They contain the path to the original file and are treated as separate files. If the original file is deleted, the symbolic link becomes a dangling link and points to a non-existent file.

`history` displays the command history list. Use `-c` to clear the history, `-w [filename]` to write history to a file, `-r [filename]` to read history from a file, `-a [filename]` to append history to a file, and `-d [offset]` to delete a specific entry. Use `!number` to repeat a specific command.

`find` searches for files and directories. It can be used to search for files and directories based on various criteria, such as name, size, type, and permissions. Use `-name` to search by name, `-size` to search by size, `-type` to search by type, and `-perm` to search by permissions. Example: `find /path/to/directory -name "pattern"`.

`locate` quickly searches for files and directories on the system. It can be used to find files and directories based on a keyword or pattern. Use `updatedb` to update the database used by `locate`. First install this package

`cut` extracts sections from each line of a file. It can be used to cut out specific columns or fields from a file, such as the first, second, or nth field. Use `-d` to specify the delimiter and `-f` to specify the field. Example: `cut -d: -f1,3 file.txt`.`-d:` specifies the colon as the delimiter, and `-f1,3` specifies the first and third fields.

`awk` is a powerful programming language for text processing. It can be used to manipulate and analyze text files, extract data, and generate reports. Example: `awk '{print $1, $3}' file.txt` prints the first and third fields of each line in the file. `-F` can be used to specify the field. Example: `awk -F: '{print $1, $3}' file.txt`. `-F:` specifies the colon as the field separator. `-f` can be used to specify a script file. Example: `awk -f script.awk file.txt`. `-v` can be used to pass variables to the script. Example: `awk -v var=value '{print $1, $3, var}' file.txt`. `-i` can be used to edit files in place. Example: `awk -i inplace '{print $1, $3}' file.txt`.

`sed` is a stream editor for filtering and transforming text. It can be used to perform text transformations, deletions, substitutions, and more. Example: `sed 's/pattern/replacement/g' file.txt` replaces all occurrences of "pattern" with "replacement" in the file. `-i` can be used to edit files in place. Example: `sed -i 's/pattern/replacement/g' file.txt`. `-e` can be used to specify multiple commands. Example: `sed -e 's/pattern1/replacement1/g' -e 's/pattern2/replacement2/g' file.txt`. `-f` can be used to specify a script file. Example: `sed -f script.sed file.txt`.

`wc` counts lines, words, and characters in a file or standard input. It can be used to count the number of lines, words, and characters in a file or the output of a command. Use `-l` to count lines, `-w` to count words, and `-c` to count characters. Example: `wc -l file.txt`.

`grep` is a powerful command-line utility used for searching plain-text data for lines that match a regular expression. It stands for "Global Regular Expression Print".

<details>
<summary>Commonly used options:</summary>

- i: Ignore case distinctions in both the pattern and the input files.
  Example: grep -i "pattern" file.txt

- v: Invert the match, displaying lines that do not match the pattern.
  Example: grep -v "pattern" file.txt

- r or -R: Recursively search directories.
  Example: grep -r "pattern" /path/to/directory

- l: Print only the names of files with matching lines.
  Example: grep -l "pattern" \*.txt

- L: Print only the names of files with no matching lines.
  Example: grep -L "pattern" \*.txt

- n: Prefix each matching line with its line number.
  Example: grep -n "pattern" file.txt

- c: Print only a count of matching lines per file.
  Example: grep -c "pattern" file.txt

- A [num]: Print [num] lines of trailing context after matching lines.
  Example: grep -A 3 "pattern" file.txt

- B [num]: Print [num] lines of leading context before matching lines.
  Example: grep -B 3 "pattern" file.txt

- C [num]: Print [num] lines of context both before and after matching lines.
  Example: grep -C 3 "pattern" file.txt

- e: Allow specifying multiple patterns.
  Example: grep -e "pattern1" -e "pattern2" file.txt

- f: Obtain patterns from a file, one per line.
  Example: grep -f patterns.txt file.txt

- w: Match only whole words.
  Example: grep -w "pattern" file.txt

- x: Match only whole lines.
  Example: grep -x "pattern" file.txt

- o: Print only the matched parts of a matching line.
  Example: grep -o "pattern" file.txt

- q: Quiet mode, exit immediately with zero status if any match is found.
  Example: grep -q "pattern" file.txt

- s: Suppress error messages about nonexistent or unreadable files.
  Example: grep -s "pattern" file.txt

- H: Always print the filename with output lines.
  Example: grep -H "pattern" file.txt

- h: Never print filenames with output lines.
  Example: grep -h "pattern" file.txt

- --color: Highlight the matching text.
  Example: grep --color "pattern" file.txt

- --exclude: Exclude files that match the specified pattern.
  Example: grep --exclude="\*.txt" "pattern" /path/to/directory

- --include: Search only files that match the specified pattern.
  Example: grep --include="\*.txt" "pattern" /path/to/directory

- --exclude-dir: Exclude directories that match the specified pattern.
  Example: grep --exclude-dir="dir\*" "pattern" /path/to/directory

- --include-dir: Search only directories that match the specified pattern.
  Example: grep --include-dir="dir\*" "pattern" /path/to/directory

  </details>

## Input Output Redirection

`>` redirects standard output to a file. It can be used to write the output of a command to a file, create a new file, or overwrite an existing file. Example: `command > file.txt`.

`>>` appends standard output to a file. It can be used to append the output of a command to a file or create a new file if it does not exist. Example: `command >> file.txt`.

`<` redirects standard input from a file. It can be used to read input from a file instead of the keyboard. Example: `command < file.txt`.

`|` redirects standard output from one command to standard input of another command. It can be used to chain multiple commands together and create pipelines. Example: `command1 | command2`.

`xargs` reads input from standard input and executes a command with the input as arguments. It can be used to build and execute commands from standard input, such as the output of another command. Use `command | xargs` to pass the output of a command as arguments to another command. Example: `ls | xargs rm`.

    difference between xargs and | is that xargs reads input from standard input and executes a command with the input as arguments, while | (pipe) passes the output of one command as input to another command. example: `ls | xargs rm` and `ls | rm`. `ls | xargs rm` will remove all files in the current directory, while `ls | rm` will not work because rm does not accept input from standard input.

`2>` redirects standard error to a file. It can be used to write error messages to a file instead of the terminal. Example: `command 2> error.txt`.

`2>>` appends standard error to a file. It can be used to append error messages to a file or create a new file if it does not exist. Example: `command 2>> error.txt`.

`&>` redirects both standard output and standard error to a file. It can be used to write both output and error messages to a file. Example: `command &> output.txt`.

`&>>` appends both standard output and standard error to a file. It can be used to append both output and error messages to a file or create a new file if it does not exist. Example: `command &>> output.txt`.

## User Management

Some important Points:

- There are three types of users on a Unix-like operating system: root user, regular users, and service users.
- The `/etc/passwd` file contains information about user accounts on the system, such as usernames, user IDs (UIDs), group IDs (GIDs), home directories, and login shells.
- Every user account on the system has a unique user ID (UID) and a unique group ID (GID).
- The `/etc/shadow` file contains encrypted passwords for user accounts on the system.
- The `/etc/group` file contains information about groups on the system, such as group names and group IDs.
- Each user has his or her own home directory, which is the default directory where the user is placed after logging in.

### Types of Users

| TYPE    | EXAMPLE          | ID (UID)      | GROUP ID (GID) | HOME DIR       | SHELL         |
| ------- | ---------------- | ------------- | -------------- | -------------- | ------------- |
| ROOT    | root             | 0             | 0              | /root          | /bin/bash     |
| REGULAR | husnain, vagrant | 1000 to 60000 | 1000 to 60000  | /home/username | /bin/bash     |
| SERVICE | ftp, ssh, apache | 1 to 999      | 1 to 999       | /var/ftp etc   | /sbin/nologin |

### Example of sample user from /etc/passwd file

`vagrant:x:1000:1000:hi:/home/vagrant:/bin/bash`

| Field          | Description                    | Sample Value  |
| -------------- | ------------------------------ | ------------- |
| Username       | Login name                     | vagrant       |
| Password       | Encrypted password placeholder | x             |
| User ID (UID)  | User identifier                | 1000          |
| Group ID (GID) | Primary group identifier       | 1000          |
| Comment        | User information (often empty) | hi            |
| Home Directory | User's home directory          | /home/vagrant |
| Shell          | User's default login shell     | /bin/bash     |

### Example of sample group from /etc/group file

`vagrant:x:1000:vagrantTest`

| Field          | Description                    | Sample Value |
| -------------- | ------------------------------ | ------------ |
| Group Name     | Group name                     | vagrant      |
| Password       | Encrypted password placeholder | x            |
| Group ID (GID) | Group identifier               | 1000         |
| Group Members  | Users who are members of group | vagrantTest  |

`id` displays information about a user or group. It can be used to view the user ID (UID), group ID (GID), and group membership of a user. Use `-u` to display the user ID, `-g` to display the group ID, and `-G` to display the group membership. Example: `id username`.

`useradd` adds a new user to the system. It can be used to create a new user account with a specified username, user ID (UID), group ID (GID), home directory, and login shell. Use `-u` to specify the user ID, `-g` to specify the group ID, `-d` to specify the home directory, and `-s` to specify the login shell. Example: `useradd -u 1001 -g 1001 -d /home/test -s /bin/bash test`, `useradd test`.

For Ubuntu and Debian based systems
`adduser` adds a new user to the system. It can be used to create a new user account with a specified username, user ID (UID), group ID (GID), home directory, and login shell. Use `--uid` to specify the user ID, `--gid` to specify the group ID, `--home` to specify the home directory, and `--shell` to specify the login shell. Example: `adduser --uid 1001 --gid 1001 --home /home/test --shell /bin/bash test`, `adduser test`.

`groupadd` adds a new group to the system. It can be used to create a new group with a specified group name and group ID (GID). Use `-g` to specify the group ID. Example: `groupadd -g 1001 testgroup`, `groupadd testgroup`.

`usermod` modifies user account settings or edit `/etc/passwd` or `/etc/group` manually . It can be used to change user account attributes, such as the username, user ID (UID), group ID (GID), home directory, and login shell. Use `-u` to change the user ID, `-g` to change the group ID, `-d` to change the home directory, and `-s` to change the login shell.Use `-l` to change the username.Use `-aG` to add a user to a secondary group. Use `-a` to append the user to the group.
Example: `usermod -u 1002 -g 1002 -d /home/test2 -s /bin/bash test`, `usermod -l newname oldname`, `usermod -aG groupname username` this command adds a user to a secondary group.

`passwd` changes a user's password. It can be used to change the password for a user account. Use `passwd username` to change the password for a specific user. Use `passwd` to change the password for the current user.

`userdel` deletes a user account. It can be used to remove a user account from the system. Use `-r` to remove the user's home directory and mail spool. Example: `userdel -r test`, `userdel test`.

`groupdel` deletes a group. It can be used to remove a group from the system. Example: `groupdel testgroup`.

`su - username` switches to another user account. It can be used to switch to another user account and run commands as that user. Use `-` to start a new login shell as the specified user. Example: `su - test`. root user can switch to any user without password.

`last` displays the last login information for users. It can be used to view the login history of users, including the date, time, and duration of their last login. Use `-n` to specify the number of entries to display. Example: `last -n 5`.

`lsof` lists open files and processes. It can be used to view information about open files, network connections, and processes that are using them. Use `-i` to display network connections, `-u` to display processes for a specific user, and `-t` to display only process IDs (PIDs). Example: `lsof -i`, `lsof -u username`, `lsof -t`. First install this package.

### File Permissions

| Character | Permission | Description                                                                                                                          |
| --------- | ---------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| `r`       | Read       | Permission to read the contents of the file or directory.                                                                            |
| `w`       | Write      | Permission to modify the contents of the file or directory.                                                                          |
| `x`       | Execute    | Permission to execute the file as a program or script. For directories, it allows entering the directory and accessing its contents. |

### Example of File Permissions

File permissions are typically displayed in a string of 10 characters, such as `-rwxr-xr--`. Here's a breakdown of what each character represents:

| Position | Character | Description                                                                            |
| -------- | --------- | -------------------------------------------------------------------------------------- |
| 1        | `-`       | File type (`-` for a regular file, `d` for a directory, `l` for a symbolic link, etc.) |
| 2-4      | `rwx`     | Owner's permissions (read, write, execute)                                             |
| 5-7      | `r-x`     | Group's permissions (read, execute)                                                    |
| 8-10     | `r--`     | Others' permissions (read)                                                             |

### Example Breakdown

For the permissions string `-rwxr-xr--`:

| Field     | Description                          | Value |
| --------- | ------------------------------------ | ----- |
| File Type | Regular file                         | `-`   |
| Owner     | Read, write, and execute permissions | `rwx` |
| Group     | Read and execute permissions         | `r-x` |
| Others    | Read permission only                 | `r--` |

To view the permissions of files and directories, you can use the `ls -l` command in the terminal.

`chown` changes the owner and group of files and directories. It can be used to change the owner and group of a file or directory to a specific user and group. Use `chown username:groupname file` to change the owner and group. Use `-R` to change ownership recursively for directories. Example: `chown username:groupname file`, `chown -R username:groupname directory`. if you want to change only owner then use `chown username file`. if you want to change only group then use `chown :groupname file`.

`chmod` changes the permissions of files and directories. It can be used to change the permissions of a file or directory to allow or restrict read, write, and execute access for the owner, group, and others. Use `chmod u=rwx,g=rx,o=r file` to set permissions. Use `-R` to change permissions recursively for directories. Example: `chmod u=rwx,g=rx,o=r file`, `chmod -R u=rwx,g=rx,o=r directory`. or you can use numeric values like `chmod 777 file` or `chmod 755 file`. 777 means read, write and execute for owner, group and others. 755 means read, write and execute for owner and read and execute for group and others. `4` for read, `2` for write and `1` for execute.

### Sudo

`sudo` allows users to run commands with elevated privileges. It can be used to perform administrative tasks that require root access, such as installing software, configuring system settings, and managing files and directories. Use `sudo command` to run a command with root privileges. Use `sudo -i` to start a new shell session as the root user. Use `sudo -u username command` to run a command as a specific user. Use `sudo -l` to list available commands for the current user. Use `sudo -v` to refresh the sudo timestamp. Use `sudo -k` to invalidate the sudo timestamp.

    The difference between sudo -i and sudo su is that sudo -i starts a new shell session as the root user, while sudo su switches to the root user in the current shell session.

    The sudoers file `(/etc/sudoers)` contains rules and configurations for the sudo command. It defines which users and groups are allowed to run commands with elevated privileges and what commands they can run.

    The sudo group is a special group that allows users to run commands with elevated privileges using the sudo command. Users who are members of the sudo group can run commands as the root user.

    The sudo command logs all sudo usage to the system log file (/var/log/auth.log or /var/log/secure). It records the user, command, timestamp, and outcome of each sudo invocation.

`visduo` edits the sudoers file. It can be used to edit the sudoers file and configure rules for the sudo command. Use `visudo` to open the sudoers file in the default text editor. Use `visudo -c` to check the syntax of the sudoers file for errors. or to add a user to sudoers file use `sudo usermod -aG sudo username`. or can edit and add user to sudoers file by `sudo visudo` and add `username ALL=(ALL:ALL) ALL`.

For Ubuntu and Debian based systems.
`export Editor=vim` to set the default editor to vim. because by default it is nano.

`/etc/sudoers` file contains rules and configurations for the sudo command. It defines which users and groups are allowed to run commands with elevated privileges and what commands they can run. The sudoers file should be edited using the `visudo` command to prevent syntax errors and ensure proper configuration.

`/etc/sudoers.d` directory contains additional configuration files for the sudo command. It can be used to add custom rules and configurations for specific `users` or `groups`. Files in this directory should follow the same syntax as the main sudoers file. add a file in this directory with `sudo visudo -f /etc/sudoers.d/filename` and add `username ALL=(ALL:ALL) ALL` in this file, for group `%groupname ALL=(ALL:ALL) ALL`.

### Package Management

`curl` is a command-line tool for transferring data with URLs. It can be used to download files, upload files, and perform various network-related tasks. Use `curl URL` to download a file from a URL. Use `-O` to save the file with the original name. Use `-o filename` to save the file with a specific name. Use `-L` to follow redirects. Use `-I` to display the HTTP headers. Use `-X` to specify the HTTP method. Use `-d` to send data in a POST request. Use `-H` to add custom headers. Use `-u` to specify authentication credentials. Use `-v` to enable verbose mode. Verbose mode displays detailed information about the request and response.

`wget` is a command-line tool for downloading files from the web. It can be used to download files, recursively download files from a website, and perform various network-related tasks. Use `wget URL` to download a file from a URL. Use `-O filename` to save the file with a specific name. Use `-r` to recursively download files. Use `-np` to exclude parent directories. Use `-nc` to skip existing files. Use `-c` to resume interrupted downloads. Use `-q` to enable quiet mode.s

#### RPM Based Systems (Red Hat, CentOS, Fedora)

`rpm` is the package manager for RPM-based Linux distributions. It can be used to install, upgrade, query, and remove software packages in the RPM format. Use `rpm -i package.rpm` to install a package, `rpm -U package.rpm` to upgrade a package, `rpm -q package` to query a package, and `rpm -e package` to remove a package. to list all installed packages use `rpm -qa`. to list files in a package use `rpm -ql package`. to verify a package use `rpm -V package`. to install a package with dependencies use `rpm -ivh package.rpm`. to install a package without dependencies use `rpm -ivh --nodeps package.rpm`. to install a package and ignore conflicts use `rpm -ivh --force package.rpm`. `-v` is used for verbose output, `-h` is used for hash marks.Hash marks are printed as the package archive is unpacked.

`yum` is a high-level package manager for RPM-based Linux distributions. It can be used to install, upgrade, query, and remove software packages and dependencies. Use `yum install package` to install a package, `yum update package` to upgrade a package, `yum list package` to query a package, and `yum remove package` to remove a package. to list all installed packages use `yum list installed`. to search for a package use `yum search package`. to install a package with dependencies use `yum install package`. to update all packages use `yum update`. to remove a package and its dependencies use `yum remove package`. to clean the package cache use `yum clean all`.

`dnf` is a package manager for RPM-based Linux distributions. It can be used to install, upgrade, query, and remove software packages and dependencies. Use `dnf install package` to install a package, `dnf upgrade package` to upgrade a package, `dnf list package` to query a package, and `dnf remove package` to remove a package. to list all installed packages use `dnf list installed`. to search for a package use `dnf search package`. to install a package with dependencies use `dnf install package`. to update all packages use `dnf upgrade`. to remove a package and its dependencies use `dnf remove package`. to clean the package cache use `dnf clean all`. repository configuration files are stored in the `/etc/yum.repos.d` directory. to enable a repository use `dnf config-manager --set-enabled repository`. to disable a repository use `dnf config-manager --set-disabled repository`. to list enabled repositories use `dnf repolist`. to list all repositories use `dnf repolist -v`. to refresh the package cache use `dnf makecache`. to list history of transactions use `dnf history`. to undo a transaction use `dnf history undo transaction-id`. to rollback a transaction use `dnf history rollback transaction-id`.

| Package Manager | Description                                                                   | When to Use                                                                                                                                                 | Benefits                                                                                                                                   |
| --------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| `rpm`           | Low-level package manager for RPM-based Linux distributions.                  | Use `rpm` for direct control over package installation, upgrades, and removals. Useful for advanced users who need precise control over package management. | Provides detailed control over package management. Can be used in scripts for automated package management.                                |
| `yum`           | High-level package manager for RPM-based Linux distributions.                 | Use `yum` for easier package management with automatic dependency resolution. Suitable for most users.                                                      | Simplifies package management with automatic dependency resolution. Provides a higher-level interface for managing packages.               |
| `dnf`           | Modern package manager for RPM-based Linux distributions, successor to `yum`. | Use `dnf` for modern package management with improved performance and better dependency handling. Recommended for newer systems.                            | Improved performance and better dependency handling compared to `yum`. Provides a more modern and efficient package management experience. |

#### DPKG Based Systems (Debian, Ubuntu)

`dpkg` is the package manager for DPKG-based Linux distributions. It can be used to install, upgrade, query, and remove software packages in the DEB format. Use `dpkg -i package.deb` to install a package, `dpkg -l package` to query a package, and `dpkg -r package` to remove a package. to list all installed packages use `dpkg -l`. to list files in a package use `dpkg -L package`.

`apt` is a high-level package manager for DPKG-based Linux distributions. It can be used to install, upgrade, query, and remove software packages and dependencies. Use `apt install package` to install a package, `apt upgrade package` to upgrade a package, `apt list package` to query a package, and `apt remove package` to remove a package. to list all installed packages use `apt list --installed`. to search for a package use `apt search package`. to update all packages use `apt upgrade`. to clean the package cache use `apt clean`. to remove unused packages use `apt autoremove`. `apt purge package` is used to remove a package and its configuration files. to list package information use `apt show package`. to show package dependencies use `apt depends package`. to show reverse dependencies use `apt rdepends package`. to show package changelog use `apt changelog package`. to show package policy use `apt policy package`. to show package download size use `apt download package`. to show package source use `apt source package`.

### Services

`systemctl` is a command-line tool for managing services on Linux systems. It can be used to start, stop, restart, enable, disable, and query services.
Use `systemctl start service` to start a service,
`systemctl stop service` to stop a service,
`systemctl restart service` to restart a service,
`systemctl enable service` to enable a service, enable means that the service will start automatically at boot time,
`systemctl is-enabled service` to check if a service is enabled,
`systemctl disable service` to disable a service,
`systemctl is-active service` to check if a service is active,
`systemctl disable service` to disable a service,  
`systemctl status service` to query the status of a service.
to list all services use `systemctl list-units --type=service`.
to list all active services use `systemctl list-units --type=service --state=active`.
to list all failed services use `systemctl list-units --type=service --state=failed`. to list all enabled services use `systemctl list-unit-files --type=service --state=enabled`. to list all disabled services use `systemctl list-unit-files --type=service --state=disabled`.
to list all masked services use `systemctl list-unit-files --type=service --state=masked`. to reload the systemd manager configuration use `systemctl daemon-reload`.
to reload the systemd manager configuration and all unit files use `systemctl daemon-reexec`. to show the system journal use `journalctl`.
to show the system journal for a specific service use `journalctl -u service`.
to show the system journal for a specific unit use `journalctl -u unit`.
to show the system journal since a specific time use `journalctl --since "2022-01-01 00:00:00"`.
to show the system journal for a specific time range use `journalctl --since "2022-01-01 00:00:00" --until "2022-01-02 00:00:00"`.
to show the system journal for a specific priority use `journalctl -p priority`.
to show the system journal for a specific user use `journalctl --user`.
to show the system journal for a specific boot use `journalctl -b bootnumber`.
to show the system journal for a specific process use `journalctl _PID=pid`.
to show the system journal for a specific message use `journalctl MESSAGE=message`.
to show the system journal for a specific executable use `journalctl _EXE=executable`.
to show the system journal for a specific unit use `journalctl _SYSTEMD_UNIT=unit`.
to show the system journal for a specific facility use `journalctl SYSLOG_FACILITY=facility`.
to show the system journal for a specific identifier use `journalctl _SYSTEMD_INVOCATION_ID=id`.
to show the system journal for a specific field use `journalctl FIELD=value`.

### Process Management

`ps` displays information about processes. It can be used to view running processes, their process IDs (PIDs), parent process IDs (PPIDs), and resource usage. Use `-e` to display all processes, `-f` to display full information, and `-u` to display processes for a specific user. Example: `ps -u username`. `ps aux` is used to display all processes in a user-friendly format. `ps -ef` is used to display all processes in a detailed format. it also shows the parent process ID (PPID), the terminal associated with the process (TTY), and the start time of the process.

`top` displays real-time information about system resources and processes. It can be used to view CPU usage, memory usage, running processes, and system uptime. Use `q` to quit the top command.

`kill` sends signals to processes. It can be used to terminate or send signals to running processes. Use `kill PID` to send a signal to a process, `kill -9 PID` to forcefully terminate a process, and `killall processname` to send a signal to all processes with a specific name. Example: `kill 1234`, `kill -9 1234`, `killall processname`.

`pkill` sends signals to processes based on their name. It can be used to terminate or send signals to running processes based on their name. Use `pkill processname` to send a signal to a process, `pkill -9 processname` to forcefully terminate a process, and `pkill -u username` to send a signal to all processes owned by a specific user. Example: `pkill processname`, `pkill -9 processname`, `pkill -u username`.

`pgrep` displays process IDs based on their name. It can be used to search for processes based on their name and display their process IDs. Use `pgrep processname` to display the process ID of a process. Example: `pgrep processname`.

orphans are processes that have been abandoned by their parent process. They continue to run in the background even after their parent process has terminated. Orphan processes are adopted by the init process (PID 1) on Unix-like systems. usually when a parent process terminates, the child process is terminated as well. However, if the parent process does not wait for the child process to terminate, the child process becomes an orphan and is adopted by the init process. it can happen when a parent process terminates forcefully or unexpectedly.

### System Information

`df` displays disk space usage on the system. It can be used to view the amount of disk space used and available on mounted filesystems. `-h` flag can be used to display the output in a human-readable format. `-T` displays the filesystem type.

`arch` displays the system architecture. It can be used to view the system architecture, such as x86_64, i386, or arm64.

`uname` displays system information. It can be used to view information about the system, such as the kernel version, architecture, and operating system. Use `-a` to display all information, `-s` to display the kernel name, `-n` to display the network node hostname, `-r` to display the kernel release, `-v` to display the kernel version, `-m` to display the machine hardware name, and `-p` to display the processor type.

`hostname` displays the hostname of the system. It can be used to view the system's hostname and change it if needed.

`uptime` displays the system uptime and load average. It can be used to view how long the system has been running, the current system load, and the number of users logged in.this information is stored in the /proc/uptime file.

`free` displays the amount of free and used memory in the system. It can be used to view memory usage, swap usage, and total available memory. flags like `-h` can be used to display the output in a human-readable format. `-m` displays the output in megabytes.

    swap space is a portion of the hard disk that is used as virtual memory when the physical memory (RAM) is full. It allows the system to swap data between RAM and the hard disk to free up memory and prevent system crashes due to memory exhaustion.

`ip addr show` and `ifconfig` displays and configures network interfaces on Unix-like operating systems. It can be used to view information about network interfaces, configure network settings, and troubleshoot network connectivity issues.

`netstat` displays network connections, routing tables, and interface statistics. It can be used to view active network connections, routing information, and network interface statistics. Use `-t` to display TCP connections, `-u` to display UDP connections, and `-l` to display listening ports. Example: `netstat -tuln`.

`ss` displays socket statistics. It can be used to view detailed information about network sockets, such as active connections, listening ports, and socket states. Use `-t` to display TCP sockets, `-u` to display UDP sockets, and `-l` to display listening sockets. Example: `ss -tuln`.

`lscpu` displays CPU information. It can be used to view detailed information about the CPU, such as the number of cores, threads, and cache sizes.

`lsblk` displays block device information. It can be used to view information about block devices, such as hard drives, solid-state drives, and partitions.

### Archive Management

`tar` is a command-line tool for creating, extracting, and managing tar archives. It can be used to compress and decompress files and directories, create backups, and transfer data. Use `tar -czvf archive.tar file1 file2` to create a tar archive, `tar -xzvf archive.tar` to extract a tar archive, and `tar -tvf archive.tar` to list the contents of a tar archive. Use `-c` to create an archive, `-x` to extract an archive, `-t` to list the contents of an archive, `-v` for verbose output, and `-f` to specify the archive file. Use `-z` to compress with gzip, `-j` to compress with bzip2, and `-J` to compress with xz. `-C /directory` can be used to specify the directory to extract to.
Example: `tar -czvf archive.tar.gz file1 file2`, `tar -xzvf archive.tar.gz`.

`zip` is a command-line tool for creating, extracting, and managing zip archives. It can be used to compress and decompress files and directories, create backups, and transfer data. Use `zip archive.zip file1 file2` to create a zip archive, `unzip archive.zip` to extract a zip archive, and `unzip -l archive.zip` to list the contents of a zip archive. Use `-r` to recursively compress directories, `-l` to list the contents of an archive, and `-d` to delete files from an archive. Example: `zip -r archive.zip directory`, `unzip archive.zip`. First install this package.
