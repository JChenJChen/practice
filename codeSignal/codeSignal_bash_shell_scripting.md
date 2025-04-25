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

- all together:
```sh
#!/bin/bash

# Redirecting initial log entry to server.log (overwrite if exists)
echo "Server started." > server.log

# Appending a user login entry to server.log
echo "User login successful" >> server.log

# Redirecting an error message to error.log (overwrite if exists)
echo "Error: Unable to connect" > error.log

# Appending the contents of error.log to server.log
cat error.log >> server.log

# Initialize a counter to number the log entries
counter=1
# Reading from server.log file line by line
while read line; do
    # Print the line number and the line content
    echo "$counter. $line"
    # Increment the counter
    ((counter++))
done < server.log

# Print the number of words in server.log
echo "Number of words:"
cat server.log | wc -w
```

output:
```
1. Server started.
2. User login successful
3. Error: Unable to connect
Number of words:
9
```

- loop through each line, count the number of words in that line, and place the output in a file called result.txt
```sh
#!/bin/bash

# Redirecting output to a file
echo "Greetings" > file.txt

# Appending output to the file
echo "Hello World" >> file.txt

echo "Welcome to Bash" >> file.txt

# Creating result.txt file
touch result.txt
echo "Word Counts by Line" > result.txt

# TODO: Read each line from file.txt, count the words, and append the count to result.txt
counter=1
while read line; do
   echo "$line" | wc -w >> result.txt
done < file.txt
# echo $counter >> result.txt
cat result.txt
```

##### U2P5
```sh
#!/bin/bash

# Defining the square function to read from stdin
square() {
    # Clearing the contents of output.txt
    > output.txt
    while read number; do
        echo "The square of $number is $((number*number))" >> output.txt
    done
}


# TODO: Create input.txt and add numbers 1, 2, and 3 to it
> input.txt
# echo 1 > input.txt
# echo 2 >> input.txt
# echo 3 >> input.txt
for i in {1..3}
do
    echo $i >> input.txt
done
cat input.txt
# TODO: Use a pipeline to pass the contents of input.txt to the square function
cat input.txt | square
# TODO: Display the contents of output.txt
cat output.txt
```

### Lesson 3: Directory Operations
- https://codesignal.com/learn/courses/intermediate-shell-scripting-with-bash/lessons/directory-operations
- https://codesignal.com/learn/lesson/3937

- Directory
- Directory structure diagram
- CWD: `pwd`
- ls
- mkdir [-p] &rarr; -p creates nonexistent parent dirs, will not fail if dir already exists.
- removing dirs:
  - rmdir &rarr; only if dir is empty
  - rm -r
- cd

- intro all together example:
```sh
#!/bin/bash

# Print working directory
echo "Current working directory: $(pwd)"
echo 

# Creating a new directory named projects
mkdir -p projects

# Changing to the projects directory
cd projects

# Creating a new directory named project1 inside projects
mkdir -p project1

# Changing to the project1 directory
cd project1

# Creating a new file named file1.txt inside project1
touch file1.txt

# Creating a new directory named project_draft inside projects
mkdir -p ../project_draft

# Creating a new file named draft.txt inside project_draft
touch ../project_draft/draft.txt

# Listing files and directories inside projects
echo "Listing files and directories inside the projects directory"
ls ..
echo 

# Removing the directory project_draft and its contents
echo "Removing project_draft directory"
rm -r ../project_draft
echo 

# Moving up one directory level to projects
cd ..

# Listing files and directories inside projects
echo "Listing files and directories inside the projects directory"
ls
```

### Lesson 4: Environment Variables in Bash
- https://codesignal.com/learn/courses/intermediate-shell-scripting-with-bash/lessons/environment-variables-in-bash
- https://codesignal.com/learn/lesson/3938

- printenv: lists all system-wide & custom env vars set for current shell session
- common built-in env vars (echo $[VAR]):
  - HOME: home dir &rarr; `/root`
  - SHELL: path of current shell &rarr; `/bin/bash`
  - PWD: current working dir &rarr; `/usercode/FILESYSTEM`
  - PATH: which dirs to search for executables
    - /root/.nvm/versions/node/v18.12.1/bin: Directory containing Node.js executables.
    - /usr/local/sbin: Directory for local system administrator binaries.
    - /usr/local/bin: Directory for locally installed executables.
    - /usr/sbin: Directory for essential system binaries for root.
    - /usr/bin: Directory for user binaries.
    - /sbin: Directory for essential system binaries.
    - /bin: Directory for essential user binaries.
- export MY_VAR="Hello, Bash!" &rarr; creates or modifies env var
- export PATH="$PATH:/usercode/FILESYSTEM"  &rarr; Add new dir to PATH
- chmod +x greet.sh &rarr; ensures script is executable

- all together example:
```sh
#!/bin/bash

# Commonly Used Built-in Environment Variables
echo "Home Directory: $HOME"
echo "Shell Directory: $SHELL"
echo "Current working directory $PWD"

# The PATH variable
echo "PATH is:"
echo $PATH
echo

# Creating USER environment variable
export USER="Cosmo"

# Adding to PATH variable
export PATH="$PATH:/usercode/FILESYSTEM"

# Calling greet_user script
chmod +x greet_user.sh
echo "Calling greet_user.sh"
greet_user.sh
```

####
```sh
#!/bin/bash

# TODO: Create an environment variable called USER with any value
export USER="any_value"
# TODO: Update PATH to include the my_scripts directory
export PATH="$PATH:/usercode/FILESYSTEM/my_scripts"
# TODO: Update permissions of greet.sh 
chmod +x my_scripts/greet.sh

# TODO: Run greet.sh script
my_scripts/greet.sh

# TODO: Update permissions of update.sh
chmod +x my_scripts/update.sh

# TODO: Run update.sh script
my_scripts/greet.sh
```


## Course 3: System Automation with Shell Scripts
- https://codesignal.com/learn/courses/system-automation-with-shell-scripts

### Lesson 1: Updating System Packages
- https://codesignal.com/learn/courses/system-automation-with-shell-scripts/lessons/updating-system-packages
- https://codesignal.com/learn/lesson/3939

- Packages: 
  - collections of files, metadata, and scripts used to install software on a computer
  - bundle all the components necessary to run a program, including: 
    - binaries
    - configuration files
    - documentation
    - dependencies
- Repositories:
  - structured storage locations where software packages are retrieved and installed 
  - centralized, where developers upload and users download software packages
  - package management systems (PMS): handle installation, upgrade, configuration, and removal of packages. 
    - Advanced Packaging Tool (APT): a package management system on Debian-based Linux distributions (ex: Ubuntu)
    - `apt-get`: APT command-line tool that handles packages in shell scripts

- apt list --installed: see the list of installed packages

output:
```txt
...
bash/focal-updates,focal-security,now 5.0-6ubuntu1.2 amd64 [installed]
git/now 1:2.43.0-0ppa1~ubuntu20.04.1 amd64 [installed,upgradable to: 1:2.45.2-0ppa1~ubuntu20.04.1]
...
```
explanation of output:
- bash: The name of the package.
- focal-updates,focal-security: The repositories where this version of the package is available
- now: Indicates the status of the package (currently installed).
- 5.0-6ubuntu1.2: The version of the package that is installed.
- amd64: The architecture for which the package is built (64-bit in this case).
- [installed]: Indicates that the package is currently installed on your system.

- sudo apt-get update: fetches package list from repos and stores them locally, to update the list of available packages and their versions, but **does not install or upgrade them**
output:
```
Hit:1 http://archive.ubuntu.com/ubuntu focal InRelease
Hit:2 http://repo.mysql.com/apt/ubuntu focal InRelease
Hit:3 http://archive.ubuntu.com/ubuntu focal-updates In Release
....
Reading package lists... Done
```
explanation of output:
- Hit:1 indicates that the repository at position 1 in the list of sources was successfully accessed.
- http://archive.ubuntu.com/ubuntu: The URL of the Ubuntu repository.
- focal: The codename for the Ubuntu release (Focal Fossa, 20.04).
- InRelease: Indicates that the repository provides an InRelease file, which is a signed metadata file combining the Release file and its signature.


- sudo apt-get upgrade: 
  - installs latest versions of all installed packages based on the updated package lists fetched by sudo apt-get update
  - Maintains Configuration Files: If package configuration files have been modified -- prompts whether to keep the existing or replace with newer versions
  - `-s` flag simulates upgrade -- sees which packages get upgraded
output:
```
Inst base-files [11ubuntu5.7]... -- package will be installed or upgraded

Conf base-files --after the package `base-files` is upgraded, it will be configured to integrate w/ the system.
```

script combining everything:
```sh
#!/bin/bash
# Comprehensive script to update system packages
echo "Listing all packages"
apt list --installed  # Shows all installed packages

echo "Updating package lists..."
sudo apt-get update # Updates package lists from the repositories

echo "Listing packages that will be upgraded..."
sudo apt-get -s upgrade # Simulates the package upgrade
```

practice 1 full example:
```sh
#!/bin/bash
# Script to update system packages
echo "Listing all packages"
apt list --installed > package_list.txt

echo "Updating package lists..."
sudo apt-get update > updated_list.txt

echo "Listing packages that will be upgraded..."
sudo apt-get -s upgrade  > upgrades.txt
```

### Lesson 2: User Management
- https://codesignal.com/learn/courses/system-automation-with-shell-scripts/lessons/user-management
- https://codesignal.com/learn/lesson/3940

- /etc/passwd: 
  - where list of users is saved
  - 1st (: delimited) line reserved for superuser: `root:x:0:0:root:/root:/bin/bash`
  - The 1st field root is the username. This is the traditional name for the superuser.
The 6th field is /root which is the home directory for the root user.
The 7th field /bin/bash indicates that the root user's shell is bash.

- whoami: display the username of the current user who is executing the command
  - Each user has their own set of environment variables
  - $HOME displays the home directory of the current user
  - $SHELL prints the user's shell

- useradd: adds a new user
  - adduser -- alternative
```sh
#!/bin/bash
# Creating and adding a new user
username="newuser"

sudo useradd -m $username
echo "New user information: $(grep $username /etc/passwd)"
```
- $username: Creates a New User Account, with attributes i.e. username, password, home directory, shell, etc.
- -m flag: Sets User Home Dir (if specified)
- Configures Account Settings: allows setting different options like user ID (UID), group ID (GID), account expiration, etc.

Some other options you can use with the useradd command are:

-d /path/to/home: Specify a custom home directory instead of the default.
-s /path/to/shell: Set the user's login shell.

practice 1 all together example:
```sh
#!/bin/bash

# Accessing all users
cat /etc/passwd > users.txt

# Print the current user and home directory
echo "Current user: $(whoami)"
echo "Current home directory: $HOME"
echo "Current shell: $SHELL"
echo "User information: $(grep $(whoami) /etc/passwd)"

# Creating and adding a new user
username="newuser"
sudo useradd -m $username
echo "New user information: $(grep $username /etc/passwd)"
```


##### U2P3
```sh
#!/bin/bash

# Creating a directory called 'users' to store home directories of new users
mkdir -p users

# Creating and adding new users
for username in "userA" "userB" "userC"; do
    # Set the home directory for the new user inside the 'users' directory
    home_dir=$PWD/users/$username
    
    # TODO: Create the new user with specified home directory
    sudo useradd -m -d $home_dir $username
    echo "New user information: $(grep $username /etc/passwd)"
done

echo
echo "Printing subdirectories of the 'users' directory..."
# TODO: Print the content of the users directory
ls users
```



### Lesson 3: Disk Usage Monitoring
- https://codesignal.com/learn/courses/system-automation-with-shell-scripts/lessons/disk-usage-monitoring
- https://codesignal.com/learn/lesson/3941

#### P1 Demo Code
- https://codesignal.com/learn/course/560/unit/3/practice/1
```sh
#!/bin/bash

# Directory to monitor
FILESYSTEM="/tmp"

# Clear any previous files
rm -rf /tmp/big_files

# Display the disk usage of the filesystem containing the /tmp directory.
echo "Filesystem usage:"
df $FILESYSTEM
echo 

echo "Filesystem usage with -h"
df -h $FILESYSTEM
echo

# Display the disk usage of all files and directories under /tmp
echo "Directory usage with -h"
du -h $FILESYSTEM
echo

echo "Directory usage with -sh"
du -sh $FILESYSTEM
echo

# Create a new directory with a big file, and print out disk usage statistics
echo "Creating a 10 MB file"
mkdir -p $FILESYSTEM/big_files
fallocate -l 10M $FILESYSTEM/big_files/10MB_file

echo
echo "Directory usage after creating file"
du -h $FILESYSTEM
```
#### Disk Usage of Filesystems with df

- `df`: overview of filesystem disk space usage, ex: total, used, & available space, % used space.
  - No filepath: all mounted filesystems; specify filepath for only that filesystem.
  - `-h` flag: human-readable output

```sh
#!/bin/bash

# Directory to monitor
FILESYSTEM="/usercode/FILESYSTEM"

# Display the disk usage of the filesystem containing the /usercode/FILESYSTEM directory
df $FILESYSTEM
df -h $FILESYSTEM
```

> output:
```txt
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/vda1      650206116 54170548 596019184   9% /usercode/FILESYSTEM

Filesystem      Size  Used Avail Use% Mounted on
/dev/vda1       621G   52G  569G   9% /usercode/FILESYSTEM
```

#### Disk Usage of Files and Directories with du

- `du`: estimate disk usage of files and directories
  - `-sh`: total disk usage summary for specified directory in human-readable format
    - total disk usage of the entire directory at the top level -- does not list individual items.

```sh
#!/bin/bash

# Display the disk usage of all files and directories under /usercode/FILESYSTEM
echo "Using -h option"
du -h $FILESYSTEM
echo ""
echo "Using -sh option"
du -sh $FILESYSTEM
```

> output:
```txt
Using -h option
12K	/usercode/FILESYSTEM/.codesignal
20K	/usercode/FILESYSTEM

Using -sh option
20K	/usercode/FILESYSTEM
```

#### Creating and Managing Large Files

- `fallocate`: useful for creating large file quickly & ensures disk space is available by preallocating space to a file.
  - `fallocate -l <size> <filename>`
    - `-l <size>`: specifies file size to be -- in bytes, KB (e.g., 10K), MB (e.g., 10M), GB (e.g., 10G), etc.

```sh
#!/bin/bash

# Create a new directory with a big file, and print out disk usage statistics
mkdir -p $FILESYSTEM/big_files
fallocate -l 10G $FILESYSTEM/big_files/10GB_file
echo "Using -h option"
du -h $FILESYSTEM
echo 
echo "Using -sh option"
du -sh $FILESYSTEM
```

> output:
```txt
Using -h option
11G	/usercode/FILESYSTEM/big_files
12K	/usercode/FILESYSTEM/.codesignal
11G	/usercode/FILESYSTEM

Using -sh option
11G	/usercode/FILESYSTEM
```


### Lesson 4: Scheduling Tasks with Cron
- https://codesignal.com/learn/courses/system-automation-with-shell-scripts/lessons/scheduling-tasks-with-cron
- https://codesignal.com/learn/lesson/3942

- `cron` alternatives: `at`, `systemd timers`
- cron jobs: cron scheduled tasks to be executed at specific times or intervals.
- crontabs (cron tables): stores cron job configurations.
  - each system user can have own crontab.
  - `root` user manages system-wide crontab.

#### cron syntax
```txt
* * * * * command_to_execute
│ │ │ │ │
│ │ │ │ └──── Day of the week (0 - 7) (both 0 and 7 mean Sunday)
│ │ │ └────── Month (1 - 12)
│ │ └──────── Day of the month (1 - 31)
│ └────────── Hour (0 - 23)
└──────────── Minute (0 - 59)
```
- A single number: 5 means "exactly at five".
- A range of numbers: 1-5 means "1 to 5".
- A list of numbers: 1,2,3 means "1 or 2 or 3".
- An asterisk (*) wildcard means "every" possible value of this field.
- /: Specifies step values. For example, */5 in the minutes field means "every 5 minutes".

##### cron syntax examples:
every day at 5 AM:
```txt
0 5 * * * /path/to/script.sh
```

every Monday at 3 PM
```txt
0 15 * * 1 /path/to/script.sh
```

every 15 minutes
```txt
*/15 * * * * /path/to/script.sh
```

every day at midnight
```txt
0 0 * * * /path/to/nightly_backup.sh
```

10 PM on the 1st of every month
```txt
0 22 1 * * /path/to/monthly_job.sh
```

#### Creating a Simple Cron Job

`print_time.sh` -- prints current date and time to `time.txt`:
```sh
#!/bin/bash
TARGET_DIR="/usercode/FILESYSTEM"
OUTPUT_FILE="$TARGET_DIR/time.txt"
echo $(date) >> $OUTPUT_FILE
```
> NOTE: relative paths work, but absolute path's preferred.

#### Scheduling Cron Jobs Syntax
- by appending to crontab
- `crontab -l`: displays user's crontab file contents -- all scheduled tasks and corresponding schedules.

```sh
(crontab -l; echo "<command>" ) | crontab -
```
- `crontab -l`: lists the current user's cron jobs.
- `echo "<command>"`: creates a new line with the specified cron command
- parentheses group the two commands together so that they are treated as a single unit.
- `| crontab` - pipelines the combined output of the grouped commands to the crontab command.

#### Scheduling A Cron Job
- `schedule_task.sh`: set up and schedule `print_time.sh` script as a cron job
```sh
#!/bin/bash

# Specify script path and give execute permissions
SCRIPT_PATH="$PWD/print_time.sh" # absolute path
chmod +x $SCRIPT_PATH # makes script executable

# Start cron
sudo service cron start
# Verify cron has started
service cron status

# Create the cron command
command="*/1 * * * * $SCRIPT_PATH" # runs every minute

# Append the cron job; handle the case when there's no existing crontab
(crontab -l; echo "$command" ) | crontab -

# Confirm cron job was added
crontab -l
```

output:
```txt
 * Starting periodic command scheduler cron
   ...done.
 * cron is running
*/1 * * * * /usercode/FILESYSTEM/print_time.sh
```

time.txt:
```txt
Mon Jul 29 00:06:01 UTC 2024
Mon Jul 29 00:07:01 UTC 2024
Mon Jul 29 00:08:01 UTC 2024
```


#### P1 Demo Code
- https://codesignal.com/learn/course/560/unit/4/practice/1

solution.sh:
```sh
#!/bin/bash

SCRIPT_PATH="$PWD/print_time.sh"
chmod +x $SCRIPT_PATH

# Start cron services
sudo service cron start
service cron status

# Create the cron command
command="*/1 * * * * $SCRIPT_PATH"

# Append the cron job to crontab
(crontab -l; echo "$command" ) | crontab -

# Confirm cron job was added
echo "Printing cron jobs..."
crontab -l
```

print_time.sh:
```sh
#!/bin/bash
TARGET_DIR="/usercode/FILESYSTEM"
OUTPUT_FILE="$TARGET_DIR/time.txt"
echo $(date) >> $OUTPUT_FILE
```

output saved to time.txt:
```txt
Wed Apr 16 16:15:01 UTC 2025
```

stdout:
```txt
 * Starting periodic command scheduler cron
   ...done.
 * cron is running
Printing cron jobs...

*/1 * * * * /usercode/FILESYSTEM/print_time.sh
```

### Lesson 5: Automating Backups
- https://codesignal.com/learn/courses/system-automation-with-shell-scripts/lessons/automating-backups
- https://codesignal.com/learn/lesson/3943

#### P1 Demo Code
```sh
#!/bin/bash
# Script to automate backups

source_dir="$(pwd)/data"
backup_dir="$(pwd)/backups/data_$(date '+%Y-%m-%d_%H-%M-%S')" # data_YYYY-MM-DD_HH-MM-SS

mkdir -p $backup_dir
cp -r $source_dir/* $backup_dir/
echo "Backup completed: $backup_dir"
ls backups/ 
```

output:
```txt
Backup completed: /usercode/FILESYSTEM/backups/data_2025-04-21_20-29-00
data_2025-04-21_20-29-00
```

#### P5 Solution
```sh
#!/bin/bash
#!/bin/bash

# TODO: Create directories named 'data' and 'logs'
data_dir="$(pwd)/data"
logs_dir="$(pwd)/logs"
mkdir -p $data_dir
mkdir -p $logs_dir
# TODO: Add text files 'd1.txt' and 'd2.txt' to 'data' directory with the text "File D1" and "File D2" respectively
echo "File D1" > "$data_dir/d1.txt"
echo "File D2" > "$data_dir/d2.txt"
# TODO: Add log files 'l1.log' and 'l2.log' to 'logs' directory with the text "Log L1" and "Log L2" respectively
echo "Log L1" > "$logs_dir/l1.txt"
echo "Log L2" > "$logs_dir/l2.txt"
# TODO: Define source directories for data and logs

# TODO: Create backup directories with a timestamp for both data and logs
backup_data_dir="$(pwd)/backups/data_$(date '+%Y-%m-%d_%H-%M-%S')"
backup_logs_dir="$(pwd)/backups/logs_$(date '+%Y-%m-%d_%H-%M-%S')"
mkdir -p $backup_data_dir
mkdir -p $backup_logs_dir
# TODO: Copy all files from the source directories to their respective backup directories
cp -r $data_dir/* $backup_data_dir/
cp -r $logs_dir/* $backup_logs_dir/
# TODO: List the contents of the 'backups' directory to confirm successful backup
ls backups/
# OUTPUT:
# logs_2025-04-24_22-17-07
# data_2025-04-24_22-17-07
```

## Course 4: Bash Script Error Handling
- https://codesignal.com/learn/courses/bash-script-error-handling
- https://codesignal.com/learn/lesson/3944



## Course 5: Text Processing with Bash

- https://codesignal.com/learn/courses/text-processing-with-bash


#### LATER COURSES

> https://codesignal.com/learn/paths/mastering-web-scraping-with-python-and-beautiful-soup