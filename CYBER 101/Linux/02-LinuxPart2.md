### SSH (Secure Shell)
**SSH (Secure Shell)** is a protocol used to securely connect to and manage a **remote computer** through a terminal.

It encrypts the connection, so data such as commands and passwords are protected while being transmitted.

## Why is SSH Used?

- Connect to remote Linux servers
- Execute commands remotely
- Manage servers through the terminal
- Transfer files securely
- Perform remote administration

## SSH Syntax

```bash
ssh <username>@<IP-address>
```
# ls
<img width="727" height="153" alt="image" src="https://github.com/user-attachments/assets/c604adda-04bf-4b06-8589-ff84351fcf21" />


## `ls -a`

`ls` normally shows the **visible** files and directories.
The `-a` option means **all**, so it also shows **hidden files and directories**.

### Command

```bash
ls -a
```bash
ls -a
```
<img width="697" height="146" alt="image" src="https://github.com/user-attachments/assets/3b609902-8975-4618-8a00-4a7be5aa4aef" />

## ls --help
<img width="802" height="690" alt="image" src="https://github.com/user-attachments/assets/310967b6-971d-4bc6-a0bf-fd88f71907c0" />

## man ls

<img width="776" height="677" alt="image" src="https://github.com/user-attachments/assets/d5325d2d-2c17-4976-9675-241814969522" />

## `touch`

`touch` is used to **create a new empty file**

```bash
touch <filename>
```
<img width="730" height="140" alt="image" src="https://github.com/user-attachments/assets/73d2a985-7ddf-4531-aba9-4ca1a541e191" />

## `mkdir`

`mkdir` stands for **Make Directory**. It is used to **create a new folder/directory**.

```bash
mkdir <directory-name>
```

<img width="700" height="148" alt="image" src="https://github.com/user-attachments/assets/85d518e6-d65f-48d8-8753-5b3cd655eefe" />

## Removing Files 

<img width="718" height="147" alt="image" src="https://github.com/user-attachments/assets/6625619b-b782-42f6-98a2-46bac7dfe0cc" />

## Removing folder
<img width="748" height="142" alt="image" src="https://github.com/user-attachments/assets/27579d80-14c1-4eea-b46d-13c0da775fdf" />

## Copying Files

cp copies the entire contents of the existing file into the new file. In the screenshot below, we are copying "note" to "note2"
1. the name of the existing file
2. the name we wish to assign to the new file when copying.

  <img width="715" height="147" alt="image" src="https://github.com/user-attachments/assets/31885475-79d8-46af-a998-c5a227e09246" />
 
## Moving Files and Folders 

Moving a file takes two arguments, just like the cp command. However, rather than copying and/or creating a new file, mv will merge or modify the second file that we provide as an argument. Not only can you use mv to move a file to a new folder, but you can also use mv to rename a file or folder. For example, in the screenshot below, we are renaming the file "note2" to be named "note3". "note3" will now have the contents of "note2". 
<img width="725" height="155" alt="image" src="https://github.com/user-attachments/assets/b677ce21-f18c-49b7-a212-9fa06c947d32" />


## Determining File Type

<img width="725" height="123" alt="image" src="https://github.com/user-attachments/assets/b648ed57-506e-4878-9ce5-76d847c4b1dd" />
