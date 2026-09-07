**MISC**

echo - relay text to the CLI



**HISTORY**

history - history of commands

history -c \&\& history -w - clear full history

history -d 1234 - clear history specific



**SHELLS**

bash - swap bourne again shell

zsh - swap z-shell 

fish - swap friendly interactive shell

chsh -s /usr/bin/zsh 



**PERMISSIONS**

sudo su

chmod +x first\_script.sh - add execution

chmos -x first\_script.sh - remove execution



**NAVIGATION**

pwd - current directory

ls - list directories

cd - change directory



**FILE INTERACTION**
cat - quick view of a file

more - full view of a file

nano - nano editor

grep THM directory.txt - find content in a file

**SCRIPTING**

```bash

\# Variables

\#!/bin/bash

echo "Hey, what’s your name?"

read name

echo "Welcome, $name"

```



```bash

\# Loops

\#!/bin/bash

for i in {1..10};

do

echo $i

done

```



```bash

\# Conditions

\#!/bin/bash

echo "Please enter your name first:"

read name

if \[ "$name" = "Stewart" ]; then

&#x20;  	echo "Welcome Stewart! Here is the secret: THM\_Script"

else

&#x09;echo "Sorry! You are not authorized to access the secret."

fi

```



```bash

\# Defining the Interpreter 

\#!/bin/bash 

\# Defining the variables

username=""

companyname=""

pin=""

\# Defining the loop

for i in {1..3}; do

\# Defining the conditional statements

&#x20;       if \[ "$i" -eq 1 ]; then

&#x20;               echo "Enter your Username:"

&#x20;               read username

&#x20;       elif \[ "$i" -eq 2 ]; then

&#x20;               echo "Enter your Company name:"

&#x20;               read companyname

&#x20;       else

&#x20;               echo "Enter your PIN:"

&#x20;               read pin

&#x20;       fi

done

\# Checking if the user entered the correct details

if \[ "$username" = "John" ] \&\& \[ "$companyname" = "Tryhackme" ] \&\& \[ "$pin" = "7385" ]; then

&#x20;       echo "Authentication Successful. You can now access your locker, John."

else

&#x20;       echo "Authentication Denied!!"

fi

```



```bash

\#!/bin/bash



\# Defining the directory to search our flag

directory="/var/log"



\# Defining the flag to search

flag="thm-flag01-script"



echo "Flag search in directory: $directory in progress..."



\# Defining for loop to iterate over all the files with .log extension in the defined directory

for file in "$directory"/\*.log; do

&#x20;   # Check if the file exists (handles cases where no .log files are found)

&#x20;   \[ -f "$file" ] || continue



&#x20;   # Check if the file contains the flag

&#x20;   if grep -q "$flag" "$file"; then

&#x20;       # Print the filename

&#x20;       echo "Flag found in: $(basename "$file")"

&#x20;   fi

done

```

