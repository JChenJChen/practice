# CODESIGNAL COURSE PATH "Mastering Shell Scripting with Bash" NOTES

- https://codesignal.com/learn/paths/mastering-shell-scripting-with-bash
- https://codesignal.com/learn/course/558/unit/1

5 Courses:
1. Introduction to Shell Scripting Basics
2. Intermediate Shell Scripting with Bash
3. System Automation with Shell Scripts
4. Bash Script Error Handling
5. Text Processing with Bash


- bash alternatives: zsh, sh, and ksh
- NO SPACES BEFORE/AFTER `=`
- commands to run .sh:
  - `chmod +x hello_world.sh`
  - `./hello_world.sh`
- exit codes:
    - 0: Indicates the comparison is true.
    - 1: Indicates the comparison is false.
- `echo $?`: prints exit status of last executed command.
- Numeric comparisons:
    - `-eq`: Equal to
    - `-ne`: Not equal to
    - `-gt`: Greater than
    - `-lt`: Less than
    - `-ge`: Greater than or equal to
    - `-le`: Less than or equal to

```sh
#!/bin/bash

# Simple script to print "Hello, World!"
echo "Hello, World!"

greeting="Hello"
name="World"
echo "$greeting, $name!"  # Prints: Hello, World!
```

Correctly Naming Variables:
- Variable names must begin with a letter (a-z, A-Z) or an underscore (_).
- After the first character, variable names can include letters, numbers (0-9), and underscores, but no other special characters.
- Variable names cannot contain spaces or special characters like !, @, #, $, %, ^, &, *, (, ), -, +, =, etc.
- Variable names are case-sensitive.
- Do not use reserved words or keywords: if, then, else, fi, for, while, etc.

```sh
# Numeric Comparison
num1=5
num2=2
sum=$(($num1 + $num2)) # $(()) evaluate the arithmetic expression within
echo $sum  # Prints: 7
```

- String comparisons:
    - `==` or `=`: Equal to
    - `!=`: Not equal to
    - `-z`: String is null (has a length of zero)
    - `-n`: String is not null (has a length greater than zero)
```sh
# Equal to
[ $num1 -eq $num2 ]
echo $?  # 1 (false)
```

```sh
# Not equal to
[ "$str1" != "$str2" ]
echo $?  # 0 (true)

# Null
[ -z "$str1" ]
echo $?  # 1 (false)
```


https://codesignal.com/learn/course/558/unit/2/practice/2:

```sh
#!/bin/bash

# Creating Variables
greeting="Hello"
name="World"

# TODO: Combine 'greeting' and 'name' into a new variable called 'full_message'
full_message="$greeting $name!"

# Printing new variable
echo $full_message
```


##### LATER COURSES

> https://codesignal.com/learn/paths/mastering-web-scraping-with-python-and-beautiful-soup