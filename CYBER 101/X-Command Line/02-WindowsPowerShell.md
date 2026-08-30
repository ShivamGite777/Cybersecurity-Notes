<img width="965" height="225" alt="image" src="https://github.com/user-attachments/assets/bc74c8eb-ef45-4b6c-bd47-3180b34a0c38" />### PowerShell

**PowerShell** is a command-line shell and scripting language developed by Microsoft.

It was created to provide better **system administration, automation, and scripting** than traditional Windows tools such as `cmd.exe` and batch files.

##  Brief History

* **Early 2000s** → Traditional Windows tools like `cmd.exe` and batch files had limitations.
* **Jeffrey Snover** → Microsoft engineer who designed the PowerShell concept.
* **2006** → PowerShell was released.
* **2016** → Microsoft released **PowerShell Core**, an open-source and cross-platform version.
* PowerShell Core can run on:

  * Windows
  * Linux
  * macOS


## Why PowerShell Was Created?

Traditional Windows command-line tools were mainly designed for simple tasks.

In large enterprise environments, administrators needed to:

* Automate tasks
* Manage many computers
* Work with Windows APIs
* Manage processes and services
* Handle structured system information
* Write powerful administration scripts

PowerShell was designed to solve these problems.


## Objects in PowerShell

One of the most important features of PowerShell is its use of **objects**.

An object contains:

* **Properties** → Information about something
* **Methods** → Actions that can be performed

###  Example: Car Object

```text
Properties:
    Color
    Model
    FuelLevel

Methods:
    Drive()
    Honk()
    Refuel()
```

PowerShell uses the same concept when managing computer resources.

### 💻 Example: File Object

A file object can contain properties such as:

```text
Name
Size
Extension
CreationTime
```

It can also provide methods for performing actions on the file.


## CMD vs PowerShell

| CMD                      | PowerShell                          |
| ------------------------ | ----------------------------------- |
| Mainly text-based        | Object-based                        |
| Basic scripting          | Powerful scripting                  |
| Limited automation       | Advanced automation                 |
| Mainly Windows-focused   | Cross-platform with PowerShell Core |
| Output is generally text | Output consists of objects          |

## CMD

```text
Command → Text Output
```

The administrator may need to **parse the text** to extract useful information.

### PowerShell

```text
Command → Object → Properties + Methods
```

Because PowerShell works with objects, information can be manipulated more easily.

# What is a Cmdlet?

A **cmdlet** is a small, specialised command used in PowerShell.

Pronunciation:

```text
cmdlet = command-let
```

# Examples
```powershell
Get-Process
Get-Service
Get-ChildItem
```

Cmdlets typically follow a:

```text
Verb-Noun
```

naming convention.

Example:

```powershell
Get-Process
```

* `Get` → action/verb
* `Process` → object/noun

---

# Why PowerShell is Important in Cybersecurity

PowerShell is widely used by system administrators and security professionals because it can:

* Manage Windows systems
* Automate security tasks
* Query system information
* Manage processes and services
* Interact with Windows APIs
* Perform administrative tasks

⚠️ **Security Note:** PowerShell is also commonly abused by attackers because it provides powerful access to Windows systems and can automate malicious activities






### PowerShell 

## Connecting with Remmina

1. Start the **Lab Machine**.
2. Start the **AttackBox**.
3. Open:

   * `Applications`
   * `Internet`
   * `Remmina`
4. Select **SSH** from the connection type.
5. Enter the target IP:

   ```text
   10.48.158.79
   ```
6. Enter the username and password.
7. Click **OK**.

> **Remmina** is a graphical client used to connect to remote machines using protocols such as SSH.

<img width="1112" height="1014" alt="image" src="https://github.com/user-attachments/assets/92b1bde4-bff7-4874-93db-a62ad9168064" />



## Launching PowerShell

PowerShell can be launched in several ways:

* **Start Menu** → Search for `PowerShell`
* **Run Dialog** → Press `Win + R` → type `powershell`
* **File Explorer** → Type `powershell` in the address bar
* **Task Manager** → File → Run new task → `powershell`
* **Command Prompt** → Type `powershell`

## Cmdlets

PowerShell commands are called **cmdlets** (pronounced *command-lets*).

Cmdlets are used to perform different tasks in PowerShell.

Examples:

```powershell
Get-Date
Get-Content
Set-Location
```

<img width="751" height="626" alt="image" src="https://github.com/user-attachments/assets/e3ef2d79-0b80-4761-a174-365fc2681c79" />

# Verb-Noun Syntax

PowerShell cmdlets normally follow the:

```text
Verb-Noun
```

format.

The **Verb** describes the action, while the **Noun** describes the object being acted upon.

### Examples

```powershell
Get-Content
Set-Location
Get-Date
Remove-Item
```

| Cmdlet         | Meaning                        |
| -------------- | ------------------------------ |
| `Get-Content`  | Gets the contents of a file    |
| `Set-Location` | Changes the current directory  |
| `Get-Date`     | Gets the current date and time |
| `Remove-Item`  | Removes an item                |

### Common PowerShell Verbs

| Verb     | Meaning  |
| -------- | -------- |
| `Get`    | Retrieve |
| `Set`    | Change   |
| `New`    | Create   |
| `Remove` | Delete   |
| `Add`    | Add      |
| `Start`  | Start    |
| `Stop`   | Stop     |

## Get-Command

`Get-Command` is used to find commands available in the current PowerShell session.

```powershell
Get-Command
```

It can display:

* Cmdlets
* Functions
* Aliases
* Scripts

Example:

```text
CommandType   Name
-----------   ----
Alias         cd
Function      A:
Cmdlet        Get-Date
Cmdlet        Get-Content
```

### Filter Commands by Type

We can filter the output using `-CommandType`.

To show only functions:

```powershell
Get-Command -CommandType Function
```
<img width="745" height="360" alt="image" src="https://github.com/user-attachments/assets/3019710e-cc51-420a-9023-cbc8c989b6dc" />

### Filter Commands by Verb

To find commands that start with the `Remove` verb:

```powershell
Get-Command -Verb Remove
```

This may show commands such as:

```text
Remove-Item
Remove-Module
Remove-Variable
```

## Get-Help

`Get-Help` is used to learn how PowerShell commands work.
<img width="760" height="738" alt="image" src="https://github.com/user-attachments/assets/d45f319d-073f-48b1-8e9b-e53a7ef55a23" />


```powershell
Get-Help
```

To get help for a specific command:

```powershell
Get-Help Get-Date
```

It provides information such as:

* Command name
* Description
* Syntax
* Parameters
* Examples
* Related commands

### Show Examples

```powershell
Get-Help Get-Date -Examples
```

### Detailed Help

```powershell
Get-Help Get-Date -Detailed
```

### Full Help

```powershell
Get-Help Get-Date -Full
```

### Online Help

```powershell
Get-Help Get-Date -Online
```

> `Get-Help` is one of the most useful commands when learning a new PowerShell cmdlet.


# 🔗 Aliases

PowerShell provides **aliases**, which are shortcuts or alternative names for commands.

Use:

```powershell
Get-Alias
```

to list available aliases.

### Common Aliases

| Alias   | Actual Cmdlet   | Purpose                |
| ------- | --------------- | ---------------------- |
| `cd`    | `Set-Location`  | Change directory       |
| `dir`   | `Get-ChildItem` | List files/directories |
| `cat`   | `Get-Content`   | Display file contents  |
| `clear` | `Clear-Host`    | Clear the screen       |

Example:

```powershell
cd C:\Users
```

is an alias for:

```powershell
Set-Location C:\Users
```

> **Alias = Shortcut for a command**

---

## PowerShell Modules

PowerShell functionality can be extended using **modules**.

A module is a collection of PowerShell commands and related functionality.

```text
Module
├── Command 1
├── Command 2
├── Command 3
└── Command 4
```

Additional modules can be found in online repositories such as the **PowerShell Gallery**.

---

## Find-Module

`Find-Module` is used to search for PowerShell modules in online repositories.

Example:

```powershell
Find-Module -Name PowerShell*
```

The `*` is a **wildcard**.

It means:

> Match anything after `PowerShell`.

For example, it can match:

```text
PowerShellGet
PowerShellForGitHub
PowerShell.Module.InvokeWinGet
```

### Wildcard Example

```powershell
Get-Command Get-*
```

This searches for commands beginning with `Get-`.

---

## Install-Module

After finding a module, we can install it using:

```powershell
Install-Module -Name PowerShellGet
```

PowerShell may ask whether you trust the repository:

```text
Untrusted repository
Are you sure you want to install the modules?
```

This is asking whether you trust the source from which the module is being installed.

> The TryHackMe machine used in this section does **not have Internet access**, so commands that need to query online repositories will not work in this environment.

##  New-LocalUser

`New-LocalUser` is a PowerShell cmdlet used to **create a new local user account** on a Windows computer.

## View Examples

To see example usage of `New-LocalUser`, use:

```powershell
Get-Help New-LocalUser -Examples
```

## Breakdown

```text
Get-Help
    ↓
Get help about a command

New-LocalUser
    ↓
The cmdlet we want to learn

-Examples
    ↓
Show usage examples
```

## Remember

```text
New-LocalUser → Create a local Windows user
```
<img width="570" height="266" alt="image" src="https://github.com/user-attachments/assets/150eb27b-069d-42d9-b9d6-6a8a2de0aec0" />



```powershell
Get-Help New-LocalUser -Examples
```

> **Purpose:** Shows practical examples of how to use the `New-LocalUser` cmdlet.


## Important Commands

| Command                             | Purpose                               |
| ----------------------------------- | ------------------------------------- |
| `powershell`                        | Start PowerShell from CMD             |
| `Get-Command`                       | List available commands               |
| `Get-Command -CommandType Function` | List only functions                   |
| `Get-Command -Verb Remove`          | List commands beginning with `Remove` |
| `Get-Help`                          | Get help about PowerShell commands    |
| `Get-Help Get-Date`                 | Get help for `Get-Date`               |
| `Get-Help Get-Date -Examples`       | Show command examples                 |
| `Get-Alias`                         | List aliases                          |
| `Get-Date`                          | Display date and time                 |
| `Get-Content`                       | Display file contents                 |
| `Set-Location`                      | Change directory                      |
| `Find-Module`                       | Search for modules                    |
| `Install-Module`                    | Install a module                      |

## How would you retrieve a list of commands that start with the verb Remove?
<img width="757" height="597" alt="image" src="https://github.com/user-attachments/assets/a44cdebf-54de-4421-a2e5-b37f9cdf476d" />










### PowerShell File System Management

PowerShell provides cmdlets for navigating and managing files and directories.

## Get-ChildItem

`Get-ChildItem` lists files and directories in a specified location.

Similar commands:

* PowerShell → `Get-ChildItem`
* Windows CMD → `dir`
* Linux/Unix → `ls`

```powershell
Get-ChildItem
```

If no path is specified, it displays the contents of the **current working directory**.

To display the contents of `C:\Users`:

```powershell
Get-ChildItem C:\Users
```

## Set-Location

`Set-Location` is used to **change the current directory**.

Similar to the `cd` command in Windows CMD.

```powershell
Set-Location -Path .\Documents
```

Example:

```text
PS C:\Users\captain>
PS C:\Users\captain\Documents>
```

## New-Item

`New-Item` is used to **create files and directories**.

### Create a Directory

```powershell
New-Item -Path .\captain-cabin\captain-wardrobe -ItemType Directory
```

### Create a File

```powershell
New-Item -Path .\captain-cabin\captain-wardrobe\captain-boots.txt -ItemType File
```

**Important:**

```text
-ItemType Directory → Creates a folder
-ItemType File      → Creates a file
```

## Remove-Item

`Remove-Item` is used to **delete files and directories**.

It can replace the Windows CMD commands `del` and `rmdir`.

### Delete a File

```powershell
Remove-Item -Path .\captain-cabin\captain-wardrobe\captain-boots.txt
```

### Delete a Directory

```powershell
Remove-Item -Path .\captain-cabin\captain-wardrobe
```

**Remember:**

```text
Remove-Item → Delete
```

## Copy-Item

`Copy-Item` is used to **copy files and directories**.

Similar to the `copy` command in Windows CMD.

```powershell
Copy-Item -Path .\captain-cabin\captain-hat.txt -Destination .\captain-cabin\captain-hat2.txt
```

This creates:

```text
captain-cabin
├── captain-hat.txt
└── captain-hat2.txt
```

The original file remains.

**Remember:**

```text
Copy-Item → Copy
```

## Move-Item

`Move-Item` is used to **move files and directories**.

Similar to the `move` command in Windows CMD.

```powershell
Move-Item -Path .\file.txt -Destination .\Documents\
```

**Remember:**

```text
Move-Item → Move
```

## Get-Content

`Get-Content` is used to **read and display the contents of a file**.

Similar commands:

* PowerShell → `Get-Content`
* Windows CMD → `type`
* Linux/Unix → `cat`

Example:

```powershell
Get-Content -Path .\captain-hat.txt
```

This displays the content stored inside `captain-hat.txt`.


## powershell
| Cmdlet          | Purpose            | CMD Equivalent   |
| --------------- | ------------------ | ---------------- |
| `Get-ChildItem` | List files/folders | `dir`            |
| `Set-Location`  | Change directory   | `cd`             |
| `New-Item`      | Create file/folder | `mkdir` / `type` |
| `Remove-Item`   | Delete file/folder | `del` / `rmdir`  |
| `Copy-Item`     | Copy file/folder   | `copy`           |
| `Move-Item`     | Move file/folder   | `move`           |
| `Get-Content`   | Read file contents | `type`           |


## Hands-on
<img width="650" height="372" alt="image" src="https://github.com/user-attachments/assets/6b716754-070c-429e-b757-ba2862dca0f0" />
<img width="527" height="51" alt="image" src="https://github.com/user-attachments/assets/5ec856fb-f55f-4f5d-8386-5ef706b4e85f" />
<img width="943" height="205" alt="image" src="https://github.com/user-attachments/assets/5f58ee66-805c-41f0-a875-6c344df0025c" />
<img width="786" height="426" alt="image" src="https://github.com/user-attachments/assets/1a641c47-49b4-49f7-b1c1-cfdbbd336990" />
<img width="782" height="87" alt="image" src="https://github.com/user-attachments/assets/f0ad89b1-daa7-42a7-8ddf-cdfe9e523596" />
<img width="768" height="352" alt="image" src="https://github.com/user-attachments/assets/55c4001d-c984-47ee-8339-402d4186f120" />
<img width="795" height="175" alt="image" src="https://github.com/user-attachments/assets/e79fdd6d-0751-49a6-bb53-668f4f6116c6" />





# PowerShell Piping & Filtering

## 1. Piping

**Piping** allows the output of one command to be used as the input of another command.

The pipe symbol is:

```powershell
|
```

### Basic Structure

```powershell
Command1 | Command2
```

Meaning:

```text
Command1
   ↓
Output
   ↓
   |
   ↓
Command2
   ↓
Result
```

### Important

In PowerShell, the pipe passes **objects**, not just text.

PowerShell objects contain:

* Data
* Properties
* Methods

This makes PowerShell piping more powerful and flexible.

---

# 2. Sort-Object

`Sort-Object` is used to **sort objects based on a property**.

### Example

```powershell
Get-ChildItem | Sort-Object Length
```

### How it works

```text
Get-ChildItem
      ↓
Gets files/folders as objects
      ↓
      |
      ↓
Sort-Object Length
      ↓
Sorts them by file size
```

`Length` is the **size of the file in bytes**.

### Descending Order

```powershell
Get-ChildItem | Sort-Object Length -Descending
```

* Default → Smallest → Largest
* `-Descending` → Largest → Smallest

---

# 3. Where-Object

`Where-Object` is used to **filter objects based on a condition**.

### Basic Structure

```powershell
Get-ChildItem | Where-Object -Property Property -eq Value
```

### Example: Find `.txt` Files

```powershell
Get-ChildItem | Where-Object -Property Extension -eq .txt
```

Meaning:

```text
Get all files
     ↓
Check Extension property
     ↓
Keep only Extension = .txt
```

So only `.txt` files are displayed.

---

# 4. Comparison Operators

PowerShell provides comparison operators for filtering objects.

| Operator | Meaning                  |
| -------- | ------------------------ |
| `-eq`    | Equal to                 |
| `-ne`    | Not equal to             |
| `-gt`    | Greater than             |
| `-ge`    | Greater than or equal to |
| `-lt`    | Less than                |
| `-le`    | Less than or equal to    |
| `-like`  | Matches a pattern        |

---

## -eq → Equal To

```powershell
Get-ChildItem | Where-Object Extension -eq .txt
```

→ Shows only `.txt` files.

---

## -ne → Not Equal

```powershell
Get-ChildItem | Where-Object Extension -ne .txt
```

→ Shows items that are **not `.txt` files**.

---

## -gt → Greater Than

```powershell
Get-ChildItem | Where-Object Length -gt 100
```

→ Shows files with a size **greater than 100 bytes**.

`-gt` is a **strict comparison**, so exactly `100` is not included.

---

## -ge → Greater Than or Equal

```powershell
Get-ChildItem | Where-Object Length -ge 100
```

→ Shows files with a size **100 bytes or greater**.

---

## -lt → Less Than

```powershell
Get-ChildItem | Where-Object Length -lt 100
```

→ Shows files with a size **less than 100 bytes**.

---

## -le → Less Than or Equal

```powershell
Get-ChildItem | Where-Object Length -le 100
```

→ Shows files with a size **100 bytes or less**.

---

# 5. -like Operator

`-like` is used to match a **pattern**.

### Example

```powershell
Get-ChildItem | Where-Object -Property Name -like ship*
```

This finds items whose names **start with `ship`**.

For example:

```text
ship-flag.txt
```

### Wildcard

```text
* = any number of characters
```

So:

```text
ship*
```

means:

```text
ship + anything
```

Examples that match:

```text
ship.txt
ship-flag.txt
ship123.txt
```

---

# 6. Select-Object

`Select-Object` is used to:

1. Select specific **properties**
2. Limit the number of **objects returned**

### Select Specific Properties

```powershell
Get-ChildItem | Select-Object Name,Length
```

Instead of displaying all properties, it displays only:

```text
Name
Length
```

### Difference Between Where-Object and Select-Object

```text
Where-Object  → Which objects?
Select-Object → Which properties?
```

Example:

```powershell
Get-ChildItem | Where-Object Extension -eq .txt
```

→ Selects **which files** to keep.

```powershell
Get-ChildItem | Select-Object Name,Length
```

→ Selects **which properties** to display.

---

# 7. Select-Object -First

`-First` limits the number of objects returned.

### Example

```powershell
Get-ChildItem | Select-Object -First 1
```

→ Returns only the **first object**.

---

# 8. Pipeline with Multiple Commands

A pipeline is not limited to two commands.

You can connect multiple cmdlets:

```powershell
Command1 | Command2 | Command3
```

Each command processes the output of the previous command.

---

# 9. Find the Largest File

To find the largest file in a directory:

```powershell
Get-ChildItem | Sort-Object Length -Descending | Select-Object -First 1
```

### Step-by-Step

```text
Get-ChildItem
      ↓
Get all files/folders
      ↓
Sort-Object Length -Descending
      ↓
Sort by size: Largest → Smallest
      ↓
Select-Object -First 1
      ↓
Take only the first item
      ↓
Largest item
```

### Meaning

> Get all items → sort them by size from largest to smallest → display only the first item.

---

# 10. Select-String

`Select-String` is used to **search for text or patterns inside files**.

It is similar to:

| PowerShell      | Windows CMD | Linux/Unix |
| --------------- | ----------- | ---------- |
| `Select-String` | `findstr`   | `grep`     |

### Example

```powershell
Select-String -Path .\captain-hat.txt -Pattern hat
```

### Breakdown

```text
Select-String
     ↓
Search text
```

```text
-Path
     ↓
File to search
```

```text
-Pattern
     ↓
Text/pattern to find
```

So:

```powershell
Select-String -Path .\captain-hat.txt -Pattern hat
```

means:

> Search inside `captain-hat.txt` for the pattern `hat`.

Example result:

```text
captain-hat.txt:8:Don't touch my hat!
```

Meaning:

```text
captain-hat.txt → File
8               → Line number
Don't touch...  → Matching line
```

---

# 11. Regular Expressions

`Select-String` supports **regular expressions (regex)**.

Regex allows you to perform more advanced and complex pattern matching.

For example, instead of searching for one exact word, regex can be used to search for different patterns.

---

### Commands

```powershell
# List files and folders
Get-ChildItem

# Sort by size
Get-ChildItem | Sort-Object Length

# Sort largest first
Get-ChildItem | Sort-Object Length -Descending

# Filter .txt files
Get-ChildItem | Where-Object Extension -eq .txt

# Filter files larger than 100 bytes
Get-ChildItem | Where-Object Length -gt 100

# Find names starting with ship
Get-ChildItem | Where-Object Name -like ship*

# Select only Name and Length
Get-ChildItem | Select-Object Name,Length

# Get the first object
Get-ChildItem | Select-Object -First 1

# Find largest file
Get-ChildItem | Sort-Object Length -Descending | Select-Object -First 1

# Search text inside a file
Select-String -Path .\captain-hat.txt -Pattern hat
```

---

##  Concept

```text
Get-ChildItem
      ↓
     |
      ↓
Where-Object     → Filter
      ↓
     |
      ↓
Sort-Object      → Sort
      ↓
     |
      ↓
Select-Object    → Select
      ↓
     |
      ↓
Final Result
```


##  Hands-on




<img width="772" height="282" alt="image" src="https://github.com/user-attachments/assets/2eeb6f17-53d5-4191-8285-96f077c95cf7" />


<img width="968" height="237" alt="image" src="https://github.com/user-attachments/assets/a23ee797-e8ba-4e92-a90a-6d3be536c12a" />


<img width="985" height="170" alt="image" src="https://github.com/user-attachments/assets/c2659382-b678-4255-a0fd-eea033769556" />


<img width="868" height="160" alt="image" src="https://github.com/user-attachments/assets/e87f7ef9-ebce-4596-885b-49985b90db8f" />


<img width="965" height="225" alt="image" src="https://github.com/user-attachments/assets/4b0d709a-7d83-4919-bc62-353b56b59556" />


<img width="953" height="77" alt="image" src="https://github.com/user-attachments/assets/ff5506f7-c7b1-409b-86eb-0e2738c0219e" />



