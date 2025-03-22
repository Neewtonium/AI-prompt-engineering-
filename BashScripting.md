

# Introduction to Bash Scripting  

**Author:** Rocky | **The Analyst**  

## What is Bash?  
Bash (**Bourne Again SHell**) is a command-line interpreter and scripting language. It’s the default shell on most Linux distributions and macOS (though macOS is moving to Zsh). Bash allows you to:  

- Execute commands  
- Automate workflows  
- Build complex programs using simple scripts  

## Why Learn Bash Scripting?  
- **Automate repetitive tasks** – Backups, file cleanup, deployments  
- **System management** – Monitor resources, manage users, configure servers  
- **Portability** – Bash scripts run on almost any Unix-like system  
- **DevOps foundation** – Used in Docker, Kubernetes, CI/CD pipelines  

---

## Getting Started: Your First Script  

1. **Create a script file:**  
   ```bash
   nano hello.sh

2. Add the shebang line:

#!/bin/bash
echo "Hello World!"


3. Make it executable:

chmod +x hello.sh


4. Run the script:

./hello.sh  # Output: Hello World!




---

Bash Scripting Basics

1. Variables

Variables store data. No data types—everything is a string unless enforced.

name="Rocky"  
age=30  
echo "Hey, I'm $name and I’m $age years old."

> Note: No spaces around = in assignments!



2. Comments

Use # for single-line comments:

# This is a comment

3. Input/Output

Printing:

echo "Text"
printf "Formatted Text"

Reading input:

echo "What's your name?"
read username
echo "Hello, $username!"


---

Control Structures

1. Conditionals (if/else)

if [ $age -gt 18 ]; then
  echo "You’re an adult."
elif [ $age -eq 18 ]; then
  echo "Welcome to adulthood!"
else
  echo "You’re a minor."
fi

Comparison Operators:

-eq : Equal

-ne : Not equal

-gt : Greater than

-lt : Less than

-z "string" : Check if string is empty


2. Case Statements

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


---

Functions

Reuse code with functions:

greet() {
  echo "Hello, $1!"  # $1 = first argument
}

greet "Rocky"  # Output: Hello, Rocky!

> Return values: Use return for numeric status (0 = success, non-zero = error).




---

Handling Arguments

Scripts accept command-line arguments:

Example:

#!/bin/bash
echo "Script: $0"
echo "First arg: $1"
echo "All args: $@"


---

Exit Codes & Error Handling

Every command returns an exit code (0 = success, 1-255 = error).

Use exit to set a script’s exit code:

if [ ! -f "file.txt" ]; then
  echo "Error: File not found!" >&2  # Redirect to stderr
  exit 1
fi


---

Debugging Bash Scripts

Enable debugging:

bash -x script.sh  # Prints each command before execution

Best practices for debugging:

Add set -e: Exit immediately if any command fails.

Add set -o pipefail: Catch errors in pipelines.



---

Best Practices

✔ Quote variables to prevent word splitting:

echo "$name"  # Safer than echo $name

✔ Use [[ ... ]] instead of [ ... ]: More features, fewer surprises.

✔ Check for dependencies before running scripts:

if ! command -v git &> /dev/null; then
  echo "Install git first!"
  exit 1
fi

✔ Indent your code for better readability.


---

Example Script: Backup Utility

A simple backup script:

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


---

Next Steps

✔ Practice writing scripts for daily tasks.
✔ Explore advanced topics: arrays, traps, subshells, regex.
✔ Read the Bash Manual (man bash).

> Remember: The best way to learn is by breaking things and fixing them. 😄




---

Ready to Level Up Your Bash Skills? 🚀

If you're serious about mastering Bash scripting, check out our comprehensive guide:

> Master Shell Scripting: Build Custom Tools & Automate Pentesting



This guide is packed with:

Hands-on projects

Real-world examples

Advanced techniques


Perfect for automating server deployments, log analysis, CLI tool development, and security scripting. Grab your copy today and start automating like a pro! 🔥


---

Rocky out! 🚀

This Markdown version is structured, readable, and fully formatted for documentation or blog publishing. Let me know if you need further refinements!

