<img width="1232" height="383" alt="image" src="https://github.com/user-attachments/assets/3a396ad0-7128-412f-b961-573f2386743d" /><img width="915" height="451" alt="image" src="https://github.com/user-attachments/assets/c6e66724-adff-43ed-ab2f-f6f0c6a69be0" />### Active Directory
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


