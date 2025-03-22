
Introduction to Bash Scripting


Hey guys, Newton here! 👋

Today, we’re diving into Bash Scripting—the backbone of automation and system management in Linux/Unix environments. Whether you’re a developer, sysadmin, or just a tech enthusiast, mastering Bash scripting will save you time, reduce repetitive tasks, and unlock the true power of the command line. Let’s break it down step by step!

—

What is Bash?
Bash (Bourne Again SHell) is a command-line interpreter and scripting language. It’s the default shell on most Linux distributions and macOS (though macOS is moving to Zsh). Bash allows you to execute commands, automate workflows, and even build complex programs using simple scripts.

—

Why Learn Bash Scripting?
Automate the boring stuff: Schedule backups, clean up files, or deploy code.
System management: Monitor resources, manage users, or configure servers.
Portability: Bash scripts run on almost any Unix-like system.
Foundation for DevOps: Tools like Docker, Kubernetes, and CI/CD pipelines rely on shell scripting.
—

Getting Started: Your First Script
Let’s create a simple “Hello World” script.

Create a file:
Open a terminal and type:

   nano hello.sh
Add the shebang line:
The #!/bin/bash (shebang) tells the system to use Bash to execute the script.

   #!/bin/bash
   echo "Hello World!"
Make it executable:

   chmod +x hello.sh
Run the script:

   ./hello.sh  # Output: Hello World!
—

Bash Scripting Basics
1. Variables
Variables store data. No data types—everything is a string (unless you enforce arithmetic).

name="Newton"  
age=20  
echo "Hey, I'm $name and I’m $age years old."
Note: No spaces around = in assignments!
2. Comments
Use # for single-line comments:

# This is a comment
3. Input/Output
Printing: echo "Text" or printf "Formatted Text"

Reading input:

  echo "What's your name?"
  read username
  echo "Hello, $username!"
—

Control Structures
1. Conditionals (if/else)
Check conditions using if, elif, and else:

if [ $age -gt 18 ]; then
  echo "You’re an adult."
elif [ $age -eq 18 ]; then
  echo "Welcome to adulthood!"
else
  echo "You’re a minor."
fi
Comparison Operators:

-eq: Equal
-ne: Not equal
-gt: Greater than
-lt: Less than
-z "string": Check if string is empty
2. Case Statements
Simplify multiple conditions:

case $day in
  "Mon") echo "Monday Blues!" ;;
  "Fri") echo "TGIF!" ;;
  *)     echo "It’s $day. Keep going!" ;;
esac
3. Loops
For Loop:

  for i in {1..5}; do
    echo "Count: $i"
  done
While Loop:

  count=1
  while [ $count -le 5 ]; do
    echo "Count: $count"
    ((count++))
  done
Until Loop:
Runs until a condition becomes true.

  until [ $count -gt 5 ]; do
    echo "Count: $count"
    ((count++))
  done
—

Functions
Reuse code with functions:

greet() {
  echo "Hello, $1!"  # $1 = first argument
}

greet "Newton"  # Output: Hello, Newton!
Return values: Use return for numeric status (0 = success, non-zero = error).
—

Handling Arguments
Scripts accept command-line arguments:

$0: Script name
$1, $2, …: Arguments
$#: Number of arguments
$@: All arguments as a list
Example:

#!/bin/bash
echo "Script: $0"
echo "First arg: $1"
echo "All args: $@"
—

Exit Codes & Error Handling
Every command returns an exit code (0 = success, 1-255 = error).

Use exit to set a script’s exit code:

  if [ ! -f "file.txt" ]; then
    echo "Error: File not found!" >&2  # Redirect to stderr
    exit 1
  fi
—

Debugging Bash Scripts
Enable debugging:

  bash -x script.sh  # Prints each command before execution
Add set -e: Exit immediately if any command fails.

Add set -o pipefail: Catch errors in pipelines.

—

Best Practices
Quote variables: Prevent word splitting.

   echo "$name"  # Safer than echo $name
Use [[ ]] instead of [ ]: More features and fewer surprises.

Check for dependencies:

   if ! command -v git &> /dev/null; then
     echo "Install git first!"
     exit 1
   fi
Indent code: Improve readability.

—

Example Script: Backup Utility
Putting it all together:

#!/bin/bash
# Backup files in a directory
backup_dir="/home/rocky/backups"
source_dir="/home/rocky/documents"

if [ ! -d "$source_dir" ]; then
  echo "Error: Source directory missing!" >&2
  exit 1
fi

mkdir -p "$backup_dir"
tar -czf "$backup_dir/backup_$(date +%Y%m%d).tar.gz" "$source_dir"
echo "Backup completed!"
—

Next Steps
Practice writing scripts for daily tasks.
Explore advanced topics: arrays, traps, subshells, and regex.
Read the Bash Manual.
Remember: The best way to learn is by breaking things and fixing them. 😄

Ready to Level Up Your Bash Skills? 🚀
