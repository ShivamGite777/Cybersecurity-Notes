
###  Linux CLI Navigation Notes

##  Terminal

The **Terminal** is a text-based interface used to interact with Linux by typing commands.

### Why use the Terminal?

 Faster than using the GUI
 Gives more control
 Many cybersecurity tools run only in the terminal

#  1. pwd (Print Working Directory)

Shows your current directory.

bash
pwd
Example:

text
/home/ubuntu

# 📂 2. ls (List Files)

Displays files and folders in the current directory.

```bash
ls
```
Example:

```text
Desktop  Documents  Downloads
```

# 3. ls -l (Long Listing)

Shows detailed information about files.

```bash
ls -l
```

Displays:
 File permissions
 Owner
 File size
 Date modified
 File nam

# 4. ls -al (Show Hidden Files)

Lists all files, including hidden ones.

```bash
ls -al
```

### Hidden Files

 Begin with a `.` (dot)
 Hidden by default in Linux
Example:

```text
.bashrc
.profile
```
# In order to get the hidden files in the directory, we can append the command to ls -al, and it will display all the hidden files present in the directory, as shown below:


# 5. cd (Change Directory)
Move into another directory.

```bash
cd Documents
```

Example:

```text
/home/ubuntu/Documents
```

### Go Back One Directory

```bash
cd ..
```

#  6. find (Search Files)

Search for files by name.

Syntax:

```bash
find <starting_directory> -name <filename>
```

Example:

```bash
find ~ -name mission_brief.txt
```

Output:

```text
/home/ubuntu/Documents/.research/archive/mission_brief.txt
```

**`~` = Home Directory**


#  7. cat (Read File)

Displays the contents of a file.

```bash
cat mission_brief.txt
```

Example:

```text
FLAG: THM{...}
```

#  Key Commands Summary

| Command | Purpose |
|---------|---------|
| `pwd` | Show current directory |
| `ls` | List files/folders |
| `ls -l` | Detailed file listing |
| `ls -al` | Show hidden files |
| `cd <folder>` | Change directory |
| `cd ..` | Go back one directory |
| `find ~ -name file` | Search for a file |
| `cat file` | Display file contents |


#  Memory Tricks

 **pwd** → **P**rint **W**orking **D**irectory
 **ls** → **L**i**s**t files
 **cd** → **C**hange **D**irectory
 **cat** → Read file contents
 **find** → Search for files
 **~** → Home directory
 **..** → Parent directory
