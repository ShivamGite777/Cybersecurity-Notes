### DNS (Domain Name System)

**DNS (Domain Name System)** is used to translate human-readable **domain names** into IP addresses.

Hum websites ke names easily remember kar sakte hain:

```text
google.com
youtube.com
github.com
```

But computers communicate using **IP addresses**.

DNS connects these two:

```text
Domain Name
     ↓
    DNS
     ↓
IP Address
     ↓
Web Server
```

### Simple Example

When you enter:

```text
example.com
```

DNS finds the IP address associated with that domain.

```text
example.com
     ↓
DNS
     ↓
IP Address
     ↓
Website Server
```

### Easy Definition

> **DNS is like the phonebook of the Internet. It converts domain names into IP addresses.**

---

# Why Do We Need DNS?

Without DNS, users would have to remember IP addresses to access websites.

Instead of:

```text
93.x.x.x
```

we can simply use:

```text
example.com
```

DNS finds the corresponding IP address automatically.

---

# DNS and OSI Model

DNS operates at:

```text
OSI Layer 7 → Application Layer
```

---

# DNS Ports

DNS normally uses:

```text
UDP → Port 53
TCP → Port 53
```

UDP is commonly used for normal DNS queries.

TCP can be used when required, such as for larger DNS responses or certain DNS operations.

### Remember

```text
DNS → Port 53
```

---

# DNS Records

DNS stores different types of records.

The important records are:

```text
A
AAAA
CNAME
MX
```

---

## 1. A Record

**A = Address Record**

An A record maps a domain/hostname to an **IPv4 address**.

```text
example.com
     ↓
172.17.2.172
```

### Remember

```text
A → IPv4
```

---

## 2. AAAA Record

An **AAAA record** maps a domain/hostname to an **IPv6 address**.

```text
example.com
     ↓
IPv6 Address
```

AAAA is pronounced **Quad-A**.

### Remember

```text
A     → IPv4
AAAA  → IPv6
```

---

## 3. CNAME Record

**CNAME = Canonical Name**

A CNAME record maps one domain name to **another domain name**.

Example:

```text
www.example.com
        ↓
example.com
```

It does not directly map the name to an IP address. It points to another domain name, which can then be resolved further.

### Remember

```text
CNAME → Name → Another Name
```

---

# 4. MX Record

**MX = Mail Exchange**

An MX record tells the Internet **which mail server handles email for a domain**.

For example:

```text
shivam@example.com
        ↓
      DNS
        ↓
    MX Record
        ↓
   Mail Server
```

So when someone sends an email to:

```text
test@example.com
```

the sending mail server checks the **MX record** for `example.com` to find the server responsible for receiving that email.

---

# Website vs Email

This is an important concept.

## Website

When you enter:

```text
example.com
```

DNS can use an **A record** to find the IPv4 address of the web server.

```text
example.com
     ↓
 A Record
     ↓
IPv4 Address
     ↓
Web Server
```

---

## Email

When you send:

```text
test@example.com
```

DNS uses the **MX record** to find the mail server responsible for receiving email for `example.com`.

```text
example.com
     ↓
 MX Record
     ↓
Mail Server
     ↓
Email Delivery
```

### Important

The **domain name itself is not the mail server**.

The domain's **DNS MX record tells mail systems which server handles its email**.

---

# Complete Example

Suppose we have:

```text
example.com
```

Its DNS could contain:

```text
A Record
example.com → 172.17.2.172

AAAA Record
example.com → IPv6 Address

CNAME Record
www.example.com → example.com

MX Record
example.com → mail.example.com
```

This means:

```text
🌐 Website

example.com
     ↓
A Record
     ↓
172.17.2.172
     ↓
Web Server
```

And:

```text
📧 Email

test@example.com
     ↓
MX Record
     ↓
mail.example.com
     ↓
Mail Server
```

---

# DNS Lookup with nslookup

We can use `nslookup` from the command line to query DNS information.

```bash
nslookup example.com
```

Conceptually:

```text
example.com
     ↓
nslookup
     ↓
DNS Server
     ↓
IP Address
```

You can also query specific record types.

### A Record

```bash
nslookup -type=A example.com
```

### MX Record

```bash
nslookup -type=MX example.com
```

### CNAME Record

```bash
nslookup -type=CNAME www.example.com
```

---

# 

| Record    | Purpose                 |
| --------- | ----------------------- |
| **A**     | Domain → IPv4           |
| **AAAA**  | Domain → IPv6           |
| **CNAME** | Domain → Another domain |
| **MX**    | Domain → Mail server    |

---






### WHOIS

**WHOIS** is a service used to look up **registration information about a domain name**.

For example:

```bash
whois example.com
```

A WHOIS lookup may provide information such as:

* **Registrar** – Company through which the domain is registered
* **Creation Date** – When the domain was registered
* **Expiration Date** – When the registration expires
* **Registrant/Organization** – Owner or organization, if publicly available
* **Domain Status** – Current status of the domain

## Purpose of WHOIS

The main purpose of WHOIS is to find **who registered a domain and information about its registration**.
It can also be useful in **cybersecurity reconnaissance** for collecting publicly available information about a domain.

## WHOIS vs DNS

```text
DNS
↓
Finds where the domain's service is
(IP address / Mail server)

WHOIS
↓
Finds domain registration information
(Registrar / Dates / Registrant details)
```

## Example

For:

```text
example.com
```

WHOIS may show:

```text
Domain Name: example.com
Registrar: Example Registrar
Creation Date: 2020-01-01
Expiration Date: 2027-01-01
Registrant: Private/Organization
```
<img width="1010" height="515" alt="image" src="https://github.com/user-attachments/assets/75fe51f4-71c3-4cfb-942d-b5275cbcfd38" />

## Important

Registrant information may be **hidden by domain privacy protection**, so the actual owner's personal details may not always be visible.

## **WHOIS = Who registered the domain + its registration details.**







###3 FTP (File Transfer Protocol)

**FTP (File Transfer Protocol)** is used to **transfer files between a client and a server**.

```text
Client  ←── FTP ──→  FTP Server
        Upload / Download
```

### FTP vs HTTP

```text
HTTP → Web pages / web data
FTP  → File transfer
```

---

## FTP Port

FTP commonly uses:

```text
TCP Port 21
```

Port 21 is mainly used for the **control connection**. File transfers and directory listings use a separate data connection.

---

## Important FTP Commands

| Command | Purpose                |
| ------- | ---------------------- |
| `USER`  | Enter username         |
| `PASS`  | Enter password         |
| `LIST`  | List files/directories |
| `PWD`   | Show current directory |
| `CWD`   | Change directory       |
| `RETR`  | Download a file        |
| `STOR`  | Upload a file          |
| `DELE`  | Delete a file          |
| `QUIT`  | Exit FTP               |
```
```

---

## Anonymous FTP

Some FTP servers allow login without a normal user account.

```text
Username: anonymous
Password: [Press Enter]
```

---

## Basic FTP Usage

### Connect

```bash
ftp 10.49.133.66
```

### List files

```text
ftp> ls
```

The FTP client may send the `LIST` command to the server.

### Download a file

```text
ftp> get flag.txt
```

Internally:

```text
get flag.txt
      ↓
RETR flag.txt
```

### Exit

```text
ftp> quit
```
## FTP Transfer Modes

### ASCII

Used mainly for text files:

```text
type ascii
```

### Binary

Used for binary files such as images, ZIP files, PDFs, etc.:

```text
binary
```


---

## Complete Command Flow

```bash
ftp 10.49.133.66
```

```text
anonymous
[Enter]

ls
get flag.txt
quit
```

Then:

```bash
cat flag.txt
```

<img width="650" height="790" alt="image" src="https://github.com/user-attachments/assets/661fd2a1-d727-435e-bc9c-eb5ff6f2aff0" />


---

## Quick Revision

```text
FTP        → File Transfer Protocol
Port 21    → FTP control connection
USER       → Username
PASS       → Password
LIST       → List files
RETR       → Download
STOR       → Upload
get        → Download using FTP client
ls         → View remote files
quit       → Exit FTP
```






