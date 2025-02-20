# Shell Special Variables

## Table of Contents

- [Shell Special Variables](#shell-special-variables)
  - [Table of Contents](#table-of-contents)
  - [`$0` - Script Name](#0---script-name)
  - [`$1`, `$2`, ... - Command-Line Arguments](#1-2----command-line-arguments)
  - [`$#` - Number of Command-Line Arguments](#---number-of-command-line-arguments)
  - [`$@` - All Command-Line Arguments](#---all-command-line-arguments)
  - [`$?` - Exit Status of the Last Command](#---exit-status-of-the-last-command)
  - [`$$` - Process ID of the Script](#---process-id-of-the-script)
  - [`$USER` - Current User](#user---current-user)
  - [`$HOME` - User's Home Directory](#home---users-home-directory)
  - [`$PWD` - Current Working Directory](#pwd---current-working-directory)
  - [`$OLDPWD` - Previous Working Directory](#oldpwd---previous-working-directory)
  - [`$HOSTNAME` - Hostname of the Machine](#hostname---hostname-of-the-machine)
  - [`$SHELL` - Current Shell](#shell---current-shell)
  - [`$PATH` - Colon-Separated List of Directories to Search for Commands](#path---colon-separated-list-of-directories-to-search-for-commands)
  - [`$EDITOR` - Default Editor](#editor---default-editor)
  - [`$TERM` - Terminal Type](#term---terminal-type)
  - [`$LANG` - Current Locale](#lang---current-locale)
  - [`$DISPLAY` - X Server Display Number](#display---x-server-display-number)
  - [`$SESSION` - Current Session Name](#session---current-session-name)
  - [`$HISTFILE` - History File](#histfile---history-file)
  - [`$TTY` - Controlling Terminal](#tty---controlling-terminal)
  - [`$UID` - User ID](#uid---user-id)
  - [`$EUID` - Effective User ID](#euid---effective-user-id)
  - [`$GROUPS` - Groups the User Belongs To](#groups---groups-the-user-belongs-to)
  - [`$RANDOM` - Random Number](#random---random-number)
  - [`$LINENO` - Current Line Number](#lineno---current-line-number)
  - [`$SECONDS` - Seconds Since the Script Started](#seconds---seconds-since-the-script-started)
  - [`$FUNCNAME` - Current Function Name](#funcname---current-function-name)
  - [`$COLUMNS` - Number of Columns in the Terminal](#columns---number-of-columns-in-the-terminal)
  - [`$LINES` - Number of Lines in the Terminal](#lines---number-of-lines-in-the-terminal)
  - [`$PIPESTATUS` - Array of Exit Statuses of Piped Commands](#pipestatus---array-of-exit-statuses-of-piped-commands)
  - [`$PPID` - Parent Process ID](#ppid---parent-process-id)
  - [`$BASH_VERSION` - Bash Version](#bash_version---bash-version)
  - [`$BASH_VERSINFO` - Bash Version Information](#bash_versinfo---bash-version-information)
  - [`$BASH_SOURCE` - Source Filename of the Script or Function Call](#bash_source---source-filename-of-the-script-or-function-call)
  - [`$BASH_COMMAND` - Command Being Executed](#bash_command---command-being-executed)
  - [`$BASH_LINENO` - Array of Line Numbers in a Function](#bash_lineno---array-of-line-numbers-in-a-function)
  - [`$BASH_REMATCH` - Array of Matched Patterns in a Regex](#bash_rematch---array-of-matched-patterns-in-a-regex)
  - [`$BASH_SUBSHELL` - Subshell Level](#bash_subshell---subshell-level)
  - [`$IFS` - Internal Field Separator](#ifs---internal-field-separator)
  - [`$PS1` - Primary Prompt String](#ps1---primary-prompt-string)
  - [`$PS2` - Secondary Prompt String](#ps2---secondary-prompt-string)
  - [`$PS3` - Select Prompt String](#ps3---select-prompt-string)
  - [`$PS4` - Debug Prompt String](#ps4---debug-prompt-string)

This document explains special shell variables, their use cases, and provides examples.

## `$0` - Script Name

- **Use Case**: Accessing the name of the currently executing script. Useful for logging, debugging, and displaying help messages.
- **Details**: This variable expands to the name of the shell script being executed. If the script is executed with a relative or absolute path, `$0` will contain that path.
- **Example**:

  ```bash
  #!/bin/bash
  echo "Script name: $0"
  ```

  If the script is named `test.sh` and executed as `./test.sh`, the output will be:

  ```text
  Script name: ./test.sh
  ```

## `$1`, `$2`, ... - Command-Line Arguments

- **Use Case**: Accessing arguments passed to the script from the command line.
- **Details**: These variables represent the arguments passed to the script, with `$1` being the first argument, `$2` the second, and so on.
- **Example**:

  ```bash
  #!/bin/bash
  echo "Argument 1: $1"
  echo "Argument 2: $2"
  ```

  If you run the script as `test.sh arg1 arg2`, the output will be:

  ```text
  Argument 1: arg1
  Argument 2: arg2
  ```

## `$#` - Number of Command-Line Arguments

- **Use Case**: Determining the number of arguments passed to the script. Useful for validating input.
- **Details**: This variable expands to the number of positional parameters (arguments) passed to the script.
- **Example**:

  ```bash
  #!/bin/bash
  echo "Number of arguments: $#"
  ```

  If you run the script as `test.sh arg1 arg2 arg3`, the output will be:

  ```text
  Number of arguments: 3
  ```

## `$@` - All Command-Line Arguments

- **Use Case**: Accessing all command-line arguments as a single string. Useful for passing arguments to another command.
- **Details**: This variable expands to all positional parameters (arguments), except `$0`. When quoted (`"$@"`), each parameter expands as a separate word.
- **Example**:

  ```bash
  #!/bin/bash
  echo "Arguments: $@"
  ```

  If you run the script as `test.sh arg1 arg2 arg3`, the output will be:

  ```text
  Arguments: arg1 arg2 arg3
  ```

## `$?` - Exit Status of the Last Command

- **Use Case**: Checking if the last command executed successfully. A value of `0` typically indicates success, while non-zero values indicate failure.
- **Details**: This variable expands to the exit status of the most recently executed foreground pipeline.
- **Example**:

  ```bash
  #!/bin/bash
  ls -l
  echo "Exit status of ls: $?"
  ```

  The output will show the exit status of the `ls -l` command.

## `$$` - Process ID of the Script

- **Use Case**: Getting the process ID of the current script. Useful for creating unique temporary files or logging.
- **Details**: This variable expands to the process ID of the current shell.
- **Example**:

  ```bash
  #!/bin/bash
  echo "Process ID: $$"
  ```

  The output will show the process ID of the script.

## `$USER` - Current User

- **Use Case**: Getting the username of the current user. Useful for user-specific configurations.
- **Details**: This variable expands to the username of the current user.
- **Example**:

  ```bash
  #!/bin/bash
  echo "Current user: $USER"
  ```

  The output will show the username of the current user.

## `$HOME` - User's Home Directory

- **Use Case**: Accessing the home directory of the current user. Useful for reading configuration files or storing data.
- **Details**: This variable expands to the absolute path of the current user's home directory.
- **Example**:

  ```bash
  #!/bin/bash
  echo "Home directory: $HOME"
  ```

  The output will show the home directory of the current user.

## `$PWD` - Current Working Directory

- **Use Case**: Getting the current working directory. Useful for navigating the file system.
- **Details**: This variable expands to the absolute path of the current working directory.
- **Example**:

  ```bash
  #!/bin/bash
  echo "Current working directory: $PWD"
  ```

  The output will show the current working directory.

## `$OLDPWD` - Previous Working Directory

- **Use Case**: Accessing the previous working directory. Useful for returning to the previous directory.
- **Details**: This variable expands to the previous working directory as set by the `cd` command.
- **Example**:

  ```bash
  #!/bin/bash
  cd /tmp
  echo "Current directory: $PWD"
  cd -
  echo "Previous directory: $PWD"
  ```

  The output will show the current and previous working directories.

## `$HOSTNAME` - Hostname of the Machine

- **Use Case**: Getting the hostname of the machine. Useful for identifying the machine in scripts.
- **Details**: This variable expands to the hostname of the current machine.
- **Example**:

  ```bash
  #!/bin/bash
  echo "Hostname: $HOSTNAME"
  ```

  The output will show the hostname of the machine.

## `$SHELL` - Current Shell

- **Use Case**: Getting the path to the current shell.
- **Details**: This variable expands to the path of the current shell.
- **Example**:

  ```bash
  #!/bin/bash
  echo "Current shell: $SHELL"
  ```

  The output will show the path to the current shell.

## `$PATH` - Colon-Separated List of Directories to Search for Commands

- **Use Case**: Displaying the directories where the system looks for executable commands.
- **Details**: This variable expands to a colon-separated list of directories that the shell searches for commands.
- **Example**:

  ```bash
  #!/bin/bash
  echo "PATH: $PATH"
  ```

  The output will show the list of directories in the PATH variable.

## `$EDITOR` - Default Editor

- **Use Case**: Getting the default text editor.
- **Details**: This variable expands to the default text editor set in the environment.
- **Example**:

  ```bash
  #!/bin/bash
  echo "Default editor: $EDITOR"
  ```

  The output will show the default editor.

## `$TERM` - Terminal Type

- **Use Case**: Getting the terminal type.
- **Details**: This variable expands to the terminal type.
- **Example**:

  ```bash
  #!/bin/bash
  echo "Terminal type: $TERM"
  ```

  The output will show the terminal type.

## `$LANG` - Current Locale

- **Use Case**: Getting the current locale settings.
- **Details**: This variable expands to the current locale settings.
- **Example**:

  ```bash
  #!/bin/bash
  echo "Current locale: $LANG"
  ```

  The output will show the current locale.

## `$DISPLAY` - X Server Display Number

- **Use Case**: Getting the X server display number (used in GUI environments).
- **Details**: This variable expands to the X server display number, used for graphical applications.
- **Example**:

  ```bash
  #!/bin/bash
  echo "X server display: $DISPLAY"
  ```

  The output will show the X server display number.

## `$SESSION` - Current Session Name

- **Use Case**: Getting the current session name.
- **Details**: This variable expands to the current session name.
- **Example**:

  ```bash
  #!/bin/bash
  echo "Current session: $SESSION"
  ```

  The output will show the current session name.

## `$HISTFILE` - History File

- **Use Case**: Getting the path to the history file.
- **Details**: This variable expands to the path of the history file where shell commands are stored.
- **Example**:

  ```bash
  #!/bin/bash
  echo "History file: $HISTFILE"
  ```

  The output will show the path to the history file.

## `$TTY` - Controlling Terminal

- **Use Case**: Getting the name of the controlling terminal.
- **Details**: This variable expands to the name of the controlling terminal.
- **Example**:

  ```bash
  #!/bin/bash
  echo "Controlling terminal: $TTY"
  ```

  The output will show the controlling terminal.

## `$UID` - User ID

- **Use Case**: Getting the user ID.
- **Details**: This variable expands to the user ID of the current user.
- **Example**:

  ```bash
  #!/bin/bash
  echo "User ID: $UID"
  ```

  The output will show the user ID.

## `$EUID` - Effective User ID

- **Use Case**: Getting the effective user ID.
- **Details**: This variable expands to the effective user ID.
- **Example**:

  ```bash
  #!/bin/bash
  echo "Effective user ID: $EUID"
  ```

  The output will show the effective user ID.

## `$GROUPS` - Groups the User Belongs To

- **Use Case**: Listing the groups the user belongs to.
- **Details**: This variable expands to the groups the user belongs to.
- **Example**:

  ```bash
  #!/bin/bash
  echo "Groups: $GROUPS"
  ```

  The output will show the groups the user belongs to.

## `$RANDOM` - Random Number

- **Use Case**: Generating a random number.
- **Details**: This variable expands to a random integer between 0 and 32767.
- **Example**:

  ```bash
  #!/bin/bash
  echo "Random number: $RANDOM"
  ```

  The output will show a random number.

## `$LINENO` - Current Line Number

- **Use Case**: Getting the current line number in the script.
- **Details**: This variable expands to the current line number in the script.
- **Example**:

  ```bash
  #!/bin/bash
  echo "Current line number: $LINENO"
  ```

  The output will show the current line number.

## `$SECONDS` - Seconds Since the Script Started

- **Use Case**: Measuring the execution time of a script.
- **Details**: This variable expands to the number of seconds since the script started.
- **Example**:

  ```bash
  #!/bin/bash
  echo "Seconds since start: $SECONDS"
  sleep 2
  echo "Seconds since start: $SECONDS"
  ```

  The output will show the number of seconds since the script started.

## `$FUNCNAME` - Current Function Name

- **Use Case**: Getting the name of the current function.
- **Details**: This variable expands to the name of the current function.
- **Example**:

  ```bash
  #!/bin/bash
  my_function() {
      echo "Function name: ${FUNCNAME[0]}"
  }
  my_function
  ```

  The output will show the name of the function.

## `$COLUMNS` - Number of Columns in the Terminal

- **Use Case**: Getting the number of columns in the terminal.
- **Details**: This variable expands to the number of columns in the terminal.
- **Example**:

  ```bash
  #!/bin/bash
  echo "Columns: $COLUMNS"
  ```

  The output will show the number of columns in the terminal.

## `$LINES` - Number of Lines in the Terminal

- **Use Case**: Getting the number of lines in the terminal.
- **Details**: This variable expands to the number of lines in the terminal.
- **Example**:

  ```bash
  #!/bin/bash
  echo "Lines: $LINES"
  ```

  The output will show the number of lines in the terminal.

## `$PIPESTATUS` - Array of Exit Statuses of Piped Commands

- **Use Case**: Getting the exit statuses of piped commands.
- **Details**: This variable expands to an array of exit statuses from the processes in a pipeline.
- **Example**:

  ```bash
  #!/bin/bash
  ls | grep non_existent_file
  echo "Exit status of ls: ${PIPESTATUS[0]}"
  echo "Exit status of grep: ${PIPESTATUS[1]}"
  ```

  The output will show the exit statuses of the `ls` and `grep` commands.

## `$PPID` - Parent Process ID

- **Use Case**: Getting the parent process ID.
- **Details**: This variable expands to the process ID of the parent process.
- **Example**:

  ```bash
  #!/bin/bash
  echo "Parent process ID: $PPID"
  ```

  The output will show the parent process ID.

## `$BASH_VERSION` - Bash Version

- **Use Case**: Getting the Bash version.
- **Details**: This variable expands to the version of Bash.
- **Example**:

  ```bash
  #!/bin/bash
  echo "Bash version: $BASH_VERSION"
  ```

  The output will show the Bash version.

## `$BASH_VERSINFO` - Bash Version Information

- **Use Case**: Getting detailed Bash version information.
- **Details**: This variable expands to an array containing version information for Bash.
- **Example**:

  ```bash
  #!/bin/bash
  echo "Bash version info: ${BASH_VERSINFO[@]}"
  ```

  The output will show detailed Bash version information.

## `$BASH_SOURCE` - Source Filename of the Script or Function Call

- **Use Case**: Getting the source filename.
- **Details**: This variable expands to the source filename of the script or function call.
- **Example**:

  ```bash
  #!/bin/bash
  echo "Bash source: ${BASH_SOURCE[0]}"
  ```

  The output will show the source filename.

## `$BASH_COMMAND` - Command Being Executed

- **Use Case**: Getting the command being executed.
- **Details**: This variable expands to the command currently being executed.
- **Example**:

  ```bash
  #!/bin/bash
  echo "Bash command: $BASH_COMMAND"
  ```

  The output will show the command being executed.

## `$BASH_LINENO` - Array of Line Numbers in a Function

- **Use Case**: Getting the line numbers in a function.
- **Details**: This variable expands to an array of line numbers in a function.
- **Example**:

  ```bash
  #!/bin/bash
  my_function() {
      echo "Line number: ${BASH_LINENO[0]}"
  }
  my_function
  ```

  The output will show the line number in the function.

## `$BASH_REMATCH` - Array of Matched Patterns in a Regex

- **Use Case**: Getting the matched patterns in a regex.
- **Details**: This variable expands to an array of matched patterns in a regular expression.
- **Example**:

  ```bash
  #!/bin/bash
  string="hello world"
  if [[ $string =~ (hello) ]]; then
      echo "Match: ${BASH_REMATCH[1]}"
  fi
  ```

  The output will show the matched pattern.

## `$BASH_SUBSHELL` - Subshell Level

- **Use Case**: Getting the subshell level.
- **Details**: This variable expands to the subshell level.
- **Example**:

  ```bash
  #!/bin/bash
  echo "Subshell level: $BASH_SUBSHELL"
  (echo "Subshell level: $BASH_SUBSHELL")
  ```

  The output will show the subshell level.

## `$IFS` - Internal Field Separator

- **Use Case**: Getting the internal field separator.
- **Details**: This variable expands to the internal field separator used for word splitting after expansion and to split lines into words with the `read` builtin command.
- **Example**:

  ```bash
  #!/bin/bash
  echo "IFS: '$IFS'"
  ```

  The output will show the internal field separator.

## `$PS1` - Primary Prompt String

- **Use Case**: Getting the primary prompt string.
- **Details**: This variable expands to the primary prompt string, which is displayed when the shell is ready to read a command.
- **Example**:

  ```bash
  #!/bin/bash
  echo "PS1: $PS1"
  ```

  The output will show the primary prompt string.

## `$PS2` - Secondary Prompt String

- **Use Case**: Getting the secondary prompt string.
- **Details**: This variable expands to the secondary prompt string, which is displayed when the shell expects more input to complete a command.
- **Example**:

  ```bash
  #!/bin/bash
  echo "PS2: $PS2"
  ```

  The output will show the secondary prompt string.

## `$PS3` - Select Prompt String

- **Use Case**: Getting the select prompt string.
- **Details**: This variable expands to the prompt string used by the `select` command.
- **Example**:

  ```bash
  #!/bin/bash
  PS3="Choose an option: "
  select option in "Option 1" "Option 2"; do
      echo "You chose: $option"
      break
  done
  ```

  The output will show the select prompt string.

## `$PS4` - Debug Prompt String

- **Use Case**: Getting the debug prompt string.
- **Details**: This variable expands to the debug prompt string, which is displayed when the `-x` option is enabled for debugging.
- **Example**:

  ```bash
  #!/bin/bash
  PS4='+(${BASH_SOURCE}:${LINENO}): ${FUNCNAME[0]:+${FUNCNAME[0]}(): }'
  set -x
  my_function() {
      echo "Hello"
  }
  my_function
  ```

  The output will show the debug prompt string.
