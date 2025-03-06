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
- echo $? prints:
  -  0 for true 
  -  1 for false

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
[ $file_size -le $available_space ]
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

##### L3P2
```sh
#!/bin/bash

file_size=10
available_space=20

restricted_name="example.txt"
file_name="hello.txt"

# TODO: Change comparison operator to check if file_size is less than or equal to available_space
[ $file_size -le $available_space ]
echo "Is there enough space for the file? $?" # Expected output: Is there enough space for the file? 0

# TODO: Change comparison operator to check if restricted_name is equal to file_name
[ "$restricted_name" = "$file_name" ]
echo "Is the file name restricted? $?" # Expected output: Is the file name restricted? 1
```


##### [U3P3](https://codesignal.com/learn/course/558/unit/3/practice/3)
```sh
#!/bin/bash

newest_version=5
current_version=4

[ $newest_version -gt $current_version ]
echo "Does version need to be updated: $?"

admin_name="Cosmo Admin"
[ "$admin_name" == "Cosmo Admin" ]
echo "Is the user an admin? $?"
```
> NOTE: quotes around string variable to be compared





### Lesson 4: Control Structures and Logical Operators in Shell Scripting

- https://codesignal.com/learn/courses/introduction-to-shell-scripting-basics/lessons/control-structures-and-logical-operators-in-shell-scripting
- https://codesignal.com/learn/lesson/3932


#### Control structures (if, elif, else)

- if
- elif
- else

- conditions must be enclosed in `[]`, padded with spaces
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

##### U4P3
```sh
#!/bin/bash

available_memory=2048
download_size=1048
admin_password="password"
user_password="password"

if [ $available_memory -ge $download_size ] && [ "$admin_password" == "$user_password" ] 
then
    echo "Download allowed"
elif [ $available_memory -ge $download_size ] || [ "$admin_password" == "$user_password" ]
then
    echo "There is either not enough space or password is incorrect"
else
    echo "Not enough memory and incorrect password"
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

#### Arrays in sh

- arrays syntax
```sh
#!/bin/bash
computers=("Dell" "HP" "Lenovo")
```

- add elements to array using `+=`
```sh
#!/bin/bash
computers=("Dell" "HP" "Lenovo")
computers+=("Mac")
```

- Array Length and Printing
    - ${#array_name[@]} - access array length
    - ${array_name[@]} - print array contents

```sh
#!/bin/bash
computers=("Dell" "HP" "Lenovo")
computers+=("Mac")
echo "Number of computers: ${#computers[@]}"
echo "All computers: ${computers[@]}"
```
returns:
```
Number of computers: 4
All computers: Dell HP Lenovo Mac
```

- Array Indexing
  - 0 indexed
  - ${array_name[index_number]}


#### While Loops in sh

- while loop syntax:
```sh
#!/bin/bash
while [ condition ]
do
    command1
    command2
    ...
done
```

- while loop syntax example
```sh
#!/bin/bash

counter=1

# Start the while loop
while [ $counter -le 3 ]
do
    echo "Counter: $counter" 
    # Increment the counter
    ((counter++))
done
```

#### For Loops in sh

- For Loop syntax:
```sh
#!/bin/bash
for ((initialization; condition; update))
do
  commands
done
```

- For Loop syntax example
```sh
#!/bin/bash
for ((x=1; x<=3; x++))
do
  echo "Iteration $x"
done
```

#### For In Loops in sh

- For In loop syntax
  - {start..end} - range/list syntax
```sh
#!/bin/bash
for variable in list
do
    command1
    command2
    ...
done
```

- For In loop syntax example
```sh
#!/bin/bash
# Script to demonstrate for loop
for i in {1..5}
do
  echo "Iteration $i"
done
```

```sh
#!/bin/bash

operating_systems=("Windows" "macOS" "Linux")

for ((i=0; i<${#operating_systems[@]}; i++))
do
  echo "OS $i: ${operating_systems[$i]}"
done
```

#### Looping Thru Arrays
- `for in` with `"${array_name[@]}"` - iterate over array elements
```sh
#!/bin/bash
# Looping through array
computers=("Dell" "HP" "Lenovo")

for computer in "${computers[@]}"
do
    echo "$computer"
done
```

#### Unit 5 Practices

All Together
```sh
#!/bin/bash
# Declare Array
operating_systems=("Windows" "macOS" "Linux")

# While Loop
echo "Starting while loop"
index=0
while [ $index -le 2 ]
do
    echo "OS $index: ${operating_systems[$index]}"
    ((index++))
done

# For loop
echo "Starting for loop on range"
for i in {0..2}
do
  echo "OS $i: ${operating_systems[$i]}"
done

# Looping through array
echo "Starting for loop on array"
for os in "${operating_systems[@]}"
do
    echo "$os"
done
```

##### U5P4
```sh
#!/bin/bash
# Declare and Use Array
file_names=("example.txt" "hello.py")
# TODO: Add a file "index.html" to the file_names array
file_names+=("index.html")
# TODO: Print the number of files
echo "Number of files: ${#file_names[@]}"

# TODO: Print the file_names array
echo "All files: ${file_names[@]}"

# Loop through the array and print each file name
for file in "${file_names[@]}"
do
    echo "$file"
done
```

##### U5P5
```sh
#!/bin/bash
applications=("Photos" "Email" "Calendar")
update_needed=("Yes" "No" "Yes")

# TODO: Add "Browser" to `applications`
applications+=("Browser")
# TODO: Update the `update_needed` array. "Browser" does not need to be updated
update_needed+=("No")
# TODO: Loop through the arrays. If an update is needed print "Updating <application>". If an update is not needed, print "<application> up to date"
# for application in "${applications[@]}"
# for update in "${update_needed[@]}"
for i in {0..3}
do
    if [ "${update_needed[$i]}" = "Yes" ]
    then
        echo "Updating ${applications[$i]}"
    else
        echo "${applications[$i]} up to date"
    fi
done
```

### Lesson 6: Functions in Shell Scripts

- https://codesignal.com/learn/courses/introduction-to-shell-scripting-basics/lessons/functions-in-shell-scripts
- https://codesignal.com/learn/lesson/3934

#### Defining and Calling Functions

- defining functions syntax
```sh
#!/bin/bash
# Defining a function
function_name() {
  # Commands to be executed
}

# Calling the function
function_name
```

- defining functions syntax example
```sh
#!/bin/bash
# Defining a function
greet() {
  echo "Hello"
}

greet
```

#### Passing Arguments to Functions

```sh
#!/bin/bash
# Function with 1 input
update_one() {
  echo "Updating $1"
}

# Function with 2 inputs
update_two() {
    echo "Updating $1 and $2"
}

update_one "Photos"
update_two "Photos" "Browser"
```

#### Counting Arguments with `$#`

```sh
#!/bin/bash
# Function to count arguments
count_args() {
    echo "Number of arguments: $#"
}

count_args "Photos" "Browser" "Documents"
```

#### Iterating Over Arguments Using Arrays and `$@`

- convert arguments to an array using args=("$@")

```sh
#!/bin/bash
print_args() {
  arr=("$@")
  
  echo "Using array indices:"
  for x in "${arr[@]}"
   do
    echo "$x"
  done
  
  echo "Using \$@:"
  for y in "$@"
  do
    echo "$y"
  done
}

print_args "Photos" "Browser" "Documents"
```

#### Returning Values from Functions

```sh
#!/bin/bash
# Function to increase a version number
increase_version() {
  ((version += increment))
  echo $version
}

version=2
increment=3
# Capture the return value using command substitution
result=$(increase_version)          
echo "Updating from version $version to $result"   # Prints: "Updating from version 2 to 5"
```

##### U6P1
```sh
#!/bin/bash

greet() {
  echo "Hello, $1!"
}

greet "World"

add_file() {
    num=$1
    ((num++))
    echo $num
}

num_files=5
num_files=$(add_file $num_files)
echo "Number of files is $num_files"
```

##### U6P2
```sh
#!/bin/bash
#!/bin/bash

# TODO: Modify the add_one function to take two parameters and return their sum.
add_one_number() {
    num1=$1
    num2=$2
    echo $(($num1 + $number2))
}

number1=5
number2=3

# TODO: Modify the function call to pass two parameters
result=$(add_one_number $number1 $number2)

# TODO: Adjust the print statement to reflect the new function
echo "Adding $number1 and $number2 gives: $result" # Expected output: Adding 5 and 3 gives: 8
```

##### U6P4
```sh
#!/bin/bash
update_apps() {
  # TODO: Convert the arguments to an array and assign it to the variable apps
  apps=("$@")
  
  # TODO: Loop through the "apps" array
  for app in "${apps[@]}"
  do
    echo "Checking $app"
  done
  
  # TODO: Loop through the positional arguments without using the "apps" array
  for app in "$@"
  do
    echo "Updating $app"
  done
}

update_apps "Photos" "Browser" "Documents"
```

###### U6P5
```sh
#!/bin/bash

# TODO: Define the `increase_file_size` function
increase_file_size() {
# The function should accept three parameters: filename, current size in bytes, and bytes to increase.
    filename=$1
    cur_size=$2
    bytes_to_inc=$3
    new_size=$(($cur_size+$bytes_to_inc))
# It should calculate the new size and echo a message in the format: "File {filename} is now {new_size} bytes".
    # echo 
    echo "File $filename is now $new_size bytes"
}

# TODO: Define the `validate_files` function
validate_files() {
# The function should accept multiple filenames as parameters.
    filenames=("$@")
# It should iterate through each filename and echo a validation message in the format: "{filename} validated".
    for filename in "${filenames[@]}"
    do
        echo "$filename validated"
    done
}

# TODO: Call the `increase_file_size` function with "index.html", 1024, and 2048 as arguments
# Store the result in a variable and echo the result.
result=$(increase_file_size "index.html" 1024 2048)
echo $result
# TODO: Call the `validate_files` function with "hello.py" and "main.cpp" as arguments
validate_files "hello.py", "main.cpp"
```

## Course 2: Intermediate Shell Scripting with Bash
- https://codesignal.com/learn/course/559/unit/1
- https://codesignal.com/learn/lesson/3935

### Lesson 1: File Operations
- https://codesignal.com/learn/courses/intermediate-shell-scripting-with-bash/lessons/file-operations
- https://codesignal.com/learn/lesson/3935

#### Creating a File
```sh#!/bin/bash
touch example.txt
```

#### Writing to a File
```txt
command > filename
```

```sh
#!/bin/bash
echo "Hello, World!" > example.txt
```

#### Displaying the Content of a File
```sh
#!/bin/bash
cat example.txt
```

#### Copying a File
```txt
cp source destination
```

```sh
#!/bin/bash
cp example.txt example_copy.txt
```

#### Removing a File
```sh
#!/bin/bash
rm example.txt
```

#### Clearing the Contents of a File
```sh
#!/bin/bash
> example_copy.txt
```

### Lesson 2: Input, Output, and Redirection
- https://codesignal.com/learn/courses/intermediate-shell-scripting-with-bash/lessons/input-output-and-redirection?
- https://codesignal.com/learn/lesson/3936

#### stdin, stdout, and stderr
- standard input, output, error

#### Redirecting Output to a File
- > : overwrites the contents of the file
- >> : appends to file

#### Appending the Contents of One File to Another
- cat file1 >> file2

#### Reading from a File Line by Line
```sh
#!/bin/bash
while read line; do
    echo "$line"
done < destination.txt
```

#### `|` (Pipeline) Operator
- passes output of first command as input to next command

#### Using a Pipeline to Process Input
- wc : counts lines, words (-w), and characters
```sh
#!/bin/bash
cat destination.txt | wc -w
```

### Lesson 3: Directory Operations
- https://codesignal.com/learn/courses/intermediate-shell-scripting-with-bash/lessons/directory-operations
- https://codesignal.com/learn/lesson/3937

### Lesson 4: Environment Variables in Bash
- https://codesignal.com/learn/courses/intermediate-shell-scripting-with-bash/lessons/environment-variables-in-bash
- https://codesignal.com/learn/lesson/3938


## Course 3: System Automation with Shell Scripts
- https://codesignal.com/learn/courses/system-automation-with-shell-scripts
- 

## Course 4: Bash Script Error Handling
- https://codesignal.com/learn/courses/bash-script-error-handling


## Course 5: Text Processing with Bash

- https://codesignal.com/learn/courses/text-processing-with-bash


#### LATER COURSES

> https://codesignal.com/learn/paths/mastering-web-scraping-with-python-and-beautiful-soup