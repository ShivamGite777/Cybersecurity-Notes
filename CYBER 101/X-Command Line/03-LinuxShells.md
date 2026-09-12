### Linux Shell

A **Linux Shell** is a command-line interface (CLI) that allows us to interact with the Linux operating system by typing commands.

Most Linux distributions use **Bash (Bourne Again Shell)** as the default shell.

Example shell prompt:

```bash
user@tryhackme:~$
```

* `user` → current username
* `tryhackme` → hostname
* `~` → current home directory
* `$` → indicates a normal user

---

## Basic Linux Shell Commands

| Command | Meaning                         | Purpose                   |
| ------- | ------------------------------- | ------------------------- |
| `pwd`   | Print Working Directory         | Show current directory    |
| `cd`    | Change Directory                | Move to another directory |
| `ls`    | List                            | Show files and folders    |
| `cat`   | Concatenate                     | Display file contents     |
| `grep`  | Global Regular Expression Print | Search for text/patterns  |

### Linux Shells — Bash, Fish & Zsh

## What is a Shell?

A **shell** is a program that interprets the commands we type and communicates with the Linux operating system.

```text
User
 ↓
Terminal
 ↓
Shell
 ↓
Linux
```

The **Terminal** is where we type commands, while the **Shell** understands and executes those commands.

---








## Types of Linux Shells

Linux has different types of shells. The most common ones are:

* **Bash**
* **Fish**
* **Zsh**

All of them allow us to run Linux commands, but they provide different features.

---

## 1. Bash

**Bash = Bourne Again Shell**

Bash is the most commonly used Linux shell and is the default shell on many Linux distributions.

### Example

```bash
echo "Hello"
```

Output:

```text
Hello
```

### Key Features

* Very widely used
* Excellent scripting support
* Command history
* Tab completion
* Reliable and commonly available

**Remember:**

> Bash = Common + reliable + great for scripting

---

## 2. Fish

**Fish = Friendly Interactive Shell**

Fish focuses on making the command-line experience easier and more user-friendly.

### Example

```fish
echo "Hello"
```

Output:

```text
Hello
```

### Key Features

* User-friendly
* Auto suggestions
* Auto spell correction
* Built-in syntax highlighting
* Tab completion
* Customizable

**Remember:**

> Fish = Easy + friendly + helpful suggestions

---

## 3. Zsh

**Zsh = Z Shell**

Zsh is a powerful and highly customizable shell.

### Example

```zsh
echo "Hello"
```

Output:

```text
Hello
```

### Key Features

* Advanced tab completion
* Auto spell correction
* Command history
* Scripting support
* Plugins and themes
* Highly customizable

**Remember:**

> Zsh = Powerful + customizable

### Bash Scripting 

## 1. Shell Script

A **shell script** is a file containing multiple commands.

```text
Commands → Script → Run once → Tasks execute
```

Used for **automation**.

---

## 2. Bash

**Bash** = Bourne Again Shell.

It is a common Linux shell used to run commands and scripts.

```bash
bash
```

---

## 3. `.sh`

`.sh` is the common file extension for shell scripts.

```text
script.sh
```

---

## 4. Shebang

```bash
#!/bin/bash
```

Tells Linux:

> Use **Bash** to run this script.

---

## 5. `nano`

```bash
nano script.sh
```

`nano` → terminal text editor.

Used to **create/edit** a script.

---

## 6. `echo`

```bash
echo "Hello"
```

`echo` → **prints/displays** text.

---

## 7. Variable

A variable **stores a value**.

```bash
name="Shivam"
```

Use it with `$`:

```bash
echo "$name"
```

Output:

```text
Shivam
```

---

## 8. `read`

```bash
read name
```

`read` → takes **user input** and stores it in `name`.

Example:

```bash
echo "Enter name:"
read name
echo "Hello $name"
```

---

## 9. `chmod`

```bash
chmod +x script.sh
```

Gives the script **execute permission**.

```text
chmod → change permission
+x    → add execute permission
```

---

## 10. `./`

```bash
./script.sh
```

`./` → tells Linux to run the script from the **current directory**.

---

## 11. Loop

A loop **repeats commands**.

```bash
for i in {1..5}
do
    echo $i
done
```

Output:

```text
1
2
3
4
5
```

```text
for  → start loop
do   → start action
done → end loop
```

---

## 12. Condition

A condition makes a **decision**.

```bash
if [ "$name" = "Shivam" ]; then
    echo "Allowed"
else
    echo "Denied"
fi
```

```text
if   → check condition
else → if condition is false
fi   → end condition
```

---

## 13. Comment

```bash
# This is a comment
```

`#` → comment.

Comments are **not executed**. They explain the code.

---

## Basic Workflow

nano first_script.sh
        ↓
write code
        ↓
CTRL+X → Y → ENTER
        ↓
chmod +x first_script.sh
        ↓
./first_script.sh





### Bash Scripting — Task

## Create a Script

```bash
nano first_script.sh
```

Creates/opens a Bash script file.

## Shebang

```bash
#!/bin/bash
```

Tells Linux to use **Bash** to run the script.

## Basic Script

```bash
#!/bin/bash

echo "What's your name?"
read name
echo "Welcome, $name"
```

* `echo` → prints text
* `read` → takes user input
* `$name` → uses the variable value

## Give Execute Permission

```bash
chmod +x first_script.sh
```

Makes the script executable.

* `chmod` → change permission
* `+x` → add execute permission

## Run the Script

```bash
./first_script.sh
```

`./` → run the script from the **current directory**.

## Loop

```bash
for i in {1..10}
do
    echo $i
done
```

Prints numbers from `1` to `10`.

* `for` → start loop
* `do` → start actions
* `done` → end loop

## Condition

```bash
if [ "$name" = "Stewart" ]; then
    echo "Allowed"
else
    echo "Denied"
fi
```

* `if` → check condition
* `else` → if condition is false
* `fi` → end condition

## Comments

```bash
# This is a comment
```

`#` → comment; not executed.




### Bash Locker Authentication Script

## Purpose

This script verifies a user's details before allowing access to a locker.

# Correct Details

```text
Username: John
Company: Tryhackme
PIN: 7385
```

If **all details are correct** → Access Allowed.
If **any detail is wrong** → Access Denied.

---

## Script

```bash
#!/bin/bash

# Variables
username=""
companyname=""
pin=""

# Loop runs 3 times
for i in {1..3}; do

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

# Check all details
if [ "$username" = "John" ] && [ "$companyname" = "Tryhackme" ] && [ "$pin" = "7385" ]; then
    echo "Authentication Successful. You can now access your locker, John."
else
    echo "Authentication Denied!!"
fi
```

---

## How It Works

```text
Start
  ↓
Ask Username
  ↓
Ask Company Name
  ↓
Ask PIN
  ↓
Check all details
  ↓
All correct?
 ├── Yes → Authentication Successful
 └── No  → Authentication Denied
```

## Important Commands

| Command       | Meaning                           |
| ------------- | --------------------------------- |
| `#!/bin/bash` | Use Bash                          |
| `echo`        | Display text                      |
| `read`        | Take user input                   |
| `username=""` | Create variable                   |
| `for`         | Repeat                            |
| `if`          | Check condition                   |
| `elif`        | Check another condition           |
| `else`        | If previous condition is false    |
| `fi`          | End `if` statement                |
| `done`        | End loop                          |
| `-eq`         | Equal to (numbers)                |
| `=`           | Compare text                      |
| `&&`          | AND — all conditions must be true |

## Example Execution

```text
$ ./locker_script.sh

Enter your Username:
John

Enter your Company name:
Tryhackme

Enter your PIN:
1349

Authentication Denied!!
```

### Why Denied?

```text
Username: John       ✅
Company: Tryhackme   ✅
PIN: 1349            ❌

Result → Authentication Denied!!
```

> `&&` means all three details must be correct for successful authentication.






> ## Task



# Flag Hunt — Q1

## Task

Find the `.log` file in `/var/log` containing:

```text
thm-flag01-script
```

## Steps

Become root:

```bash
sudo su
```

Open the script:

```bash
nano flag_hunt.sh
```

Set the values:

```bash
directory="/var/log"
flag="thm-flag01-script"
```

Run the script:

```bash
chmod +x flag_hunt.sh
./flag_hunt.sh
```

## Output

```text
Flag found in: authentication.log
```

## Answer

**authentication.log**


Q2. Where is the cat sleeping?

To search for the word cat inside /var/log:

grep -Rni "cat" /var/log 2>/dev/null
Command Breakdown
grep        → Search text
-R          → Search recursively
-n          → Show line number
-i          → Ignore uppercase/lowercase
"cat"       → Text to search
/var/log    → Directory to search
2>/dev/null → Hide error messages
Example Output
/var/log/example.log:25:The cat is sleeping under the table.
