# Bash Scripting Extras

.bashrc is a shell script that Bash runs whenever it is started interactively. It initializes an interactive shell session. You can put any command in that file that you could type at the command prompt. You can also put commands that should be run when you log out or when you log in.

The .bashrc file is located in the user's home directory. It is a hidden file, so you need to use the ls -a command to see it.

When you log in, `source ~/.bashrc` is used to apply the configurations. This command reloads the file and makes the new settings available in the current session.

All the variables and aliases you define in the .bashrc file will be available in the current shell session. They will be loaded every time you start a new shell session.

## Additional configurations and aliases can be added here

## For example

```bash
alias ll='ls -la'
alias gs='git status' # Shorten git status command
alias ..='cd ..' # Shortcut to go up one directory
export PATH="$HOME/bin:$PATH" # this will add the bin directory in your home directory to the PATH environment variable
alias c='clear' # Shortcut to clear the terminal
```

## Difference between login and non-login shell

A login shell is a shell session that starts by logging in, either by entering a username and password or by running a command such as ssh. A login shell reads the .bash_profile file to set up the environment for the user.

A non-login shell is a shell session that starts without logging in, such as opening a new terminal window or running a command like bash. A non-login shell reads the .bashrc file to set up the environment for the user.

## Difference between .bashrc and .bash_profile

.bash_profile is executed for login shells, while .bashrc is executed for interactive non-login shells.

When you log in (type username and password) via console, either sitting at the machine, or remotely via ssh: .bash_profile is executed to configure your shell before the initial command prompt.

But, if you've already logged into your machine and open a new terminal window (xterm) or start a new bash instance (bash): .bashrc is executed before the window command prompt. .bashrc is also run when you start a new bash instance by typing /bin/bash in a terminal.

configurations in .bash_profile will not be available in non-login shells, and configurations in .bashrc will not be available in login shells.

.bash_profile is used to set environment variables and execute commands that should be run only once, while .bashrc is used to set up the shell environment for every shell session.

> when you put configurations in the .bashrc of user home directory, they will be available every time you start a new shell session for that particular user. but if you put it in /etc/bash.bashrc, it will be available for all users.

## Difference between .bashrc and other configuration files

`/etc/profile` is a system-wide configuration file that is executed when a user logs in. It sets environment variables and runs scripts that should be available to all users.

`/etc/bash.bashrc` is a system-wide configuration file that is executed for interactive shells. It sets environment variables and runs scripts that should be available to all users.

`/etc/bash.bash_logout` is a system-wide configuration file that is executed when a user logs out. It runs scripts that should be executed when a user logs out.

`/etc/profile.d/` is a directory that contains scripts that are executed when a user logs in. It is used to set environment variables and run scripts that should be available to all users.
