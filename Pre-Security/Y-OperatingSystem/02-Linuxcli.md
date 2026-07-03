
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

<img width="741" height="142" alt="image" src="https://github.com/user-attachments/assets/1c4ae62b-b73f-4d4f-a6bc-a1b6486bc832" />


#  2. ls (List Files)

Displays files and folders in the current directory.

```bash
ls
```
Example:

```text
Desktop  Documents  Downloads
```
<img width="752" height="156" alt="image" src="https://github.com/user-attachments/assets/d1da3d8f-9a98-414e-bb52-c86cd02dd386" />

# 3. ls -l (Long Listing)

Shows detailed information about files.

```bash
ls -1

<img width="683" height="458" alt="image" src="https://github.com/user-attachments/assets/d2e030ed-3fc1-46ea-a313-df1283dce076" />

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
<img width="733" height="455" alt="image" src="https://github.com/user-attachments/assets/4ff1e3d3-6f21-46d3-8be0-ea3a8df46c89" />

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
<img width="706" height="150" alt="image" src="https://github.com/user-attachments/assets/60214ad8-fbc0-4a7c-8789-cc9d0be14d72" />


### Go Back One Directory

```bash
cd ..
```
<img width="737" height="156" alt="image" src="https://github.com/user-attachments/assets/9e5d95dc-cc44-4819-96c3-703b25fa7344" />


#  6. find (Search Files)

Search for files by name.

Syntax:

```bash
find <starting_directory> -name <filename>
```
<img width="728" height="135" alt="image" src="https://github.com/user-attachments/assets/601999a9-6a5c-424e-8629-4808dafc5ada" />


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
<img width="756" height="433" alt="image" src="https://github.com/user-attachments/assets/791b9a5e-adda-43a0-8896-a631edde77f9" />


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
