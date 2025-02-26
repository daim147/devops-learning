# Bash Scripting Guide

Welcome to this comprehensive Bash scripting guide. Explore essential concepts, syntax, and best practices to write effective scripts on Linux and Unix systems. Documentation is available in [Bash Reference Manual](https://www.gnu.org/software/bash/manual/bash.html).

## Table of Contents

- [Bash Scripting Guide](#bash-scripting-guide)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Getting Started](#getting-started)
  - [Variables](#variables)
    - [Command-Line Arguments](#command-line-arguments)
    - [Environment Variables](#environment-variables)
    - [Special Variables](#special-variables)
  - [Control Structures](#control-structures)
    - [Conditional Statements](#conditional-statements)
    - [Loops](#loops)
      - [For Loop](#for-loop)
      - [While Loop](#while-loop)
    - [Test Operators](#test-operators)
      - [Expression Operators](#expression-operators)
      - [String Operators](#string-operators)
      - [Integer Comparison Operators](#integer-comparison-operators)
      - [File Test Operators](#file-test-operators)
  - [Functions](#functions)
  - [Arrays](#arrays)
  - [Arithmetic and Command Substitution](#arithmetic-and-command-substitution)
  - [Best Practices](#best-practices)
  - [Cron Jobs](#cron-jobs)
  - [Conclusion](#conclusion)

## Introduction

Bash is a powerful Unix shell and command language. It not only serves as an interactive shell but also as a scripting language to automate tasks and system operations.

## Getting Started

Create a new Bash script file with a `.sh` extension and make it executable:

```bash
# Create and open a script file
vim myscript.sh

# Make it executable using chmod to give the user permission to execute the script
chmod +x myscript.sh

# Add the shebang at the top it makes the script executable /bin/bash is the path to the bash interpreter that will be used to run the script and #! is the shebang character sequence that tells the system that the file is a script and should be interpreted by the specified program
echo "#!/bin/bash" > myscript.sh


```

## Variables

Variables store data values. Quote variables to avoid unexpected word splitting.

```bash
# Define variables
name="Alice"
age=30

# Use variables
echo "Name: $name, Age: $age"
```

### Command-Line Arguments

Access command-line arguments passed to the script.

```bash
# Access command-line arguments
echo "Script name: $0"
echo "First argument: $1"
echo "Second argument: $2"
```

Pass arguments when running the script:

```bash
./myscript.sh arg1 arg2
```

### Environment Variables

Access environment variables available to the script.

```bash
# Access environment variables
echo "Home directory: $HOME" # User's home directory
echo "User: $USER" # Current user
echo "Path: $PATH" # Colon-separated list of directories to search for commands
```

You can also set custom environment variables:

```bash
# Set environment variables
export MY_VAR="Hello, World"
echo "Custom variable: $MY_VAR"
```

Remove environment variables:

```bash
# Remove environment variables
unset MY_VAR
```

More environment variables are available on your system. Use `printenv` to list all environment variables.

```bash
printenv
```

### Special Variables

Special variables provide additional information about the script and its execution.

- `$0`: Script name
- `$1`, `$2`, ...: Command-line arguments
- `$#`: Number of command-line arguments
- `$@`: All command-line arguments
- `$?`: Exit status of the last command
- `$$`: Process ID of the script
- `$USER`: Current user
- `$HOME`: User's home directory
- `$PWD`: Current working directory

More special variables are available. [Learn more](./shell_special_variable.md).
[Bash Variables](https://www.gnu.org/software/bash/manual/html_node/Bash-Variables.html). [Positional Parameters](https://www.gnu.org/software/bash/manual/html_node/Positional-Parameters.html). [Shell Variables](https://www.gnu.org/software/bash/manual/html_node/Shell-Variables.html). [Shell Parameters](https://www.gnu.org/software/bash/manual/html_node/Shell-Parameters.html). [Special Parameters](https://www.gnu.org/software/bash/manual/html_node/Special-Parameters.html).

## Control Structures

### Conditional Statements

Use `if`, `elif`, and `else` to execute commands based on conditions.

```bash
if [ "$name" == "Alice" ]; then
    echo "Hello, Alice!"
elif [ "$name" == "Bob" ]; then
    echo "Hi, Bob!"
else
    echo "Greetings!"
fi
```

### Loops

#### For Loop

Iterate over a sequence or list.

```bash
for i in {1..5}; do
    echo "Iteration: $i"
done
```

#### While Loop

Repeat commands while a condition is true.

```bash
count=0
while [ $count -lt 5 ]; do
    echo "Count: $count"
    count=$((count + 1))
done
```

### Test Operators

Bash provides various test operators for use in conditional statements. Here are the commonly used operators:

#### Expression Operators

| Operator       | Description             |
| -------------- | ----------------------- |
| `! EXPRESSION` | The EXPRESSION is false |

#### String Operators

| Operator             | Description                                      |
| -------------------- | ------------------------------------------------ |
| `-n STRING`          | The length of STRING is greater than zero        |
| `-z STRING`          | The length of STRING is zero (i.e., it is empty) |
| `STRING1 = STRING2`  | STRING1 is equal to STRING2                      |
| `STRING1 != STRING2` | STRING1 is not equal to STRING2                  |

#### Integer Comparison Operators

| Operator                | Description                                   |
| ----------------------- | --------------------------------------------- |
| `INTEGER1 -eq INTEGER2` | INTEGER1 is numerically equal to INTEGER2     |
| `INTEGER1 -gt INTEGER2` | INTEGER1 is numerically greater than INTEGER2 |
| `INTEGER1 -lt INTEGER2` | INTEGER1 is numerically less than INTEGER2    |

#### File Test Operators

| Operator  | Description                                       |
| --------- | ------------------------------------------------- |
| `-d FILE` | FILE exists and is a directory                    |
| `-e FILE` | FILE exists                                       |
| `-r FILE` | FILE exists and the read permission is granted    |
| `-s FILE` | FILE exists and its size is greater than zero     |
| `-w FILE` | FILE exists and the write permission is granted   |
| `-x FILE` | FILE exists and the execute permission is granted |

## Functions

Functions modularize your code and help with code reuse.

```bash
function greet {
    local person=$1
    echo "Hello, $person!"
}

# Call the function
greet "Alice"
```

## Arrays

Arrays hold multiple values and enhance data management.

```bash
# Declare an array
fruits=("apple" "banana" "cherry")

# Iterate over the array
for fruit in "${fruits[@]}"; do
    echo "Fruit: $fruit"
done
```

## Arithmetic and Command Substitution

Perform arithmetic and capture command output.

```bash
# Arithmetic expression
result=$((5 + 3))
echo "Result: $result"

# Command substitution
current_date=$(date)
echo "Today's date: $current_date"
```

## Best Practices

- Always quote your variables.
- Start scripts with a shebang: `#!/bin/bash`
- Use `set -e` to exit immediately on errors.
- Comment your code for clarity.
- Use tools like ShellCheck to lint your scripts.

```bash
#!/bin/bash
set -e  # Exit on errors

# Your script logic goes here...
```

## Cron Jobs

Cron jobs allow you to schedule tasks to run automatically at specific intervals. [Learn more](./cron_jobs.md).

## Conclusion

This guide covered the foundations of Bash scripting—from variables and control structures to functions, arrays, arithmetic, and best practices. With these essentials, you can create scripts to automate tasks and manage systems efficiently.

Happy scripting!
