### Active Directory
Picture yourself administering a small business network with only five computers and five employees. In such a tiny network, you will probably be able to configure each omputer separately without a problem. You will manually log into each computer, create users for whoever will use them, and make specific configurations for each employee's accounts. If a user's computer stops working, you will probably go to their place and fix the computer on-site.

While this sounds like a very relaxed lifestyle, let's suppose your business suddenly grows and now has 157 computers and 320 different users located across four different offices. Would you still be able to manage each computer as a separate entity, manually configure policies for each of the users across the network and provide on-site support for everyone? The answer is most likely no.

To overcome these limitations, we can use a Windows domain. Simply put, a Windows domain is a group of users and computers under the administration of a given business. The main idea behind a domain is to centralise the administration of common components of a Windows computer network in a single repository called Active Directory (AD). The server that runs the Active Directory services is known as a Domain Controller (DC).


<img width="452" height="362" alt="image" src="https://github.com/user-attachments/assets/18f3c6f9-13f7-4c22-8333-60de7a513f62" />

 ### Advantages
 ##  Centralised Identity Management

AD manages users and accounts from **one central location**.

- Create/manage users
- Reset passwords
- Manage groups
- Control access

```text
Active Directory
      ↓
Users + Computers
```

##  Security Policies

AD allows administrators to apply **security policies** to users and computers across the network.

Examples:

- Password policies
- Account lockout
- Security settings
- Access restrictions

```text
AD
 ↓
Group Policy
 ↓
Users + Computers
```

### A Real-World Example

If this sounds a bit confusing, chances are that you have already interacted with a Windows domain at some point in your school, university or work.

In school/university networks, you will often be provided with a username and password that you can use on any of the computers available on campus. Your credentials are valid for all machines because whenever you input them on a machine, it will forward the authentication process back to the Active Directory, where your credentials will be checked. Thanks to Active Directory, your credentials don't need to exist in each machine and are available throughout the network.

Active Directory is also the component that allows your school/university to restrict you from accessing the control panel on your school/university machines. Policies will usually be deployed throughout the network so that you don't have administrative privileges over those computers.

### Active Directory 

**Active Directory (AD)** is a centralized system used by organizations to manage:

- 👤 Users
- 💻 Computers
- 👥 Groups
- 🔐 Permissions
- ⚙️ Security policies
- 📁 Network resources

```text
             Active Directory
                    ↓
       ┌────────────┼────────────┐
       ↓            ↓            ↓
     Users       Computers      Groups
       ↓            ↓            ↓
   Accounts         PCs      Permissions
```

---

## 👤 Users

AD stores user accounts for employees and services.

```text
User
 ↓
Login to Domain
 ↓
Access Resources
```

---

## 💻 Computers

When a Windows computer joins the domain, AD creates a **computer account**.

Example:

```text
Computer: PC01
AD Account: PC01$
```

> `$` at the end usually indicates a **machine account**.

## 👥 Security Groups

Groups are used to manage **permissions** for multiple users/computers.

```text
Sales Group
Sales Users → Access ✅
```

> A user can belong to **multiple groups**.

## 📂 Organizational Units (OUs)

An **OU** is like a folder inside Active Directory used to organize users and computers.

Example:

```text
THM
├── IT
├── Sales
├── Marketing
└── Management
```

OUs are mainly used to:

- Organize users/computers
- Apply **Group Policies**

# OU = "What policies should apply to this user/computer?"

# Security Group = "What resources should this user be allowed to access?"

<img width="415" height="675" alt="image" src="https://github.com/user-attachments/assets/7315ebab-8d7d-4c5c-b446-95b363118e70" />
<img width="915" height="451" alt="image" src="https://github.com/user-attachments/assets/7b903379-b9c5-4f3a-b78f-924ec6f45c28" />
<img width="913" height="451" alt="image" src="https://github.com/user-attachments/assets/2541ecaf-f1b4-4f9b-a207-adbd9df41ee6" />
<img width="1232" height="383" alt="image" src="https://github.com/user-attachments/assets/d54b0005-b1e9-416b-94e2-306e90d29800" />

## in Active Directory, computer accounts follow a specific naming convention.
Computer name + $ = Machine Account

So:

TOM-PC → TOM-PC$ 

### Deleting extra OUs and users

The first thing you should notice is that there is an additional department OU in your current AD configuration that doesn't appear in the chart. We've been told it was closed due to budget cuts and should be removed from the domain. If you try to right-click and delete the OU, you will get the following error:

<img width="1542" height="702" alt="image" src="https://github.com/user-attachments/assets/6ce7e068-aa98-4228-ba18-d33499ca033f" />
### By default, OUs are protected from accidental deletion.
### Steps

1. Open **Active Directory Users and Computers (ADUC)**.
2. Go to **View → Advanced Features**.
3. Right-click the unwanted OU → **Properties**.
4. Open the **Object** tab.
5. Uncheck:
   `Protect object from accidental deletion`
6. Click **Apply → OK**.
7. Right-click the OU → **Delete**.
8. Confirm the deletion.


<img width="404" height="159" alt="image" src="https://github.com/user-attachments/assets/87dcc9be-9188-46ea-8a5f-2a3c2d4286ca" />
<img width="1000" height="777" alt="image" src="https://github.com/user-attachments/assets/c32d3d1f-80a4-47b3-97b5-0a843680b63d" />
<img width="935" height="692" alt="image" src="https://github.com/user-attachments/assets/8456c3e3-c115-4e8b-a6f8-3d2b33ba455a" />
<img width="754" height="417" alt="image" src="https://github.com/user-attachments/assets/4a4e5974-e1ef-4144-952a-8fec25afa735" />
<img width="420" height="472" alt="image" src="https://github.com/user-attachments/assets/a492a34c-530a-48fe-bef8-8b9e05ad81fe" />



### Delegation

One of the nice things you can do in AD is to give specific users some control over some OUs. This process is known as delegation and allows you to grant users specific privileges to perform advanced tasks on OUs without needing a Domain Administrator to step in.

One of the most common use cases for this is granting IT support the privileges to reset other low-privilege users' passwords. According to our organisational chart, Phillip is in charge of IT support, so we'd probably want to delegate the control of resetting passwords over the Sales, Marketing and Management OUs to him.

For this example, we will delegate control over the Sales OU to Phillip. To delegate control over an OU, you can right-click it and select Delegate Control:

<img width="311" height="372" alt="image" src="https://github.com/user-attachments/assets/fdae4ae0-61a7-4272-aa78-95c59898ea10" />
<img width="583" height="570" alt="image" src="https://github.com/user-attachments/assets/668b12d5-3c37-4b1a-97ca-caa8d75518f7" />
<img width="531" height="414" alt="image" src="https://github.com/user-attachments/assets/3dbad524-14b1-4a16-a9c3-94769d2efabb" />
### practical
## Active Directory — Password Reset Delegation
The task is to delegate password-reset permission to Phillip for the Sales OU, so Phillip can reset passwords of Sales users like Sophie without being a Domain Administrator.
# Password Reset with Delegation

Phillip has delegated permission to reset passwords for users in the **Sales OU**.

# 1. Login as Phillip

```bash
xfreerdp /v:10.48.158.214 /u:'THM\phillip' /p:'Claire2008' /cert:ignore
```
# 2. Reset Sophie's Password

Run this command in **Phillip's PowerShell**:

```powershell
Set-ADAccountPassword sophie -Reset -NewPassword (Read-Host -AsSecureString -Prompt 'New Password') -Verbose
```
## 3  Run as Administrator:

Set-ADUser -Identity sophie -ChangePasswordAtLogon $false
## 4. Now leave Phillip

Go back to the AttackBox terminal and connect as Sophie:

xfreerdp /v:10.48.158.214 /u:'THM\sophie' /p:'Shivam@02' /cert:ignore

##
Phillip resets Sophie's password
        ↓
Password = Shiv@02 ✅
        ↓
ChangePasswordAtLogon = FALSE
        ↓
No password-change requirement ✅
        ↓
RDP as THM\sophie
        ↓
Sophie's Desktop 
win  + r
<img width="1027" height="852" alt="image" src="https://github.com/user-attachments/assets/624088ba-e1c4-4c5e-8eb5-dc4fff10ac4e" />
<img width="1028" height="501" alt="image" src="https://github.com/user-attachments/assets/861f4feb-359d-4434-b90f-bf979f30427a" />
<img width="1037" height="857" alt="image" src="https://github.com/user-attachments/assets/1446d5d8-9f01-43e7-8754-17a664d4fbbd" />

### Organising Computers into OUs

## Default Computers Container

By default, domain-joined machines (except **Domain Controllers**) are placed in the **Computers** container.
This can become difficult to manage because different machines require different security policies.

## Types of Machines

### 1. Workstations
- Employee PCs and laptops.
- Used for normal work and browsing.
- Privileged accounts should **not** be used on them.

### 2. Servers
- Provide services to users or other servers.
- Require stricter security policies.

### 3. Domain Controllers (DCs)
- Manage the Active Directory domain.
- Contain sensitive information such as password hashes.
- Are already placed in a dedicated OU by Windows.

## Organising the AD

Create two new OUs directly under `thm.local`:

```text
thm.local
├── Workstations
├── Servers
└── Domain Controllers
```
<img width="754" height="417" alt="image" src="https://github.com/user-attachments/assets/1e44cdca-3469-4659-9351-ae1d9fb65047" />
<img width="754" height="366" alt="image" src="https://github.com/user-attachments/assets/6ebd6720-7e0b-445e-9ef1-f813d1098c78" />
