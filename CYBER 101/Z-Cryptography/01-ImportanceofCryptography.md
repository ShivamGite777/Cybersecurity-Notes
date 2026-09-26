# Cryptography Basics

**Cryptography** is the practice of protecting information from attackers and unauthorized people.

The main purpose of cryptography is to allow **secure communication even when attackers may be present**.

An attacker may try to:

* Read the information
* Steal the information
* Change the information
* Pretend to be someone else

Cryptography provides techniques to protect against these problems.

### Simple Example

Without protection:

```text
You → "My password is 12345" → Server
             ↑
          Attacker
```

With encryption:

```text
You → "X7#kP9@..." → Server
             ↑
          Attacker
```

The attacker may see the communication, but the actual information is protected.

---

# Main Goals of Cryptography

Cryptography mainly helps provide:

1. **Confidentiality**
2. **Integrity**
3. **Authenticity**

---

## 1. Confidentiality

**Confidentiality means keeping information secret.**

Only authorized people or systems should be able to read the information.

### Example

```text
Your Password
     ↓
🔒 Encryption
     ↓
Server
```

If an attacker monitors the network, they should not be able to simply read the password.

###  **Confidentiality = Only authorized people can read the data.**

---

## 2. Integrity

**Integrity means making sure that data has not been changed or tampered with.**

For example, suppose you send:

```text
Transfer ₹1,000
```

An attacker should not be able to secretly change it to:

```text
Transfer ₹10,000
```

without the change being detected.

### **Integrity = Data should remain unchanged and trustworthy.**

---

## 3. Authenticity

**Authenticity means verifying that something is really from the person or system it claims to be from.**

For example, when you visit your bank's website, your browser can check the website's **digital certificate** to help verify the server's identity.

### **Authenticity = Verify who or what you are communicating with.**

---

# Cryptography in Daily Life

We use cryptography almost every day without directly interacting with it.

Common examples:

* HTTPS websites
* SSH
* Online banking
* Secure messaging
* File hashes
* Digital certificates

Most cryptographic operations happen **in the background**.

---

# Example 1: Logging in to TryHackMe

When you log in to TryHackMe, your credentials are sent to the server through a secure connection.

```text
Your Computer
      ↓
🔒 Encrypted Connection
      ↓
TryHackMe Server
```

This helps prevent someone monitoring the network from simply reading your credentials.

### Main Concept

**Confidentiality**

---

# Example 2: SSH

**SSH = Secure Shell**

SSH allows you to securely connect to a remote computer.

```text
Your Computer
      ↓
🔒 Encrypted SSH Connection
      ↓
Remote Server
```

The encrypted connection helps prevent attackers from simply reading your commands and the server's responses while monitoring the network.

### Main Concept

**Secure Communication**

---

#  Example 3: Online Banking

When you visit your bank's website, your browser needs to have confidence that it is communicating with the correct server.

The server provides a **digital certificate**.

The browser can check the certificate and its trust chain.

```text
Browser
   ↓
"Are you really the bank's server?"
   ↓
Certificate Verification
   ↓
Server Identity Information
```

This helps provide **authentication/authenticity**.

### Main Concept

**Authenticity**

---

# Example 4: File Hashes

Suppose you download a file.

You want to know:

> Is the downloaded file the same as the original file?

A **hash function** can help check this.

### Original File

```text
Original File
     ↓
   Hash
     ↓
ABC123
```

### Downloaded File

```text
Downloaded File
       ↓
     Hash
       ↓
ABC123
```

If the hashes match, this provides evidence that the downloaded file has not been changed.

If the hashes are different:

```text
Original     → ABC123
Downloaded   → XYZ789
```

the files are not identical.

### Main Concept

**Integrity**

---

# Data at Rest

**Data at rest** means data that is currently stored somewhere.

Examples:

* Database
* Hard drive
* Cloud storage
* Backup

Example:

```text
Database
   ↓
Customer Information
   ↓
🔒 Protected
```

Sensitive data may need to be protected with appropriate security controls, including encryption where required.

### **Data at rest = Stored data**

---

# 🚀 Data in Motion / Data in Transit

**Data in motion** or **data in transit** means data that is travelling from one system to another.

Example:

```text
Your Computer
      ↓
🔒 Network
      ↓
Server
```

The data needs protection while travelling across the network.

### **Data in motion = Data travelling between systems**

---

# PCI DSS

**PCI DSS = Payment Card Industry Data Security Standard**

Suppose a company handles customers' credit-card information.

Because payment-card information is sensitive, organizations handling it may need to follow PCI DSS requirements.

PCI DSS addresses security of payment-card data when it is:

* Stored
* Processed
* Transmitted

### Simple Idea

```text
Credit Card Data
       ↓
Security Requirements
       ↓
Protection
```

---

# Medical Records and Security

Medical records also contain sensitive information.

Different countries and regions have different laws and regulations for handling healthcare information.

Examples mentioned in this topic:

* **HIPAA** → United States
* **HITECH** → United States
* **GDPR** → European Union
* **DPA** → United Kingdom

These rules can require organizations to apply appropriate security protections when handling sensitive information.

---

# Why Are Laws and Regulations Mentioned?

Cryptography is not only a technical concept.

Organizations that handle sensitive information may also have **legal and regulatory requirements** for protecting that information.

For example:

```text
Sensitive Data
      ↓
Security Requirements
      ↓
Encryption + Other Security Controls
      ↓
Data Protection
```

---

# Important Terms

| Term                | Simple Meaning                               |
| ------------------- | -------------------------------------------- |
| Cryptography        | Techniques used to protect information       |
| Confidentiality     | Keeping data secret                          |
| Integrity           | Making sure data was not changed             |
| Authenticity        | Verifying identity/source                    |
| Encryption          | Converting readable data into protected form |
| Hash                | A value used to help verify data integrity   |
| Digital Certificate | Helps verify a server's identity             |
| Data at Rest        | Stored data                                  |
| Data in Motion      | Data travelling across a network             |
| PCI DSS             | Security standard for payment-card data      |
| HIPAA               | US healthcare privacy/security law           |
| HITECH              | US healthcare technology/privacy law         |
| GDPR                | EU data protection regulation                |
| DPA                 | UK data protection legislation               |

---

# Summary

```text
                 CRYPTOGRAPHY
                      │
       ┌──────────────┼──────────────┐
       ↓              ↓              ↓
Confidentiality   Integrity     Authenticity
       ↓              ↓              ↓
 Keep data        Detect       Verify identity
   secret          changes
```






# Cryptography Basic Terms

## Basic Flow

```text
Plaintext + Key
      ↓
  Encryption
      ↓
 Ciphertext
```

### Plaintext

Plaintext is the **original readable data** that we want to protect.

It can be:

* `Hello`
* A photo
* Credit card details
* Medical records
* A file

Example:

```text
Hello Shivam
```

This is plaintext because we can read it.

### Encryption

Encryption is the process of converting **plaintext into ciphertext** using an encryption algorithm and a key.

```text
Plaintext + Key → Encryption → Ciphertext
```

### Ciphertext

Ciphertext is the **encrypted form of the plaintext**.

Example:

```text
Plaintext:
Hello

        ↓ Encryption

Ciphertext:
x7@K91#p
```

We should not be able to understand the original message just by looking at the ciphertext.

### Key

A key is a value used by the encryption algorithm to encrypt or decrypt data.

```text
Plaintext + Key
      ↓
  Encryption
      ↓
 Ciphertext
```

### Cipher

A cipher is the **algorithm/rules used to convert plaintext into ciphertext and back**.

```text
Encryption:
Plaintext → Ciphertext

Decryption:
Ciphertext → Plaintext
```


<img width="1160" height="640" alt="image" src="https://github.com/user-attachments/assets/10a1eb48-4911-4637-afba-e5735db29b02" />
<img width="1160" height="640" alt="image" src="https://github.com/user-attachments/assets/6b82c0e6-e3ff-4151-babf-02c566235473" />
