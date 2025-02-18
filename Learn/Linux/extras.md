# General Information

`[vagrant@localhost ~]$` is the default command prompt for a Vagrant virtual machine. It consists of the username `vagrant` and the hostname `localhost`. The hostname `localhost` is used to refer to the local system, while the username `vagrant` is the default username for a Vagrant virtual machine. The `~` symbol represents the current user's home directory. The `$` symbol indicates that the user has normal user privileges. If the user has root privileges, the command prompt will end with a `#` symbol.

`touch file{1..5}.txt` creates five empty files named `file1.txt`, `file2.txt`, `file3.txt`, `file4.txt`, and `file5.txt`. The `{1..5}` syntax is used to generate a sequence of numbers from 1 to 5, which are then appended to the filename `file.txt`.

## Change Hostname

Temporary Change (until reboot):

`sudo hostname new-hostname`

Permanent Change:

`sudo hostnamectl set-hostname new-hostname`

Manually edit the hostname file:

`sudo vim /etc/hostname`

Then replace the old hostname with the new one.

Update /etc/hosts:

`sudo vim /etc/hosts`

`/dev/null` is a special file in Unix-like operating systems that discards all data written to it. It is often used to redirect output to nothing, effectively suppressing it. For example, `command > /dev/null` redirects the output of `command` to `/dev/null`, effectively silencing any output.`cat /dev/null > file` will delete the content of file.

## Create a file and append text to it

note: there should be no space between `<<` and `EOF` and around `EOF`

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
