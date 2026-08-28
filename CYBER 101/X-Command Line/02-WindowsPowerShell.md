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

⚠️ **Security Note:** PowerShell is also commonly abused by attackers because it provides powerful access to Windows systems and can automate malicious activities.
