### PowerShell

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


<img width="757" height="597" alt="image" src="https://github.com/user-attachments/assets/a44cdebf-54de-4421-a2e5-b37f9cdf476d" />

