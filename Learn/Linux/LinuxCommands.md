# Linux Commands

## Table of Contents

- [Basic Commands](#basic-commands)
- [File Content Commands](#file-content-commands)
- [System Information Commands](#system-information-commands)
- [Linking Commands](#linking-commands)
- [History and Searching](#history-and-searching)
- [Text Processing Commands](#text-processing-commands)
- [Input/Output Redirection](#inputoutput-redirection)
- [User Management](#user-management)
- [File Permissions](#file-permissions)
- [Sudo](#sudo)
- [Package Management](#package-management)
- [Services](#services)
- [Process Management](#process-management)
- [System Information](#system-information)
- [Archive Management](#archive-management)
- [Networking](#networking)

## Basic Commands

### `man`

Displays the manual page for a **command**. It can be used to view information about a command, including its syntax, options, and usage examples.

### `--help`

Displays help information for a command. It can be used to view a brief description of a command, its options, and how to use it.

### `pwd`

Displays the current working directory. It can be used to view the full path of the current directory and navigate to other directories.

- `-L`: Follow symbolic links.
- `-P`: Use the physical directory structure without following symbolic links.

### `mkdir`

Creates a new directory. It can be used to create directories in the current directory or specify a path to create directories in a specific location.

- `-p`: Create parent directories if they do not exist.

### `cd`

Changes the current working directory. It can be used to navigate to different directories on the system.

- `cd -`: Switch to the previous directory.
- `cd ~`: Go to the home directory.

### `ls`

Lists the contents of a directory. It can be used to view files and directories in the current directory, as well as their permissions, ownership, and size.

- `-l`: Displays detailed information about files and directories.
- `-a`: Displays hidden files and directories.
- `-h`: Displays file sizes in a human-readable format.
- `-t`: Sorts files and directories by modification time.
- `-r`: Reverses the order of the sorting.
- `-d`: Displays only directories.
- `-R`: Recursively lists subdirectories.

### `touch`

Creates a new empty file. It can be used to create files in the current directory or specify a path to create files in a specific location.

### `cp`

Copies files and directories. It can be used to make copies of files and with `-r` flag directories in the current directory or specify a source and destination path.

### `mv`

Moves or renames files and directories. It can be used to move files and directories to a different location or rename them.

### `rm`

Removes files and directories. It can be used to delete files and directories in the current directory or specify a path to delete files and directories in a specific location.

- `-r`: Used to delete directories.
- `-rf`: Used to force delete files and directories.

### `echo`

Displays text on the terminal. It can be used to print messages, variables, and command output.

- `-e`: Enable interpretation of backslash escapes.
- `-n`: Suppress the trailing newline.
- `-E`: Disable interpretation of backslash escapes.

### `date`

Displays the current date and time. It can be used to view the system date and time, format the output, and perform date and time calculations.

- `+%format`: Specify the output format.
- `-d`: Display a specific date and time.
- `-u`: Display the date and time in UTC.

### `cal`

Displays a calendar for a specific month or year. It can be used to view the calendar for the current month, a specific month, or a specific year.

- `-3`: Display the previous, current, and next month.
- `-y`: Display the calendar for the current year.

## File Content Commands

### `cat`

Displays the contents of a file. It can be used to view the contents of text files, concatenate multiple files, and create new files.

- `cat file1 file2 > file3`: Concatenate files.

### `less`

Displays the contents of a file one page at a time. It can be used to view the contents of text files and navigate through them using keyboard shortcuts.

- `-N`: Show line numbers.

### `more`

Displays the contents of a file one page at a time. It can be used to view the contents of text files and navigate through them using keyboard shortcuts in percentage.

### `head`

Displays the first few (default 10) lines of a file. It can be used to view the beginning of text files and specify the number of lines to display.

- `-n`: Specify the number of lines (e.g., `head -n 10 file`).

### `tail`

Displays the last few (default 10) lines of a file. It can be used to view the end of text files and specify the number of lines to display.

- `-n`: Specify the number of lines (e.g., `tail -n 10 file`).
- `-f`: Follow the output of a file in real-time.

## System Information Commands

### `hostname`

Displays the hostname of the system. It can be used to view the system's hostname and change it if needed.

### `who`

Displays information about users who are currently logged in. It can be used to view the usernames, terminal names, login times, and IP addresses of users who are logged in.

### `whoami`

Displays the username of the current user. It can be used to view the username of the current user and determine the permissions and privileges associated with that user.

> Difference between `hostname` and `whoami` is that `hostname` displays the system's hostname, while `whoami` displays the username of the current user.
>
> System hostname is the name that identifies a system on a network. It is used to uniquely identify the system and allow other systems to communicate with it. The hostname is typically set during the system installation process and can be changed later if needed.
>
> `vagrant@localhost` is the default hostname for a Vagrant virtual machine. It consists of the username "vagrant" and the hostname "localhost." The hostname "localhost" is used to refer to the local system, while the username "vagrant" is the default username for a Vagrant virtual machine.

### `file`

Determines the type of a file. It can be used to identify the file type, such as text, binary, or executable, and provide information about the file's contents and usage.

### `printenv`

Displays the environment variables. It can be used to view the environment variables available to the current user and their values.

## Linking Commands

### `ln`

Creates links between files. It can be used to create hard links and symbolic links to files and directories.

- `-s`: Used to create symbolic links.

### `unlink`

Removes links between files. It can be used to delete hard links and symbolic links to files and directories.

> **Hard Link vs. Symbolic Link**
>
> - Hard links are direct pointers to the file's inode on disk. They share the same inode number and data blocks as the original file. If the original file is deleted, the hard link still points to the data blocks, and the file's contents are preserved.
> - Symbolic links are indirect pointers to the file's path on disk. They contain the path to the original file and are treated as separate files. If the original file is deleted, the symbolic link becomes a dangling link and points to a non-existent file.

## History and Searching

### `history`

Displays the command history list.

- `-c`: Clear the history.
- `-w [filename]`: Write history to a file.
- `-r [filename]`: Read history from a file.
- `-a [filename]`: Append history to a file.
- `-d [offset]`: Delete a specific entry.
- `!number`: Repeat a specific command.

### `find`

Searches for files and directories. It can be used to search for files and directories based on various criteria, such as name, size, type, and permissions.

- `-name`: Search by name.
- `-size`: Search by size.
- `-type`: Search by type.
- `-perm`: Search by permissions.
- Example: `find /path/to/directory -name "pattern"`.

### `locate`

Quickly searches for files and directories on the system. It can be used to find files and directories based on a keyword or pattern.

- `updatedb`: Update the database used by `locate`. (First install this package)

## Text Processing Commands

### `cut`

Extracts sections from each line of a file. It can be used to cut out specific columns or fields from a file, such as the first, second, or nth field.

- `-d`: Specify the delimiter.
- `-f`: Specify the field.
- Example: `cut -d: -f1,3 file.txt` (`-d:` specifies the colon as the delimiter, and `-f1,3` specifies the first and third fields).

### `awk`

A powerful programming language for text processing. It can be used to manipulate and analyze text files, extract data, and generate reports.

- Example: `awk '{print $1, $3}' file.txt` (prints the first and third fields of each line in the file).
- `-F`: Specify the field separator. Example: `awk -F: '{print $1, $3}' file.txt` (`-F:` specifies the colon as the field separator).
- `-f`: Specify a script file. Example: `awk -f script.awk file.txt`.
- `-v`: Pass variables to the script. Example: `awk -v var=value '{print $1, $3, var}' file.txt`.
- `-i`: Edit files in place. Example: `awk -i inplace '{print $1, $3}' file.txt`.

### `sed`

A stream editor for filtering and transforming text. It can be used to perform text transformations, deletions, substitutions, and more.

- Example: `sed 's/pattern/replacement/g' file.txt` (replaces all occurrences of "pattern" with "replacement" in the file).
- `-i`: Edit files in place. Example: `sed -i 's/pattern/replacement/g' file.txt`.
- `-e`: Specify multiple commands. Example: `sed -e 's/pattern1/replacement1/g' -e 's/pattern2/replacement2/g' file.txt`.
- `-f`: Specify a script file. Example: `sed -f script.sed file.txt`.

### `wc`

Counts lines, words, and characters in a file or standard input. It can be used to count the number of lines, words, and characters in a file or the output of a command.

- `-l`: Count lines.
- `-w`: Count words.
- `-c`: Count characters.
- Example: `wc -l file.txt`.

### `grep`

A powerful command-line utility used for searching plain-text data for lines that match a regular expression. It stands for "Global Regular Expression Print".

<details>
<summary>Commonly used options:</summary>

- `-i`: Ignore case distinctions in both the pattern and the input files.
  Example: `grep -i "pattern" file.txt`
- `-v`: Invert the match, displaying lines that do not match the pattern.
  Example: `grep -v "pattern" file.txt`
- `-r` or `-R`: Recursively search directories.
  Example: `grep -r "pattern" /path/to/directory`
- `-l`: Print only the names of files with matching lines.
  Example: `grep -l "pattern" *.txt`
- `-L`: Print only the names of files with no matching lines.
  Example: `grep -L "pattern" *.txt`
- `-n`: Prefix each matching line with its line number.
  Example: `grep -n "pattern" file.txt`
- `-c`: Print only a count of matching lines per file.
  Example: `grep -c "pattern" file.txt`
- `-A [num]`: Print `[num]` lines of trailing context after matching lines.
  Example: `grep -A 3 "pattern" file.txt`
- `-B [num]`: Print `[num]` lines of leading context before matching lines.
  Example: `grep -B 3 "pattern" file.txt`
- `-C [num]`: Print `[num]` lines of context both before and after matching lines.
  Example: `grep -C 3 "pattern" file.txt`
- `-e`: Allow specifying multiple patterns.
  Example: `grep -e "pattern1" -e "pattern2" file.txt`
- `-f`: Obtain patterns from a file, one per line.
  Example: `grep -f patterns.txt file.txt`
- `-w`: Match only whole words.
  Example: `grep -w "pattern" file.txt`
- `-x`: Match only whole lines.
  Example: `grep -x "pattern" file.txt`
- `-o`: Print only the matched parts of a matching line.
  Example: `grep -o "pattern" file.txt`
- `-q`: Quiet mode, exit immediately with zero status if any match is found.
  Example: `grep -q "pattern" file.txt`
- `-s`: Suppress error messages about nonexistent or unreadable files.
  Example: `grep -s "pattern" file.txt`
- `-H`: Always print the filename with output lines.
  Example: `grep -H "pattern" file.txt`
- `-h`: Never print filenames with output lines.
  Example: `grep -h "pattern" file.txt`
- `--color`: Highlight the matching text.
  Example: `grep --color "pattern" file.txt`
- `--exclude`: Exclude files that match the specified pattern.
  Example: `grep --exclude="*.txt" "pattern" /path/to/directory`
- `--include`: Search only files that match the specified pattern.
  Example: `grep --include="*.txt" "pattern" /path/to/directory`
- `--exclude-dir`: Exclude directories that match the specified pattern.
  Example: `grep --exclude-dir="dir*" "pattern" /path/to/directory`
- `--include-dir`: Search only directories that match the specified pattern.
  Example: `grep --include-dir="dir*" "pattern" /path/to/directory`

</details>

## Input/Output Redirection

### `>`

Redirects standard output to a file. It can be used to write the output of a command to a file, create a new file, or overwrite an existing file.

- Example: `command > file.txt`.

### `>>`

Appends standard output to a file. It can be used to append the output of a command to a file or create a new file if it does not exist.

- Example: `command >> file.txt`.

### `<`

Redirects standard input from a file. It can be used to read input from a file instead of the keyboard.

- Example: `command < file.txt`.

### `|`

Redirects standard output from one command to standard input of another command. It can be used to chain multiple commands together and create pipelines.

- Example: `command1 | command2`.

### `xargs`

Reads input from standard input and executes a command with the input as arguments. It can be used to build and execute commands from standard input, such as the output of another command.

- Use `command | xargs` to pass the output of a command as arguments to another command.
- Example: `ls | xargs rm`.

> Difference between `xargs` and `|` is that `xargs` reads input from standard input and executes a command with the input as arguments, while `|` (pipe) passes the output of one command as input to another command.
>
> Example: `ls | xargs rm` and `ls | rm`. `ls | xargs rm` will remove all files in the current directory, while `ls | rm` will not work because `rm` does not accept input from standard input.

### `2>`

Redirects standard error to a file. It can be used to write error messages to a file instead of the terminal.

- Example: `command 2> error.txt`.

### `2>>`

Appends standard error to a file. It can be used to append error messages to a file or create a new file if it does not exist.

- Example: `command 2>> error.txt`.

### `&>`

Redirects both standard output and standard error to a file. It can be used to write both output and error messages to a file.

- Example: `command &> output.txt`.

### `&>>`

Appends both standard output and standard error to a file. It can be used to append both output and error messages to a file or create a new file if it does not exist.

- Example: `command &>> output.txt`.

## User Management

Some important points:

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

### Example of sample user from `/etc/passwd` file

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

### Example of sample group from `/etc/group` file

`vagrant:x:1000:vagrantTest`

| Field          | Description                    | Sample Value |
| -------------- | ------------------------------ | ------------ |
| Group Name     | Group name                     | vagrant      |
| Password       | Encrypted password placeholder | x            |
| Group ID (GID) | Group identifier               | 1000         |
| Group Members  | Users who are members of group | vagrantTest  |

### `id`

Displays information about a user or group. It can be used to view the user ID (UID), group ID (GID), and group membership of a user.

- `-u`: Display the user ID.
- `-g`: Display the group ID.
- `-G`: Display the group membership.
- Example: `id username`.

### `useradd`

Adds a new user to the system. It can be used to create a new user account with a specified username, user ID (UID), group ID (GID), home directory, and login shell.

- `-u`: Specify the user ID.
- `-g`: Specify the group ID.
- `-d`: Specify the home directory.
- `-s`: Specify the login shell.
- Example: `useradd -u 1001 -g 1001 -d /home/test -s /bin/bash test`, `useradd test`.

### `adduser` (For Ubuntu and Debian based systems)

Adds a new user to the system. It can be used to create a new user account with a specified username, user ID (UID), group ID (GID), home directory, and login shell.

- `--uid`: Specify the user ID.
- `--gid`: Specify the group ID.
- `--home`: Specify the home directory.
- `--shell`: Specify the login shell.
- Example: `adduser --uid 1001 --gid 1001 --home /home/test --shell /bin/bash test`, `adduser test`.

### `groupadd`

Adds a new group to the system. It can be used to create a new group with a specified group name and group ID (GID).

- `-g`: Specify the group ID.
- Example: `groupadd -g 1001 testgroup`, `groupadd testgroup`.

### `usermod`

Modifies user account settings or edit `/etc/passwd` or `/etc/group` manually. It can be used to change user account attributes, such as the username, user ID (UID), group ID (GID), home directory, and login shell.

- `-u`: Change the user ID.
- `-g`: Change the group ID.
- `-d`: Change the home directory.
- `-s`: Change the login shell.
- `-l`: Change the username.
- `-aG`: Add a user to a secondary group.
- `-a`: Append the user to the group.
- Example: `usermod -u 1002 -g 1002 -d /home/test2 -s /bin/bash test`, `usermod -l newname oldname`, `usermod -aG groupname username` (this command adds a user to a secondary group).

### `passwd`

Changes a user's password. It can be used to change the password for a user account.

- `passwd username`: Change the password for a specific user.
- `passwd`: Change the password for the current user.

### `userdel`

Deletes a user account. It can be used to remove a user account from the system.

- `-r`: Remove the user's home directory and mail spool.
- Example: `userdel -r test`, `userdel test`.

### `groupdel`

Deletes a group. It can be used to remove a group from the system.

- Example: `groupdel testgroup`.

### `su - username`

Switches to another user account. It can be used to switch to another user account and run commands as that user.

- `-`: Start a new login shell as the specified user.
- Example: `su - test`. (root user can switch to any user without password).

### `last`

Displays the last login information for users. It can be used to view the login history of users, including the date, time, and duration of their last login.

- `-n`: Specify the number of entries to display.
- Example: `last -n 5`.

## File Permissions

### Permissions

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

### `chown`

Changes the owner and group of files and directories. It can be used to change the owner and group of a file or directory to a specific user and group.

- `chown username:groupname file`: Change the owner and group.
- `-R`: Change ownership recursively for directories.
- Example: `chown username:groupname file`, `chown -R username:groupname directory`.
- If you want to change only owner then use `chown username file`.
- If you want to change only group then use `chown :groupname file`.

### `chmod`

Changes the permissions of files and directories. It can be used to change the permissions of a file or directory to allow or restrict read, write, and execute access for the owner, group, and others.

- `chmod u=rwx,g=rx,o=r file`: Set permissions.
- `-R`: Change permissions recursively for directories.
- Example: `chmod u=rwx,g=rx,o=r file`, `chmod -R u=rwx,g=rx,o=r directory`.
- You can use numeric values like `chmod 777 file` or `chmod 755 file`.
  - 777 means read, write, and execute for owner, group, and others.
  - 755 means read, write, and execute for owner and read and execute for group and others.
  - `4` for read, `2` for write, and `1` for execute.

## Sudo

### `sudo`

Allows users to run commands with elevated privileges. It can be used to perform administrative tasks that require root access, such as installing software, configuring system settings, and managing files and directories.

- `sudo command`: Run a command with root privileges.
- `sudo -i`: Start a new shell session as the root user.
- `sudo -u username command`: Run a command as a specific user.
- `sudo -l`: List available commands for the current user.
- `sudo -v`: Refresh the sudo timestamp.
- `sudo -k`: Invalidate the sudo timestamp.

> The difference between `sudo -i` and `sudo su` is that `sudo -i` starts a new shell session as the root user, while `sudo su` switches to the root user in the current shell session.
>
> The `sudoers` file (`/etc/sudoers`) contains rules and configurations for the `sudo` command. It defines which users and groups are allowed to run commands with elevated privileges and what commands they can run.
>
> The `sudo` group is a special group that allows users to run commands with elevated privileges using the `sudo` command. Users who are members of the `sudo` group can run commands as the root user.
>
> The `sudo` command logs all `sudo` usage to the system log file (`/var/log/auth.log` or `/var/log/secure`). It records the user, command, timestamp, and outcome of each `sudo` invocation.

### `visudo`

Edits the `sudoers` file. It can be used to edit the `sudoers` file and configure rules for the `sudo` command.

- `visudo`: Open the `sudoers` file in the default text editor.
- `visudo -c`: Check the syntax of the `sudoers` file for errors.
- To add a user to `sudoers` file use `sudo usermod -aG sudo username`.
- Or can edit and add user to `sudoers` file by `sudo visudo` and add `username ALL=(ALL:ALL) ALL`.

For Ubuntu and Debian based systems:

- `export Editor=vim`: Set the default editor to vim (because by default it is nano).

### `/etc/sudoers`

File contains rules and configurations for the `sudo` command. It defines which users and groups are allowed to run commands with elevated privileges and what commands they can run. The `sudoers` file should be edited using the `visudo` command to prevent syntax errors and ensure proper configuration.

### `/etc/sudoers.d`

Directory contains additional configuration files for the `sudo` command. It can be used to add custom rules and configurations for specific `users` or `groups`. Files in this directory should follow the same syntax as the main `sudoers` file.

- Add a file in this directory with `sudo visudo -f /etc/sudoers.d/filename` and add `username ALL=(ALL:ALL) ALL` in this file, for group `%groupname ALL=(ALL:ALL) ALL`.

## Package Management

### `curl`

A command-line tool for transferring data with URLs. It can be used to download files, upload files, and perform various network-related tasks.

- `curl URL`: Download a file from a URL.
- `-O`: Save the file with the original name.
- `-o filename`: Save the file with a specific name.
- `-L`: Follow redirects.
- `-I`: Display the HTTP headers.
- `-X`: Specify the HTTP method.
- `-d`: Send data in a POST request.
- `-H`: Add custom headers.
- `-u`: Specify authentication credentials.
- `-v`: Enable verbose mode (displays detailed information about the request and response).

### `wget`

A command-line tool for downloading files from the web. It can be used to download files, recursively download files from a website, and perform various network-related tasks.

- `wget URL`: Download a file from a URL.
- `-O filename`: Save the file with a specific name.
- `-r`: Recursively download files.
- `-np`: Exclude parent directories.
- `-nc`: Skip existing files.
- `-c`: Resume interrupted downloads.
- `-q`: Enable quiet mode.

### RPM Based Systems (Red Hat, CentOS, Fedora)

#### `rpm`

The package manager for RPM-based Linux distributions. It can be used to install, upgrade, query, and remove software packages in the RPM format.

- `rpm -i package.rpm`: Install a package.
- `rpm -U package.rpm`: Upgrade a package.
- `rpm -q package`: Query a package.
- `rpm -e package`: Remove a package.
- `rpm -qa`: List all installed packages.
- `rpm -ql package`: List files in a package.
- `rpm -V package`: Verify a package.
- `rpm -ivh package.rpm`: Install a package with dependencies.
- `rpm -ivh --nodeps package.rpm`: Install a package without dependencies.
- `rpm -ivh --force package.rpm`: Install a package and ignore conflicts.
- `-v`: Verbose output.
- `-h`: Hash marks (printed as the package archive is unpacked).

#### `yum`

A high-level package manager for RPM-based Linux distributions. It can be used to install, upgrade, query, and remove software packages and dependencies.

- `yum install package`: Install a package.
- `yum update package`: Upgrade a package.
- `yum list package`: Query a package.
- `yum remove package`: Remove a package.
- `yum list installed`: List all installed packages.
- `yum search package`: Search for a package.
- `yum install package`: Install a package with dependencies.
- `yum update`: Update all packages.
- `yum remove package`: Remove a package and its dependencies.
- `yum clean all`: Clean the package cache.

#### `dnf`

A package manager for RPM-based Linux distributions. It can be used to install, upgrade, query, and remove software packages and dependencies.

- `dnf install package`: Install a package.
- `dnf upgrade package`: Upgrade a package.
- `dnf list package`: Query a package.
- `dnf remove package`: Remove a package.
- `dnf list installed`: List all installed packages.
- `dnf search package`: Search for a package.
- `dnf install package`: Install a package with dependencies.
- `dnf upgrade`: Update all packages.
- `dnf remove package`: Remove a package and its dependencies.
- `dnf clean all`: Clean the package cache.
- Repository configuration files are stored in the `/etc/yum.repos.d` directory.
- `dnf config-manager --set-enabled repository`: Enable a repository.
- `dnf config-manager --set-disabled repository`: Disable a repository.
- `dnf repolist`: List enabled repositories.
- `dnf repolist -v`: List all repositories.
- `dnf makecache`: Refresh the package cache.
- `dnf history`: List history of transactions.
- `dnf history undo transaction-id`: Undo a transaction.
- `dnf history rollback transaction-id`: Rollback a transaction.

| Package Manager | Description                                                                   | When to Use                                                                                                                                                 | Benefits                                                                                                                                   |
| --------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| `rpm`           | Low-level package manager for RPM-based Linux distributions.                  | Use `rpm` for direct control over package installation, upgrades, and removals. Useful for advanced users who need precise control over package management. | Provides detailed control over package management. Can be used in scripts for automated package management.                                |
| `yum`           | High-level package manager for RPM-based Linux distributions.                 | Use `yum` for easier package management with automatic dependency resolution. Suitable for most users.                                                      | Simplifies package management with automatic dependency resolution. Provides a higher-level interface for managing packages.               |
| `dnf`           | Modern package manager for RPM-based Linux distributions, successor to `yum`. | Use `dnf` for modern package management with improved performance and better dependency handling. Recommended for newer systems.                            | Improved performance and better dependency handling compared to `yum`. Provides a more modern and efficient package management experience. |

### DPKG Based Systems (Debian, Ubuntu)

#### `dpkg`

The package manager for DPKG-based Linux distributions. It can be used to install, upgrade, query, and remove software packages in the DEB format.

- `dpkg -i package.deb`: Install a package.
- `dpkg -l package`: Query a package.
- `dpkg -r package`: Remove a package.
- `dpkg -l`: List all installed packages.
- `dpkg -L package`: List files in a package.

#### `apt`

A high-level package manager for DPKG-based Linux distributions. It can be used to install, upgrade, query, and remove software packages and dependencies.

- `apt install package`: Install a package.
- `apt upgrade package`: Upgrade a package.
- `apt list package`: Query a package.
- `apt remove package`: Remove a package.
- `apt list --installed`: List all installed packages.
- `apt search package`: Search for a package.
- `apt upgrade`: Update all packages.
- `apt clean`: Clean the package cache.
- `apt autoremove`: Remove unused packages.
- `apt purge package`: Remove a package and its configuration files.
- `apt show package`: List package information.
- `apt depends package`: Show package dependencies.
- `apt rdepends package`: Show reverse dependencies.
- `apt changelog package`: Show package changelog.
- `apt policy package`: Show package policy.
- `apt download package`: Show package download size.
- `apt source package`: Show package source.

## Services

### `systemctl`

A command-line tool for managing services on Linux systems. It can be used to start, stop, restart, enable, disable, and query services.

- `systemctl start service`: Start a service.
- `systemctl stop service`: Stop a service.
- `systemctl restart service`: Restart a service.
- `systemctl enable service`: Enable a service (enable means that the service will start automatically at boot time).
- `systemctl is-enabled service`: Check if a service is enabled.
- `systemctl disable service`: Disable a service.
- `systemctl is-active service`: Check if a service is active.
- `systemctl status service`: Query the status of a service.
- `systemctl daemon-reload`: Reload the systemd manager configuration.
- `systemctl list-units --type=service`: List all services.
- `systemctl list-units --type=service --state=active`: List all active services.
- `systemctl list-units --type=service --state=failed`: List all failed services.
- `systemctl list-unit-files --type=service --state=enabled`: List all enabled services.
- `systemctl list-unit-files --type=service --state=disabled`: List all disabled services.
- `systemctl list-unit-files --type=service --state=masked`: List all masked services.
- `systemctl daemon-reexec`: Reload the systemd manager configuration and all unit files.
- `journalctl`: Show the system journal.
- `journalctl -u service`: Show the system journal for a specific service.
- `journalctl -u unit`: Show the system journal for a specific unit.
- `journalctl --since "2022-01-01 00:00:00"`: Show the system journal since a specific time.
- `journalctl --since "2022-01-01 00:00:00" --until "2022-01-02 00:00:00"`: Show the system journal for a specific time range.
- `journalctl -p priority`: Show the system journal for a specific priority.
- `journalctl --user`: Show the system journal for a specific user.
- `journalctl -b bootnumber`: Show the system journal for a specific boot.
- `journalctl _PID=pid`: Show the system journal for a specific process.
- `journalctl MESSAGE=message`: Show the system journal for a specific message.
- `journalctl _EXE=executable`: Show the system journal for a specific executable.
- `journalctl _SYSTEMD_UNIT=unit`: Show the system journal for a specific unit.
- `journalctl SYSLOG_FACILITY=facility`: Show the system journal for a specific facility.
- `journalctl _SYSTEMD_INVOCATION_ID=id`: Show the system journal for a specific identifier.
- `journalctl FIELD=value`: Show the system journal for a specific field.

## Process Management

### `ps`

Displays information about processes. It can be used to view running processes, their process IDs (PIDs), parent process IDs (PPIDs), and resource usage.

- `-e`: Display all processes.
- `-f`: Display full information.
- `-u`: Display processes for a specific user.
- Example: `ps -u username`.
- `ps aux`: Display all processes in a user-friendly format.
- `ps -ef`: Display all processes in a detailed format (also shows the parent process ID (PPID), the terminal associated with the process (TTY), and the start time of the process).

### `top`

Displays real-time information about system resources and processes. It can be used to view CPU usage, memory usage, running processes, and system uptime.

- Use `q` to quit the top command.

### `kill`

Sends signals to processes. It can be used to terminate or send signals to running processes.

- `kill PID`: Send a signal to a process.
- `kill -9 PID`: Forcefully terminate a process.
- `killall processname`: Send a signal to all processes with a specific name.
- Example: `kill 1234`, `kill -9 1234`, `killall processname`.

### `pkill`

Sends signals to processes based on their name. It can be used to terminate or send signals to running processes based on their name.

- `pkill processname`: Send a signal to a process.
- `pkill -9 processname`: Forcefully terminate a process.
- `pkill -u username`: Send a signal to all processes owned by a specific user.
- Example: `pkill processname`, `pkill -9 processname`, `pkill -u username`.

### `lsof`

Lists open files and processes. It can be used to view information about open files, network connections, and processes that are using them.

- `-i`: Display network connections.
- `-u`: Display processes for a specific user.
- `-t`: Display only process IDs (PIDs).
- Example: `lsof -i`, `lsof -u username`, `lsof -t`. (First install this package).

### `pgrep`

Displays process IDs based on their name. It can be used to search for processes based on their name and display their process IDs.

- `pgrep processname`: Display the process ID of a process.
- Example: `pgrep processname`.

> Orphans are processes that have been abandoned by their parent process. They continue to run in the background even after their parent process has terminated. Orphan processes are adopted by the init process (PID 1) on Unix-like systems. Usually, when a parent process terminates, the child process is terminated as well. However, if the parent process does not wait for the child process to terminate, the child process becomes an orphan and is adopted by the init process. It can happen when a parent process terminates forcefully or unexpectedly.

## System Information

### `df`

Displays disk space usage on the system. It can be used to view the amount of disk space used and available on mounted filesystems.

- `-h`: Display the output in a human-readable format.
- `-T`: Display the filesystem type.

### `arch`

Displays the system architecture. It can be used to view the system architecture, such as x86_64, i386, or arm64.

### `uname`

Displays system information. It can be used to view information about the system, such as the kernel version, architecture, and operating system.

- `-a`: Display all information.
- `-s`: Display the kernel name.
- `-n`: Display the network node hostname.
- `-r`: Display the kernel release.
- `-v`: Display the kernel version.
- `-m`: Display the machine hardware name.
- `-p`: Display the processor type.

### `hostname`

Displays the hostname of the system. It can be used to view the system's hostname and change it if needed.

### `uptime`

Displays the system uptime and load average. It can be used to view how long the system has been running, the current system load, and the number of users logged in. This information is stored in the `/proc/uptime` file.

### `free`

Displays the amount of free and used memory in the system. It can be used to view memory usage, swap usage, and total available memory.

- `-h`: Display the output in a human-readable format.
- `-m`: Display the output in megabytes.

> Swap space is a portion of the hard disk that is used as virtual memory when the physical memory (RAM) is full. It allows the system to swap data between RAM and the hard disk to free up memory and prevent system crashes due to memory exhaustion.

### `lscpu`

Displays CPU information. It can be used to view detailed information about the CPU, such as the number of cores, threads, and cache sizes.

### `lsblk`

Displays block device information. It can be used to view information about block devices, such as hard drives, solid-state drives, and partitions.

## Archive Management

### `tar`

A command-line tool for creating, extracting, and managing tar archives. It can be used to compress and decompress files and directories, create backups, and transfer data.

- `tar -czvf archive.tar file1 file2`: Create a tar archive.
- `tar -xzvf archive.tar`: Extract a tar archive.
- `tar -tvf archive.tar`: List the contents of a tar archive.
- `-c`: Create an archive.
- `-x`: Extract an archive.
- `-t`: List the contents of an archive.
- `-v`: Verbose output.
- `-f`: Specify the archive file.
- `-z`: Compress with gzip.
- `-j`: Compress with bzip2.
- `-J`: Compress with xz.
- `-C /directory`: Specify the directory to extract to.
- Example: `tar -czvf archive.tar.gz file1 file2`, `tar -xzvf archive.tar.gz`.

### `zip`

A command-line tool for creating, extracting, and managing zip archives. It can be used to compress and decompress files and directories, create backups, and transfer data.

- `zip archive.zip file1 file2`: Create a zip archive.
- `unzip archive.zip`: Extract a zip archive.
- `unzip -l archive.zip`: List the contents of a zip archive.
- `-r`: Recursively compress directories.
- `-l`: List the contents of an archive.
- `-d`: Delete files from an archive.
- Example: `zip -r archive.zip directory`, `unzip archive.zip`. (First install this package).

## Networking

### `ping`

Sends ICMP echo requests to a host. It can be used to test network connectivity, measure round-trip times, and troubleshoot network issues.

- `ping hostname`: Send ICMP echo requests to a host.
- `ping -c count`: Specify the number of packets to send.
- `ping -i interval`: Specify the interval between packets.
- Example: `ping google.com`, `ping -c 5 google.com`, `ping -i 2 google.com`.

### `ifconfig`

Displays and configures network interfaces on Unix-like operating systems. It can be used to view information about network interfaces, configure network settings, and troubleshoot network connectivity issues. (First install this package).

### `ip addr show`

Displays and configures network interfaces on Unix-like operating systems. It can be used to view information about network interfaces, configure network settings, and troubleshoot network connectivity issues.

### `ss`

Displays socket statistics. It can be used to view detailed information about network sockets, such as active connections, listening ports, and socket states.

- `-t`: Display TCP sockets.
- `-u`: Display UDP sockets.
- `-l`: Display listening sockets.
- Example: `ss -tuln`.

### `traceroute`

Traces the route to a host. It can be used to trace the path that packets take from the local host to a remote host.

- `traceroute hostname`: Trace the route to a host.
- `traceroute -n`: Display IP addresses instead of hostnames.
- `traceroute -q count`: Specify the number of packets to send.
- Example: `traceroute google.com`, `traceroute -n google.com`, `traceroute -q 5 google.com`.

### `netstat`

Displays network connections, routing tables, and interface statistics. It can be used to view active network connections, routing information, and network interface statistics.

- `-t`: Display TCP connections.
- `-u`: Display UDP connections.
- `-l`: Display listening ports.
- Example: `netstat -tuln`.
- `-a`: Display all sockets.
- `-n`: Display numerical addresses.
- `-p`: Display the process ID and name.
- `-r`: Display the routing table.
- `-s`: Display network statistics.
- `-i`: Display network interfaces.
- `-c`: Continuously refresh the output.
- Example: `netstat -antp` (display all TCP connections with process information).

### `nmap`

A network scanning tool. It can be used to discover hosts, services, and open ports on a network.

- `nmap hostname`: Scan a host.
- `nmap -p port`: Scan a specific port.
- `nmap -sV`: Detect service versions.
- Example: `nmap google.com`, `nmap -p 80 google.com`, `nmap -sV google.com`. (First install this package).

### `nslookup`

A DNS lookup tool. It can be used to query DNS servers, resolve hostnames, and retrieve DNS records.

- `nslookup hostname`: Query a DNS server.
- `nslookup -type=type`: Specify the record type.
- `nslookup -query=type`: Query a specific record type.
- Example: `nslookup google.com`, `nslookup -type=mx google.com`, `nslookup -query=mx google.com`.

### `dig`

A new DNS lookup tool. It can be used to query DNS servers, resolve hostnames, and retrieve DNS records.

- `dig hostname`: Query a DNS server.
- `dig -t type`: Specify the record type.
- `dig +short`: Display only the IP address.
- Example: `dig google.com`, `dig -t mx google.com`, `dig +short google.com`.

### `route`

Displays and configures the IP routing table. It can be used to view and modify the routing table, add or delete routes, and troubleshoot network connectivity issues.

- `route -n`: Display IP addresses instead of hostnames.
- `route add`: Add a route.
- `route del`: Delete a route.
- Example: `route -n`, `route add default gw`.

### `arp`

Displays and modifies the ARP cache. It can be used to view and modify the ARP cache, add or delete ARP entries, and troubleshoot network connectivity issues.

- `arp -n`: Display IP addresses instead of hostnames.
- `arp -s`: Add an ARP entry.
- `arp -d`: Delete an ARP entry.
- Example: `arp -n`, `arp -s ip mac`, `arp -d ip`.

### `mtr`

Combines the functionality of `ping` and `traceroute`. It can be used to trace the route to a host and measure round-trip times to each hop.

- `mtr hostname`: Trace the route to a host.
- `mtr -c count`: Specify the number of packets to send.
- `mtr -i interval`: Specify the interval between packets.
- Example: `mtr google.com`, `mtr -c 5 google.com`, `mtr -i 2 google.com`.

### `telnet`

A network protocol tool. It can be used to establish a connection to a remote host, test network services, and troubleshoot network connectivity issues.

- `telnet hostname port`: Connect to a host and port.
- `telnet -l username hostname port`: Specify a username.
- `telnet -a hostname port`: Enable automatic login.
- Example: `telnet google.com 80`, `telnet -l username google.com 22`, `telnet -a google.com 25`.

> It can be used to test network services like HTTP, SMTP, POP3, IMAP, SSH, FTP, etc. or to check if a port is open or closed.
