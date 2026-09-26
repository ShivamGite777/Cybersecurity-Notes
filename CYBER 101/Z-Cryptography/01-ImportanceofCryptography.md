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





# Historical Ciphers

Cryptography has been around for a very long time. One of the simplest old ciphers is the **Caesar Cipher**, used around the 1st century BCE.

## Caesar Cipher

The Caesar Cipher works by **shifting each letter by a fixed number**.

Example:

```text
Plaintext: TRYHACKME
Key: 3
Cipher: Caesar Cipher
```

A right shift of 3 means:

```text
T → W
R → U
Y → B
```

When we reach `Z`, we start again from `A`.

So:

```text
TRYHACKME
   ↓ Shift by 3
WUBKDFNPH
```

Therefore:

```text
Plaintext  → TRYHACKME
Ciphertext → WUBKDFNPH
Key        → 3
```

## Decryption

For decryption, we do the opposite shift.

```text
Ciphertext → WUBKDFNPH
Key        → 3
      ↓
Shift left by 3
      ↓
Plaintext → TRYHACKME
```

So:

```text
Encryption:  Right shift
Decryption:  Left shift
```

## Why is Caesar Cipher Insecure?

There are only **25 useful keys**.

The alphabet has 26 letters, but shifting by 26 brings every letter back to itself.

So an attacker can simply try all possible keys. This is called a **brute-force attack**.

```text
Ciphertext
    ↓
Try Key 1
Try Key 2
Try Key 3
...
Try Key 25
    ↓
Find readable message
```

Because there are so few possible keys, Caesar Cipher is **not secure by today's standards**.

## Other Historical Ciphers

Some other well-known historical ciphers are:

* **Vigenère Cipher** — 16th century
* **Enigma Machine** — World War II
* **One-Time Pad** — Cold War

[https://cryptii.com](url)



# Types of Encryption

# Symmetric Encryption

Symmetric encryption is one of the two main types of encryption.

The other one is **asymmetric encryption**.

## What is Symmetric Encryption?

Symmetric encryption uses the **same key** for both encryption and decryption.

```text
             Same Secret Key 🔑
                    ↓
Plaintext → Encryption → Ciphertext
                              ↓
                         Decryption
                              ↓
                           Plaintext
                    ↑
             Same Secret Key 🔑
```
<img width="1840" height="1040" alt="image" src="https://github.com/user-attachments/assets/29cc95dc-96a9-49bf-9036-2c9ed87472a4" />

### Simple Example

```text
Plaintext:  HELLO
Key:        12345

HELLO → Encryption → X7@P2
```

To get `HELLO` back:

```text
X7@P2 → Decryption + Key → HELLO
```

So the main point is:

> **Same key is used to encrypt and decrypt the data.**

## Private Key Cryptography

Symmetric encryption is also called **private key cryptography** because the key must be kept secret.

If someone gets the key, they may be able to decrypt the protected data.

## Main Problem: Key Sharing

The biggest problem is **how to securely share the secret key** with the other person.

Example:

```text
You 🔑 ────────?────────> Friend
```

You need to get the key to your friend without an attacker getting it.

This becomes even harder when there are many people communicating.

```text
1 friend     → Easy
100 people   → Much harder to manage keys
```

A powerful attacker could try to steal or intercept the keys, for example during industrial espionage.

## Flow

```text
Symmetric Encryption
        ↓
Same key for encryption + decryption
        ↓
Key must stay secret
        ↓
Main challenge = Securely sharing the key
```

**Easy definition:**

> Symmetric encryption = **one shared secret key used by both sides.**

```
```
## password-sharing problem

In symmetric encryption, both sides need the **same secret key**.

Imagine you encrypt a document and send it to your friend:

```text
🔒 Encrypted Document
        ↓
      Email
        ↓
     Friend
```

Sending the encrypted document by email is fine.

But you should not send the password through the **same email**:

```text
Email
 ├── 🔒 Encrypted document
 └── 🔑 Password
```

If someone gets access to the mailbox, they get both the document and the password.

So, the password should be shared through a **different secure channel**.

For example:

```text
Email → Send encrypted document
In-person → Share the password
```

# Examples of Symmetric Encryption

Some well-known symmetric encryption algorithms are:

* **DES** — Data Encryption Standard
* **3DES** — Triple DES
* **AES** — Advanced Encryption Standard

## DES

**DES** was adopted as a standard in **1977**.

* Key size: **56 bits**
* It became weak as computers became more powerful.
* In 1999, a DES key was successfully broken in less than 24 hours.
* This led to the move towards stronger methods such as 3DES.

```text
DES
↓
56-bit key
↓
Too weak today
```

---

## 3DES

**3DES (Triple DES)** applies DES three times.

```text
Data
 ↓
DES
 ↓
DES
 ↓
DES
 ↓
Encrypted Data
```

* Key size: **168 bits**
* Effective security: **112 bits**
* Mainly used as a temporary replacement for DES.
* Deprecated in **2019**.
* Can still be found in some old/legacy systems.

---

## AES

**AES (Advanced Encryption Standard)** became a standard in **2001**.

AES supports three key sizes:

```text
AES-128 → 128-bit key
AES-192 → 192-bit key
AES-256 → 256-bit key
```

AES is the main modern symmetric encryption algorithm to remember from this section.

---

## Comparison

| Algorithm |          Key Size | Status          |
| --------- | ----------------: | --------------- |
| DES       |            56-bit | Old / insecure  |
| 3DES      |          168-bit* | Deprecated      |
| AES       | 128, 192, 256-bit | Modern standard |



# Asymmetric Encryption

Asymmetric encryption uses **two different keys**:

* **Public Key**
* **Private Key**

Unlike symmetric encryption, the same key is **not** used for both encryption and decryption.

## How It Works

For confidentiality:

```text
Plaintext
    ↓
Public Key
    ↓
Encryption
    ↓
Ciphertext
    ↓
Private Key
    ↓
Decryption
    ↓
Plaintext
```

### Public Key

The **public key can be shared with everyone**.

It is used to encrypt data intended for the key owner.

### Private Key

The **private key must be kept secret**.

It is used to decrypt data that was encrypted with the corresponding public key.

```text
Public Key  → Share it
Private Key → Keep it secret
```

## Example

If Alice wants to send a secret message to Bob:

```text
Alice
  ↓
Bob's Public Key
  ↓
Encrypt
  ↓
Ciphertext
  ↓
Bob's Private Key
  ↓
Decrypt
  ↓
Original Message
```
<img width="1840" height="1040" alt="image" src="https://github.com/user-attachments/assets/2004cc18-6c6c-4d1e-bba1-c49f4a0b4646" />

The important part is that Bob does **not** need to send his private key to Alice.

## Common Examples

* **RSA**
* **Diffie-Hellman**
* **ECC (Elliptic Curve Cryptography)**

## Key Sizes

Asymmetric algorithms generally use larger keys and are slower than symmetric encryption.

### RSA

```text
2048-bit
3072-bit
4096-bit
```

2048-bit is the recommended minimum key size mentioned in this section.

### ECC

ECC can provide similar security with much smaller keys.

Example:

```text
256-bit ECC ≈ 3072-bit RSA
```

## Main Idea

Asymmetric encryption is based on mathematical problems that are easy to calculate in one direction but extremely difficult to reverse.

## Alice and Bob

In cryptography examples:

```text
Alice = Person A
Bob   = Person B
```

They are simply names used to represent two people communicating.

## Remember

```text
Symmetric:
Same key → Encryption + Decryption

Asymmetric:
Two keys

Public Key  → Can be shared
Private Key → Must be kept secret
```
## Symmetric vs Asymmetric Encryption

### Symmetric Encryption

Uses the **same key** for encryption and decryption.

```text
Same Key
   ↓
Encrypt + Decrypt
```

### Asymmetric Encryption

Uses **two different keys**:

```text
Public Key  → Encrypt
Private Key → Decrypt
```

### Easy Difference

```text
Symmetric   → 1 key
Asymmetric  → 2 keys
```
