# CODESIGNAL COURSE PATH "Mastering Shell Scripting with Bash" NOTES

- https://codesignal.com/learn/paths/mastering-shell-scripting-with-bash
- https://codesignal.com/learn/course-paths/118

5 Courses:
1. [Introduction to Shell Scripting Basics](https://codesignal.com/learn/courses/introduction-to-shell-scripting-basics)  -- 6 lessons
2. [Intermediate Shell Scripting with Bash](https://codesignal.com/learn/courses/intermediate-shell-scripting-with-bash)  -- 4 lessons
3. [System Automation with Shell Scripts](https://codesignal.com/learn/courses/system-automation-with-shell-scripts)  -- 5 lessons
4. [Bash Script Error Handling](https://codesignal.com/learn/courses/bash-script-error-handling)  -- 4 lessons
5. [Text Processing with Bash](https://codesignal.com/learn/courses/text-processing-with-bash)  -- 5 lessons

## Misc Notes

- [diff btwn single vs double quotes](https://stackoverflow.com/questions/6697753/difference-between-single-and-double-quotes-in-bash) = interpolation

## Course 1. Introduction to Shell Scripting Basics

- https://codesignal.com/learn/courses/introduction-to-shell-scripting-basics

### Lesson 1: Writing Your First Shell Script

- https://codesignal.com/learn/course/558/unit/1
- https://codesignal.com/learn/lesson/3929
- https://codesignal.com/learn/courses/introduction-to-shell-scripting-basics/lessons/writing-your-first-shell-script

- bash alternatives: zsh, sh, and ksh
- NO SPACES BEFORE/AFTER `=`
- commands to run .sh:
  - `chmod +x hello_world.sh`
  - `./hello_world.sh`
- exit codes:
    - 0: Indicates the comparison is true.
    - 1: Indicates the comparison is false.
- `echo $?`: prints exit status of last executed command.


```sh
#!/bin/bash

# Simple script to print "Hello, World!"
echo "Hello, World!"

greeting="Hello"
name="World"
echo "$greeting, $name!"  # Prints: Hello, World!
```

### Lesson 2: Using Variables in Shell Scripts

- https://codesignal.com/learn/courses/introduction-to-shell-scripting-basics/lessons/using-variables-in-shell-scripts
- https://codesignal.com/learn/lesson/3930

Correctly Naming Variables:
- Variable names must begin with a letter (a-z, A-Z) or an underscore (_).
- After the first character, variable names can include letters, numbers (0-9), and underscores, but no other special characters.
- Variable names cannot contain spaces or special characters like !, @, #, $, %, ^, &, *, (, ), -, +, =, etc.
- Variable names are case-sensitive.
- Do not use reserved words or keywords: if, then, else, fi, for, while, etc.

#### Arithmetic Operations

- +, -, *, /, and %

```sh
num1=5
num2=2
sum=$(($num1 + $num2)) # $(()) evaluate the arithmetic expression within
echo $sum  # Prints: 7
```

##### Common Arithmetic Mistakes
```sh
num1=2
num2=5

x=num1+num2
echo $x  # Prints: "num1+num2"

y=$num1+$num2
echo $y  # Prints: "2+5"
```

final exercise
```sh
#!/bin/bash
# TODO: Create a variable called file_name and set it to `"example.txt"`
file_name="example.txt"

# TODO: Create a variable called size and set it to 2048.
size=2048
# TODO: Print a message displaying the file_name and its size in the format: "The file example.txt has a size of 2048 bytes."
# echo "The file example.txt has a size of 2048 bytes."
echo "The file $file_name has a size of $size bytes."
# TODO: Create a variable called file1_size and assign it the value of the size variable.
file1_size=$size
# TODO: Print the value of file1_size.
echo $file1_size
# TODO: Create a new variable called file2_size and set it to 1032.
file2_size=1032
# TODO: Calculate the total size and store it in a variable called total_size.
total_size=$(($file1_size+$file2_size))
# TODO: Print the total size in the format: "The total size is <total_size>".
echo "The total size is $total_size"
# TODO: Calculate the average size and store it in a variable called average_size.
average_size=$(($total_size/2))
# TODO: Print the average size in the format: "The average size is <average_size>".
echo "The average size is $average_size"
```

### Lesson 3: Comparison Operators in Shell Scripting
https://codesignal.com/learn/courses/introduction-to-shell-scripting-basics/lessons/comparison-operators-in-shell-scripting
- https://codesignal.com/learn/lesson/3931

#### Numeric Comparison

- Numeric comparisons:
    - `-eq`: Equal to
    - `-ne`: Not equal to
    - `-gt`: Greater than
    - `-lt`: Less than
    - `-ge`: Greater than or equal to
    - `-le`: Less than or equal to
- For each comparison (-eq, -ne, -gt, -lt, -ge, -le), the result is checked, and the exit status is printed using echo $?.
- echo $? prints 0 for true and 1 for false.

```sh
#!/bin/bash

# Variables
num1=10
num2=20

# Equal to
[ $num1 -eq $num2 ]
echo $?  # 1 (false)

# Not equal
[ $num1 -ne $num2 ]
echo $?  # 0 (true)

# Greater than
[ $num1 -gt $num2 ]
echo $?  # 1 (false)

# Less than
[ $num1 -lt $num2 ]
echo $?  # 0 (true)

# Greater than or equal to
[ $num1 -ge $num2 ]
echo $?  # 1 (false)

# Less than or equal to
[ $num1 -le $num2 ]
echo $?  # 0 (true)
```

```sh
#!/bin/bash

file_size=10
available_space=20

restricted_name="example.txt"
file_name="hello.txt"

# TODO: Change comparison operator to check if file_size is less than or equal to available_space
[ $file_size -lt $available_space ]
echo "Is there enough space for the file? $?" # Expected output: Is there enough space for the file? 0

# TODO: Change comparison operator to check if restricted_name is equal to file_name
[ "$restricted_name" = "$file_name" ]
echo "Is the file name restricted? $?" # Expected output: Is the file name restricted? 1
```

### BKMK:L3P2
```sh
#!/bin/bash

file_size=10
available_space=20

restricted_name="example.txt"
file_name="hello.txt"

# TODO: Change comparison operator to check if file_size is less than or equal to available_space
[ $file_size -lt $available_space ]
echo "Is there enough space for the file? $?" # Expected output: Is there enough space for the file? 0

# TODO: Change comparison operator to check if restricted_name is equal to file_name
[ "$restricted_name" = "$file_name" ]
echo "Is the file name restricted? $?" # Expected output: Is the file name restricted? 1
```

#### String Comparisons

- String Comparison Operators:
  - `==` or `=`: Equal to
  - `!=`: Not equal to
  - `-z`: String is null (has a length of zero)
  - `-n`: String is not null (has a length greater than zero)
- strings are compared, then result is checked using echo $? -> 0 = true, 1 = false

```sh
#!/bin/bash

# Variables
str1="Hello"
str2="World"
str3="Hello"

# Equal to with ==
[ "$str1" == "$str2" ]
echo $?  # 1 (false)

# Equal to with =
[ "$str1" = "$str3" ]
echo $?  # 0 (true)

# Not equal to
[ "$str1" != "$str2" ]
echo $?  # 0 (true)

# Null
[ -z "$str1" ]
echo $?  # 1 (false)

# Not null
[ -n "$str1" ]
echo $?  # 0 (true)
```

#### Quotes in String Comparisons

> ex: `[ "$str1" == "$str2" ]`

Purpose:
1.  Handling Empty Strings, i.e. vars are empty or undefined
```sh
#!/bin/bash

str1=""
[ $str1 == "Hello" ]  # [ == "Hello" ] -> invalid syntax
```
1. Preserving Whitespaces
```sh
#!/bin/bash

str1="Hello World"
[ $str1 == "Hello World" ]  # [ Hello == Hello World ]
```

### Lesson 4: Control Structures and Logical Operators in Shell Scripting

- https://codesignal.com/learn/courses/introduction-to-shell-scripting-basics/lessons/control-structures-and-logical-operators-in-shell-scripting
- https://codesignal.com/learn/lesson/3932


#### Control structures (if, elif, else)

- if
- elif
- else

- conditions must be enclosed in `[]`. 
- After condition, `then` keyword specifies code to execute if the condition evaluates to 0 (true).
- control structures must start with an `if` statement, and end with `fi`
  - `elif` and `else` statements are optional.

```sh
if [ condition1 ]
then
    # Commands to execute if condition1 is true
elif [ condition2 ]
then
    # Commands to execute if condition1 is false and condition2 is true
else
    # Commands to execute if both condition1 and condition2 are false
fi
```

#### Logical Operators (&&, ||)

- && (AND)
```sh
#!/bin/bash
# Variables
num1=10
num2=20
str1="Hello"
str2="World"

# Using && (AND) Operator
if [ $num1 -lt $num2 ] && [ "$str1" != "$str2" ]
then
    echo "num1 is less than num2 AND str1 is not equal to str2"  # Prints: "num1 is less than num2 AND str1 is not equal to str2"
else
    echo "Condition is false"  # This won't execute
fi
``` 

- || (OR)

```sh
#!/bin/bash

# Variables
num1=10
num2=20

# Using || (OR) Operator
if [ $num1 -gt 5 ] || [ $num2 -lt 5 ]
then
    echo "num1 is greater than 5 OR num2 is less than 5"  # Prints: "num1 is greater than 5 OR num2 is less than 5"
else
    echo "Neither condition is true"  # This won't execute
fi
```

String interpolation
```sh
#!/bin/bash

greeting="Hello"
name="World"
echo "$greeting, $name!"  # Prints: Hello, World!
```



### Lesson 5: Arrays and Looping Constructs in Shell Scripting

- https://codesignal.com/learn/courses/introduction-to-shell-scripting-basics/lessons/arrays-and-looping-constructs-in-shell-scripting
- https://codesignal.com/learn/lesson/3933



### Lesson 6: Functions in Shell Scripts

- https://codesignal.com/learn/courses/introduction-to-shell-scripting-basics/lessons/functions-in-shell-scripts

## Course 4: Bash Script Error Handling

- https://codesignal.com/learn/courses/bash-script-error-handling


## Course 5: Text Processing with Bash

- https://codesignal.com/learn/courses/text-processing-with-bash


#### LATER COURSES

> https://codesignal.com/learn/paths/mastering-web-scraping-with-python-and-beautiful-soup