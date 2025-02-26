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
    - [Case Statements](#case-statements)
    - [Test Operators](#test-operators)
      - [Expression Operators](#expression-operators)
      - [String Operators](#string-operators)
      - [Integer Comparison Operators](#integer-comparison-operators)
      - [File Test Operators](#file-test-operators)
  - [Functions](#functions)
  - [Arrays](#arrays)
  - [Arithmetic and Command Substitution](#arithmetic-and-command-substitution)
  - [Input/Output Processing](#inputoutput-processing)
  - [String Manipulation](#string-manipulation)
  - [Error Handling and Debugging](#error-handling-and-debugging)
  - [Process Management](#process-management)
  - [Regular Expressions](#regular-expressions)
  - [Best Practices](#best-practices)
  - [Practical Examples](#practical-examples)
  - [Conclusion](#conclusion)
  - [Cron Jobs](#cron-jobs)
  - [SSH Guide](#ssh-guide)

## Introduction

Bash (Bourne Again SHell) is a powerful Unix shell and command language that emerged as the enhanced replacement for the original Bourne Shell (sh). Released in 1989 as part of the GNU Project, Bash has become the default shell for most Linux distributions and macOS (until Catalina).

Bash serves dual purposes:

- **Interactive Command Interpreter**: Providing a command-line interface to interact with the operating system
- **Scripting Language**: Enabling automation of repetitive tasks, system administration, and complex workflows

**Why Learn Bash?**

- Ubiquitous presence across Unix/Linux systems
- Essential for system administration and DevOps
- Powerful tool for automation and rapid prototyping
- Requires no additional dependencies - it's built into most systems

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

**Script Structure Best Practices:**

```bash
#!/bin/bash
#
# Script Name: example.sh
# Description: Brief description of what this script does
# Author: Your Name <your.email@example.com>
# Date Created: YYYY-MM-DD
# Last Modified: YYYY-MM-DD
#
# Usage: ./example.sh [options] [arguments]
#
# Dependencies: List any dependencies here (commands, packages)
#

# Exit on error
set -e

# Define constants and configuration variables
CONFIG_FILE="/path/to/config"
MAX_RETRIES=5

# Define functions
function cleanup() {
    # Clean up temporary files or perform other cleanup tasks
    echo "Cleaning up..."
}

# Set trap to call cleanup function on exit
trap cleanup EXIT

# Main script logic begins here
echo "Script started"

# Your script code goes here

echo "Script completed successfully"
exit 0
```

**Running Scripts:**

```bash
# Direct execution (requires executable permission)
./myscript.sh

# Using bash explicitly (doesn't require executable permission)
bash myscript.sh

# With specific arguments
./myscript.sh arg1 arg2

# Run in debug mode
bash -x myscript.sh
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

**Variable Types and Scope:**

```bash
# Local variables - only available within the current shell session
local_var="I'm local"

# Environment variables - available to child processes
export GLOBAL_VAR="I'm global"

# Constants - by convention, use uppercase (bash doesn't enforce immutability)
readonly PI=3.14159

# Function-scoped local variables
function example() {
    local inside_var="Only visible inside the function"
    echo "$inside_var"
}
```

**Variable Operations:**

```bash
# Default values
echo "${name:-default}"   # Use default if name is unset or null
echo "${name:=default}"   # Assign default if name is unset or null

# Parameter length
echo "${#name}"           # Prints the length of the variable

# Substring extraction
echo "${name:0:3}"        # Extracts first 3 characters

# Pattern substitution
echo "${name/i/X}"        # Replace first 'i' with 'X'
echo "${name//i/X}"       # Replace all 'i' with 'X'

# Case modification
echo "${name^}"           # First letter uppercase
echo "${name^^}"          # All letters uppercase
echo "${name,}"           # First letter lowercase
echo "${name,,}"          # All letters lowercase
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

**Advanced Conditionals:**

```bash
# Using double brackets for enhanced features
if [[ "$string" =~ ^[0-9]+$ ]]; then
    echo "String is a number"
fi

# Compound conditions
if [ "$age" -gt 18 ] && [ "$has_id" = true ]; then
    echo "Access granted"
fi

# One-liner conditional (ternary-like operation)
[ "$count" -eq 0 ] && echo "Count is zero" || echo "Count is not zero"

# Testing exit status of commands
if grep -q "pattern" file.txt; then
    echo "Pattern found"
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

**Advanced For Loop Examples:**

```bash
# C-style for loop
for ((i=1; i<=5; i++)); do
    echo "Counter: $i"
done

# Iterating over command output
for user in $(cut -d: -f1 /etc/passwd); do
    echo "User: $user"
done

# Iterating with specific increments
for i in {0..20..5}; do  # From 0 to 20 in steps of 5
    echo "Value: $i"
done

# Breaking and continuing
for file in *.txt; do
    [ -f "$file" ] || continue  # Skip if not a file
    [ -s "$file" ] || break     # Stop if empty file encountered
    echo "Processing $file..."
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

**Additional While Loop Examples:**

```bash
# Reading file line by line
while IFS= read -r line; do
    echo "Line: $line"
done < input.txt

# Until loop (opposite of while - runs until condition becomes true)
count=5
until [ $count -eq 0 ]; do
    echo "Countdown: $count"
    ((count--))
done

# Infinite loop with manual break
while true; do
    read -p "Enter 'q' to quit: " input
    [ "$input" = "q" ] && break
    echo "You entered: $input"
done
```

### Case Statements

Case statements provide a cleaner alternative to multiple if-elif statements:

```bash
case "$fruit" in
    "apple")
        echo "It's an apple."
        ;;
    "banana"|"plantain")  # Multiple matches
        echo "It's a banana or plantain."
        ;;
    "orange")
        echo "It's an orange."
        ;;
    *)  # Default case
        echo "Unknown fruit."
        ;;
esac
```

**Pattern Matching in Case:**

```bash
case "$filename" in
    *.jpg|*.jpeg)
        echo "JPEG image"
        ;;
    *.png)
        echo "PNG image"
        ;;
    *.txt)
        echo "Text file"
        ;;
    *)
        echo "Unknown file type"
        ;;
esac
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

**Advanced Function Techniques:**

```bash
# Return values (using exit status)
function is_even() {
    if (( $1 % 2 == 0 )); then
        return 0  # Success (true in bash)
    else
        return 1  # Failure (false in bash)
    fi
}

# Using the return value
if is_even 4; then
    echo "4 is even"
fi

# Functions that output values
function get_sum() {
    echo $(( $1 + $2 ))
}

# Capture the output
result=$(get_sum 5 3)
echo "Sum: $result"

# Functions with default parameters
function greet() {
    local name="${1:-World}"  # Default to "World" if no argument provided
    echo "Hello, $name!"
}

# Recursive functions
function factorial() {
    if [ $1 -le 1 ]; then
        echo 1
    else
        local sub_result=$(factorial $(( $1 - 1 )))
        echo $(( $1 * sub_result ))
    fi
}

echo "5! = $(factorial 5)"
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

**Advanced Array Operations:**

```bash
# Associative arrays (dictionaries/maps - requires Bash 4+)
declare -A user_info
user_info[name]="John"
user_info[age]=30
user_info[city]="New York"

# Accessing associative arrays
echo "Name: ${user_info[name]}"
echo "Age: ${user_info[age]}"

# Array length
echo "Number of fruits: ${#fruits[@]}"

# Array indices
echo "Indices of fruits array: ${!fruits[@]}"

# Adding elements
fruits+=("orange" "grape")

# Slicing arrays
echo "First two fruits: ${fruits[@]:0:2}"

# Removing elements (unset)
unset 'fruits[1]'

# Copying arrays
new_fruits=("${fruits[@]}")

# Filtering arrays
for fruit in "${fruits[@]}"; do
    [[ "$fruit" == *"a"* ]] && filtered_fruits+=("$fruit")
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

**Additional Arithmetic Examples:**

```bash
# Arithmetic expansion
echo $((10 + 5))          # Addition
echo $((10 - 5))          # Subtraction
echo $((10 * 5))          # Multiplication
echo $((10 / 5))          # Division
echo $((10 % 3))          # Modulo
echo $((2 ** 3))          # Exponentiation

# Increment/decrement
count=0
((count++))              # Increment
((count--))              # Decrement

# Compound assignments
((count += 5))           # Add 5 to count
((count *= 2))           # Multiply count by 2

# bc for floating-point arithmetic
result=$(echo "scale=2; 10 / 3" | bc)
echo "10 / 3 = $result"

# Advanced command substitution
kernel_version=$(uname -r)
total_files=$(find . -type f | wc -l)
uptime_days=$(uptime | awk '{print $3}')

# Process substitution
diff <(ls dir1) <(ls dir2)
```

## Input/Output Processing

Bash provides powerful tools for handling input and output streams:

```bash
# Redirecting output to a file
echo "Hello, World!" > output.txt      # Overwrite
echo "Another line" >> output.txt      # Append

# Redirecting error output
command 2> error.log
command > output.txt 2> error.log      # Separate files
command > output.txt 2>&1              # Both to same file

# Here documents
cat << EOF > config.txt
This is a multi-line
text block that will
be written to config.txt
EOF

# Here strings
grep "pattern" <<< "Text to search in"

# Process substitution
diff <(sort file1.txt) <(sort file2.txt)

# Reading user input
read -p "Enter your name: " user_name
echo "Hello, $user_name!"

# Reading with timeout and default
read -t 5 -p "Enter value (default: 10): " value
value=${value:-10}

# Reading password (no echo)
read -s -p "Password: " password
```

## String Manipulation

Bash provides various ways to manipulate strings:

```bash
text="Hello, World!"

# String length
echo "Length: ${#text}"

# Substring extraction
echo "First 5 chars: ${text:0:5}"
echo "From 7th char: ${text:7}"

# Case modification
echo "Uppercase: ${text^^}"
echo "Lowercase: ${text,,}"

# String replacement
echo "${text/World/Universe}"         # Replace first occurrence
echo "${text//l/L}"                   # Replace all occurrences

# Trim (using parameter substitution)
text="  trim me  "
echo "Trimmed: ${text## }"            # Trim leading spaces
echo "Trimmed: ${text%% }"            # Trim trailing spaces

# Check if string contains substring
if [[ "$text" == *"World"* ]]; then
    echo "Contains 'World'"
fi

# Split string into array
IFS=',' read -ra parts <<< "apple,banana,cherry"
for part in "${parts[@]}"; do
    echo "Part: $part"
done
```

## Error Handling and Debugging

Robust scripts need proper error handling:

```bash
# Exit on error
set -e           # Exit immediately if a command exits with non-zero status
set -u           # Exit if an unset variable is used
set -o pipefail  # Return value is the value of the last command to exit with non-zero status

# Error handling function
handle_error() {
    local line=$1
    local command=$2
    local code=$3
    echo "Error on line $line: Command '$command' exited with status $code"
    # Cleanup actions
    exit $code
}

# Set error trap
trap 'handle_error ${LINENO} "$BASH_COMMAND" $?' ERR

# Debugging
set -x  # Print each command before executing (verbose mode)
set +x  # Turn off tracing

# Conditional debugging
if [ "$DEBUG" = true ]; then
    set -x
fi

# Logging function
log() {
    local level=$1
    shift
    echo "[$(date +'%Y-%m-%d %H:%M:%S')] [$level] $*" >&2
}

log INFO "Script started"
log ERROR "Something went wrong"

# Running in debug mode from command line
# bash -x script.sh
```

## Process Management

Working with processes in bash:

```bash
# Background processes
long_running_command &
pid=$!  # Store PID of last background process

# Check if process is still running
if ps -p $pid > /dev/null; then
    echo "Process $pid is running"
fi

# Wait for background process
wait $pid

# Exit status of last command
if [ $? -eq 0 ]; then
    echo "Command succeeded"
else
    echo "Command failed"
fi

# Kill a process
kill $pid
kill -9 $pid  # Force kill

# Run multiple processes and wait for all to complete
process1 &
process2 &
wait

# Timeout command (abort if running too long)
timeout 5s command_that_might_hang

# Running at lower priority
nice -n 19 resource_intensive_task &
```

## Regular Expressions

Bash supports powerful regex matching:

```bash
# Using =~ operator with [[ ]]
string="The year is 2023"
if [[ $string =~ [0-9]{4} ]]; then
    echo "Found a 4-digit number: ${BASH_REMATCH[0]}"
fi

# Common regex patterns
email_regex='^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}$'
ip_regex='^([0-9]{1,3}\.){3}[0-9]{1,3}$'
date_regex='^[0-9]{4}-[0-9]{2}-[0-9]{2}$'

# Validate email
email="user@example.com"
if [[ $email =~ $email_regex ]]; then
    echo "Valid email"
fi

# Using grep with regex
grep -E '^[0-9]{3}-[0-9]{2}-[0-9]{4}$' data.txt  # Find SSN pattern
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

**Additional Best Practices:**

1. **Always Use Version Control**

   - Keep your scripts in a Git repository
   - Include meaningful commit messages

2. **Error Handling**

   - Set appropriate error traps
   - Consider failing conditions

   ```bash
   set -euo pipefail
   trap 'echo "Error at line $LINENO"; exit 1' ERR
   ```

3. **Input Validation**

   - Verify command line arguments
   - Check file existence before using

   ```bash
   [[ -f "$file" ]] || { echo "File not found: $file"; exit 1; }
   ```

4. **Documentation**

   - Include usage instructions in script headers
   - Document complex functions and algorithms
   - Add example usage

5. **Security Considerations**

   - Never hardcode sensitive data
   - Use restricted file permissions
   - Validate and sanitize user input

   ```bash
   chmod 700 myscript.sh  # Only owner can read/write/execute
   ```

6. **Idempotency**

   - Design scripts to be safely run multiple times
   - Check if operations have already been performed

7. **Modularization**

   - Split large scripts into functions or separate scripts
   - Use source/include for common functions

   ```bash
   source lib/common_functions.sh
   ```

8. **Progressive Enhancement**

   - Add features gradually as they become necessary
   - Keep scripts as simple as possible

9. **Testing**

   - Test scripts regularly, especially after changes
   - Consider automated testing frameworks like BATS

10. **Logging**
    - Include proper logging for debugging
    - Consider different log levels

## Practical Examples

Here are some practical examples of Bash scripts for common tasks:

**1. System Backup Script:**

```bash
#!/bin/bash
# Simple backup script

# Configuration
backup_dir="/backup/$(date +%Y%m%d)"
source_dirs=("/etc" "/home" "/var/www")
log_file="/var/log/backup.log"

# Create backup directory
mkdir -p "$backup_dir" || { echo "Failed to create backup dir"; exit 1; }

# Log function
log() {
    echo "$(date +"%Y-%m-%d %H:%M:%S") - $1" >> "$log_file"
    echo "$1"
}

log "Starting backup..."

# Perform backup
for dir in "${source_dirs[@]}"; do
    if [ -d "$dir" ]; then
        log "Backing up $dir"
        tar -czf "$backup_dir/$(basename "$dir").tar.gz" "$dir" 2>> "$log_file"
        if [ $? -eq 0 ]; then
            log "Successfully backed up $dir"
        else
            log "Failed to back up $dir"
        fi
    else
        log "Directory $dir does not exist, skipping"
    fi
done

log "Backup completed"
```

**2. Monitoring Script:**

```bash
#!/bin/bash
# Simple system monitoring script

threshold_cpu=80
threshold_mem=80
threshold_disk=85
alert_email="admin@example.com"

# Check CPU usage
cpu_usage=$(top -bn1 | grep "Cpu(s)" | awk '{print $2 + $4}' | cut -d. -f1)
if [ "$cpu_usage" -gt "$threshold_cpu" ]; then
    echo "ALERT: CPU usage at $cpu_usage%" | mail -s "High CPU Alert" "$alert_email"
fi

# Check memory usage
mem_usage=$(free | grep Mem | awk '{print int($3/$2 * 100)}')
if [ "$mem_usage" -gt "$threshold_mem" ]; then
    echo "ALERT: Memory usage at $mem_usage%" | mail -s "High Memory Alert" "$alert_email"
fi

# Check disk usage
disk_usage=$(df -h / | grep / | awk '{print $(NF-1)}' | sed 's/%//')
if [ "$disk_usage" -gt "$threshold_disk" ]; then
    echo "ALERT: Disk usage at $disk_usage%" | mail -s "High Disk Usage Alert" "$alert_email"
fi
```

**3. Log Parser:**

```bash
#!/bin/bash
# Simple log parser for Apache logs

log_file="/var/log/apache2/access.log"

# Count HTTP status codes
echo "HTTP status code distribution:"
grep -o ' [0-9]\{3\} ' "$log_file" | sort | uniq -c | sort -rn

# Find top 10 IP addresses
echo -e "\nTop 10 IP addresses:"
grep -o '^[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}' "$log_file" | sort | uniq -c | sort -rn | head -10

# Find top 10 requested URLs
echo -e "\nTop 10 requested URLs:"
grep -o '"GET [^ ]*' "$log_file" | sed 's/"GET //' | sort | uniq -c | sort -rn | head -10

# Count requests per hour
echo -e "\nRequests per hour:"
grep -o '[0-9]\{2\}/[A-Z][a-z]\{2\}/[0-9]\{4\}:[0-9]\{2\}' "$log_file" | sort | uniq -c
```

## Conclusion

This guide covered the foundations of Bash scripting—from variables and control structures to functions, arrays, arithmetic, and best practices. With these essentials, you can create scripts to automate tasks and manage systems efficiently.

Bash scripting is a powerful skill that allows you to automate repetitive tasks, manage system configurations, and build complex workflows. As you continue to develop your scripts, remember that readability and maintainability are as important as functionality. Use version control, write documentation, and follow the best practices outlined in this guide to create robust and reliable scripts.

For further learning, explore:

- Advanced text processing with awk and sed
- Network scripting with curl and wget
- Creating interactive scripts with dialog
- Integration with other programming languages

Happy scripting!

## Cron Jobs

Cron jobs allow you to schedule tasks to run automatically at specific intervals. [Learn more](./cron_jobs.md).

## SSH Guide

Learn how to use SSH for secure remote connections, including key generation, authentication, file transfers, and more. [Explore the SSH Guide](./ssh_guide.md).
