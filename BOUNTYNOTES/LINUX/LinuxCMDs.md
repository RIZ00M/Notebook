# Linux Commands

## Misc

| Command | Purpose |
|---|---|
| `echo` | Relay text to the CLI |

## History

| Command | Purpose |
|---|---|
| `history` | Shows history of commands |
| `history -c && history -w` | Clear full history |
| `history -d 1234` | Clear a specific history entry |

## Shells

| Command | Purpose |
|---|---|
| `bash` | Swap to the Bourne Again shell |
| `zsh` | Swap to the Z shell |
| `fish` | Swap to the Friendly Interactive Shell |
| `chsh -s /usr/bin/zsh` | Change your default shell |

## Permissions

| Command | Purpose |
|---|---|
| `sudo su` | Switch to root |
| `chmod +x first_script.sh` | Add execute permission |
| `chmod -x first_script.sh` | Remove execute permission |

## Navigation

| Command | Purpose |
|---|---|
| `pwd` | Show current directory |
| `ls` | List directory contents |
| `cd` | Change directory |

## File Interaction

| Command | Purpose |
|---|---|
| `cat` | Quick view of a file |
| `more` | Full, paginated view of a file |
| `nano` | Nano text editor |
| `grep THM directory.txt` | Find content in a file |

## Scripting

### Variables

```bash
#!/bin/bash
echo "Hey, what's your name?"
read name
echo "Welcome, $name"
```

### Loops

```bash
#!/bin/bash
for i in {1..10};
do
    echo $i
done
```

### Conditions

```bash
#!/bin/bash
echo "Please enter your name first:"
read name
if [ "$name" = "Stewart" ]; then
    echo "Welcome Stewart! Here is the secret: THM_Script"
else
    echo "Sorry! You are not authorized to access the secret."
fi
```

### Multi-Input Example (Username / Company / PIN)

```bash
#!/bin/bash
# Defining the variables
username=""
companyname=""
pin=""

# Defining the loop
for i in {1..3}; do
    # Defining the conditional statements
    if [ "$i" -eq 1 ]; then
        echo "Enter your Username:"
        read username
    elif [ "$i" -eq 2 ]; then
        echo "Enter your Company name:"
        read companyname
    else
        echo "Enter your PIN:"
        read pin
    fi
done

# Checking if the user entered the correct details
if [ "$username" = "John" ] && [ "$companyname" = "Tryhackme" ] && [ "$pin" = "7385" ]; then
    echo "Authentication Successful. You can now access your locker, John."
else
    echo "Authentication Denied!!"
fi
```

### Flag Search Example

```bash
#!/bin/bash

# Defining the directory to search our flag
directory="/var/log"

# Defining the flag to search
flag="thm-flag01-script"

echo "Flag search in directory: $directory in progress..."

# Defining for loop to iterate over all the files with .log extension in the defined directory
for file in "$directory"/*.log; do
    # Check if the file exists (handles cases where no .log files are found)
    [ -f "$file" ] || continue

    # Check if the file contains the flag
    if grep -q "$flag" "$file"; then
        # Print the filename
        echo "Flag found in: $(basename "$file")"
    fi
done
```
