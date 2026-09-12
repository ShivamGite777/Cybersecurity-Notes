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

