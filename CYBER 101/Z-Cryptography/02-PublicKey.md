# Using Asymmetric and Symmetric Encryption Together

Symmetric encryption is **fast**, but it has one main problem:

> Both sides need the same secret key.

So the question is:  


**How can we safely establish a symmetric key without sending it openly over the network?**

## Basic Idea

Asymmetric cryptography can be used for the **initial key exchange/establishment**.

```text
Asymmetric Encryption
        ↓
Establish / agree on a secret key
        ↓
Symmetric Encryption
        ↓
Fast encrypted communication
```  

### Why use both?

* **Asymmetric** → Slower, but useful for secure key establishment.
* **Symmetric** → Faster, so it is used for the actual data communication.

---

## Lock Analogy

Imagine the server gives you a lock.

```text
Lock        → Public Key
Lock's Key  → Private Key
Secret Code → Symmetric Key
```

The public key can be shared, while the private key stays with the server.

The secret code represents the symmetric encryption key that will be used for communication.

```text
Client
  ↓
Uses server's Public Key
  ↓
Protects the Symmetric Key
  ↓
Server
  ↓
Uses its Private Key
  ↓
Gets the Symmetric Key
```

Now both sides can use the symmetric key for fast communication.

---

## Real-World Idea

In a secure connection, asymmetric cryptography is used during the **initial setup**, rather than for encrypting all the data.

After the secure key establishment:

```text
Client 🔐 ←── Symmetric Encryption ──→ Server
```

This is faster than using asymmetric encryption for every piece of data.

## Authentication

There is another problem:

> How do we know the server is actually the real server?

**Digital signatures and certificates** help verify the identity of the server.

## Remember

```text
Asymmetric → Initial setup / key establishment
Symmetric  → Fast data communication

Public Key  → Can be shared
Private Key → Must be kept secret

Certificates + Digital Signatures
→ Help verify identity
```

### Simple Flow

```text
Client
  ↓
Server's Public Key
  ↓
Secure Key Establishment
  ↓
Shared Symmetric Key
  ↓
Fast Encrypted Communication
```




# RSA

**RSA (Rivest–Shamir–Adleman)** is a **public-key encryption algorithm** used to securely transmit data over insecure networks.

It is an example of **asymmetric cryptography**, meaning it uses:

* **Public Key** → can be shared
* **Private Key** → must be kept secret


## Working of RSA 

RSA security is based on the mathematical difficulty of **factoring very large numbers**.

The basic idea is:

```text
Two large prime numbers
        ↓
     Multiply
        ↓
Very large number
```

Multiplying two large prime numbers is relatively easy.

However, given only the resulting large number, finding the **two original prime factors** can be extremely difficult when the numbers are sufficiently large.

### Simple Example

```text
113 × 127 = 14351
```

It is easy to calculate:

```text
113 × 127 → 14351
```

But RSA uses extremely large prime numbers, so reversing the process becomes computationally difficult:

```text
Very large number → ? × ?
```

## Why is RSA Secure?

An attacker may know the public information, but recovering the private information would require solving a computationally difficult mathematical problem.

```text
Large Prime A × Large Prime B
            ↓
       Large Number
            ↓
   Difficult to factor
```

## Key Point

> RSA relies on the computational difficulty of factoring very large numbers.

RSA is mainly used for **secure key exchange, encryption, and digital signatures**, although modern systems often combine RSA or other asymmetric cryptography with faster symmetric encryption.



# RSA – Numerical Example

RSA uses a **public key for encryption** and a **private key for decryption**.

## Numerical Example

### 1. Choose two prime numbers

```text
p = 157
q = 199
```

Calculate `n`:

```text
n = p × q
  = 157 × 199
  = 31243
```

`n` is used in both the public and private keys.

### 2. Calculate φ(n)

```text
φ(n) = n - p - q + 1
     = 31243 - 157 - 199 + 1
     = 30888
```

`φ(n)` is just a calculated value used to generate `e` and `d`.

Bob chooses:

```text
e = 163
d = 379
```
### 3. Choose e and d:


```text
e = 163
d = 379
```
They satisfy:

e × d mod φ(n) = 1
### It simply means e and d are chosen so that their multiplication gives remainder 1 when divided by φ(n).
The keys are:

```text
Public Key  = (n, e)
            = (31243, 163)

Private Key = (n, d)
            = (31243, 379)
```

### 3. Encryption

Alice wants to send:

```text
m = 13
```

She uses Bob's **public key**:

```text
c = m^e mod n

c = 13^163 mod 31243
c = 16341
```

So the encrypted message is:

```text
c = 16341
```

### 4. Decryption

Bob receives:

```text
c = 16341
```

He uses his **private key**:

```text
m = c^d mod n

m = 16341^379 mod 31243
m = 13
```

Bob gets the original message back:

```text
13 → 16341 → 13
```

## RSA Variables for CTFs

| Variable | Meaning                        |
| -------- | ------------------------------ |
| `p`      | First prime number             |
| `q`      | Second prime number            |
| `n`      | `p × q`                        |
| `e`      | Public exponent                |
| `d`      | Private exponent               |
| `m`      | Original message / plaintext   |
| `c`      | Encrypted message / ciphertext |

### Important Formulas

```text
n = p × q

Public Key  = (n, e)
Private Key = (n, d)

Encryption:
c = m^e mod n

Decryption:
m = c^d mod n
```

## RSA in CTFs

In RSA CTF challenges, you may be given some of these values:

```text
p, q, n, e, d, c
```

The goal is usually to **find the missing value or decrypt the ciphertext to recover the flag**.

### Main Flow

```text
Public Key
(n, e)
   ↓
Encryption
   ↓
Ciphertext (c)
   ↓
Private Key
(n, d)
   ↓
Decryption
   ↓
Message (m)
```





# Diffie-Hellman Key Exchange
**Diffie-Hellman (DH)** is a method used by two parties to create a **shared secret key over an insecure network**.
 **Diffie-Hellman allows two parties to create the same secret key without directly sending that secret key over the network.**

The secret key is **not directly sent** between them.

The shared secret can later be used for **symmetric encryption**.

---

## Numerical Example

### 1. Public Values

Alice and Bob agree on two public values:

```text
p = 29
g = 3
```

These values are **not secret**.

### 2. Private Values

Alice chooses:

```text
a = 13
```

Bob chooses:

```text
b = 15
```

These values must remain **secret**.

### 3. Generate Public Keys

Alice:

```text
A = g^a mod p
  = 3^13 mod 29
  = 19
```

Bob:

```text
B = g^b mod p
  = 3^15 mod 29
  = 26
```

So:

```text
Alice's Public Key = 19
Bob's Public Key   = 26
```

They exchange these public keys.

### 4. Calculate Shared Secret

Alice uses Bob's public key and her private key:

```text
B^a mod p
= 26^13 mod 29
= 10
```

Bob uses Alice's public key and his private key:

```text
A^b mod p
= 19^15 mod 29
= 10
```

Both get:

```text
Shared Secret = 10
```

### Complete Flow

```text
Alice                              Bob

Private = 13                    Private = 15
    ↓                                ↓
Public = 19                     Public = 26
    └──────── exchange ────────────┘
              ↓
       Shared Secret = 10
```

## Important Points

* `p` and `g` → **public**
* `a` and `b` → **private**
* `A` and `B` → **public keys**
* `10` → **shared secret**
* The shared secret is **never directly sent**
* The shared secret can be used for **symmetric encryption**
<img width="1560" height="1180" alt="image" src="https://github.com/user-attachments/assets/330ec2e7-745b-4cf5-8dc9-c71b0642525f" />






# SSH Server Authentication

When connecting to a server using SSH, SSH checks the **server's public key** to make sure we are connecting to the correct server.
**SSH uses the server's public-key fingerprint to verify the server's identity and detect unexpected key changes.**

## SSH Example

```bash
ssh 10.10.244.173
```

SSH may show:

```text
The authenticity of host can't be established.
ED25519 key fingerprint is SHA256:...
Are you sure you want to continue?
```

### What is a Fingerprint?

A **fingerprint** is a short representation of the server's public key.

SSH shows it so the user can verify the server's identity.
The server has a public key. SSH shows you a short version of that key called a fingerprint.

You are basically being asked:

"Do you trust that this public key belongs to the server you are trying to connect to?"

### What happens when we type `yes`?

```text
yes
 ↓
SSH saves the server's public key
 ↓
Stored in known_hosts
```

Next time:

```text
Server sends key
      ↓
SSH compares it with saved key
      ↓
Matches → Connect
Different → Warning
```

### Why is this useful?

It helps detect a possible **Man-in-the-Middle (MITM)** attack.

```text
You → Attacker → Real Server
```

If an attacker tries to pretend to be the server and provides a different key, SSH can warn you.

> **SSH uses the server's public-key fingerprint to verify the server's identity and detect unexpected key changes.**




# SSH Client Authentication

SSH authentication answers:

> **"Is this user allowed to log in to the server?"**

SSH can use:

* Username + password
* Public/private key authentication

## Public & Private Keys

SSH can use a **key pair** to authenticate the client.

```text
Private Key → Keep ONLY with yourself 🔒
Public Key  → Give/store on the server
```

Think of it like:

```text
Public Key  = Lock
Private Key = Secret key that opens/proves ownership of the lock
```

The private key is **never sent to the server**. SSH uses cryptography to prove that you have the matching private key.

---

## Generate SSH Keys

Use:

```bash
ssh-keygen -t ed25519
```

### Meaning

```text
ssh-keygen → Program used to generate SSH keys
-t         → Select the key type
ed25519    → Key algorithm
```

It generates two files:

```text
id_ed25519       → Private Key 🔒
id_ed25519.pub   → Public Key
```

### Important

```text
Private key → NEVER share
Public key  → Can be shared with the server
```

---

## Passphrase

During key generation, SSH asks:

```text
Enter passphrase:
```

A **passphrase protects the private key file**.

So if someone gets your private key file, they may still need the passphrase to use it.

---

## Key Algorithms

SSH supports different key algorithms:

```text
RSA
DSA
ECDSA
ECDSA-SK
Ed25519
Ed25519-SK
```



## SSH Authentication Flow

```text
1. Generate key pair
        ↓
2. Private Key + Public Key
        ↓
3. Put Public Key on the server
        ↓
4. Keep Private Key with yourself
        ↓
5. Connect using SSH
        ↓
6. Server verifies that you have the matching Private Key
        ↓
7. Access granted
```

## Key Point

> **The public key is stored on the server, while the private key stays secret with the user. SSH uses the private key to prove that the user is authorized.**


# SSH Client Authentication

SSH client authentication is used to prove that **you are an authorized user** of the server.
The public key is stored on the server, while the private key stays secret on your machine. SSH uses cryptographic proof to verify that you possess the matching private key.
## Example Setup

```text
Your Laptop = Client
Server      = 192.168.1.100
Username    = shivam
```

## 1. Generate SSH Key Pair

Run on your laptop:

```bash
ssh-keygen -t ed25519
```

This creates two files:

```text
~/.ssh/id_ed25519
        ↓
Private Key 🔒

~/.ssh/id_ed25519.pub
        ↓
Public Key
```

### Important

```text
Private Key → Keep on your machine and NEVER share
Public Key  → Can be shared with the server
```

---

## 2. Copy Public Key to Server

```bash
ssh-copy-id shivam@192.168.1.100
```

The public key is stored on the server in:

```text
/home/shivam/.ssh/authorized_keys
```

The **private key is not copied** to the server.

---

## 3. Connect to the Server

```bash
ssh shivam@192.168.1.100
```

The server checks whether you have the **private key that matches the public key** stored on the server.

```text
Your Laptop                         Server
     │                                 │
     │──── SSH connection ────────────>│
     │                                 │
     │<──── Prove your identity ──────│
     │                                 │
     │──── Cryptographic proof ───────>│
     │                                 │
     │       Key matches               │
     │<────────────────────────────────│
     │                                 │
     │          LOGIN SUCCESS          │
```

The private key itself is **never sent** to the server.

---

## 4. Passphrase

When generating the key, SSH may ask:

```text
Enter passphrase:
```

Example:

```text
MySecretPass123
```

The passphrase adds protection to your **private key file**.
The passphrase does NOT authenticate you to the SSH server.

It only protects your private key locally.

The passphrase:

is not sent to the server
does not leave your computer
is not the SSH account password


```text
Private Key
     ↓
Protected by Passphrase
     ↓
More secure
```

---

## 5. What Can Be Shared?

### Public Key

```text
id_ed25519.pub
```

Can be shared with the server.

### Private Key

```text
id_ed25519
```

Must remain secret.

```text
Public Key  → Shareable
Private Key → NEVER SHARE 🔒
```

If someone gets your private key, they may be able to authenticate as you.

---

## Simple Analogy

Think of a padlock:

```text
Public Key  = Padlock 🔒
Private Key = Secret Key 🔑
```

The server has the **public key**, while you keep the **private key**.

The server uses the public key to verify that you have the matching private key.

---

## Complete Flow

```text
1. Generate Key Pair
        ↓
2. Public Key + Private Key
        ↓
3. Public Key → Server
        ↓
4. Private Key → Stays on your machine
        ↓
5. SSH Login
        ↓
6. Server verifies your identity
        ↓
7. Access Granted
```

## Key Point

> **The public key is stored on the server, while the private key stays secret on your machine. SSH uses cryptographic proof to verify that you possess the matching private key.**




# SSH `chmod` and `-i`

## 1. `chmod`

`chmod` means **change file permissions**.

For an SSH private key:

```bash
chmod 600 id_ed25519
```

This protects the private key so that **only the owner can read and write it**.

### Permission Numbers

```text
4 = Read
2 = Write
1 = Execute
0 = No permission
```

`600` means:

```text
6 = Read + Write
0 = No permission
0 = No permission
```

So:

```text
Owner  → Read + Write ✅
Group  → No access ❌
Others → No access ❌
```

### Why `600`?

The SSH private key is **secret**, so other users should not be able to read it.

SSH may refuse to use a private key if its permissions are too open.

---

## 2. `-i` Option

`-i` is an option of the `ssh` command.

It tells SSH **which private key to use for authentication**.

```bash
ssh -i id_ed25519 shivam@192.168.1.100
```

### Breakdown

```text
ssh            → SSH program
-i             → Specify private key
id_ed25519     → Private key file
shivam         → Username
192.168.1.100  → Server
```

### Example with Multiple Keys

Suppose you have:

```text
~/.ssh/
├── id_ed25519
├── college_key
└── ctf_key
```

To use `ctf_key`:

```bash
ssh -i ctf_key user@10.10.10.10
```

SSH will use `ctf_key` as the private key.

---

## Easy Difference

```text
chmod → "Who can access my private key file?"

-i    → "Which private key should SSH use?"
```


## ~/.ssh Directory

The default SSH directory on Linux is:

~/.ssh/

It can contain files such as:

~/.ssh/
├── id_ed25519          → Private key
├── id_ed25519.pub      → Public key
├── authorized_keys     → Public keys trusted by server
└── known_hosts         → Server keys remembered by client

## authorized_keys as a Backdoor
```text
The file:

~/.ssh/authorized_keys

contains public keys that are allowed to authenticate to that user's account.

If an attacker adds their own public key:

Attacker's Public Key
        ↓
~/.ssh/authorized_keys
        ↓
Attacker can potentially log in later
        ↓
Using matching Private Key

Therefore, unexpected entries in authorized_keys can be a security concern/backdoor.

Check the file with:

cat ~/.ssh/authorized_keys
```

## John the Ripper
```text
If an SSH private key is protected with a passphrase, tools such as John the Ripper can be used to attempt to crack the passphrase.

Encrypted Private Key
        ↓
John the Ripper
        ↓
Attempts to find passphrase

This is why you should use a strong passphrase and keep your private key secure.
```



## Important Commands
```bash
Generate an Ed25519 key
ssh-keygen -t ed25519
Generate an RSA key
ssh-keygen -t rsa
Copy public key to server
ssh-copy-id user@host
Protect private key
chmod 600 private_key
Use a specific private key
ssh -i private_key user@host
View authorized public keys
cat ~/.ssh/authorized_keys
Check the first line of a key
head -n 1 private_key
```
Example:

-----BEGIN RSA PRIVATE KEY-----

→ Key uses RSA.


## Final Things to Remember
```bash
~/.ssh/
    ↓
Default SSH directory

authorized_keys
    ↓
Public keys trusted by the server

known_hosts
    ↓
Server keys remembered by the client

ssh-copy-id
    ↓
Copies public key to server

chmod 600
    ↓
Protects private key permissions

ssh -i
    ↓
Specifies private key for SSH login

Fingerprint
    ↓
Short identifier of a key

John the Ripper
    ↓
Can attempt to crack encrypted SSH key passphrases
```
# SSH Password Authentication

SSH can authenticate a user using a **username and password**.

## Basic Command

```bash
ssh user@target-ip
```

Example:

```bash
ssh user@10.49.166.236
```

### What Happens?

```text
Client
   ↓
ssh user@10.49.166.236
   ↓
Server asks for password
   ↓
Enter user's password
   ↓
Server verifies password
   ↓
Login successful ✅
```


# SSH Key Authentication

SSH can authenticate a user using a **public/private key pair** instead of a password.

## 1. Generate SSH Key Pair

```bash
ssh-keygen -t ed25519
```

This creates:

```text
~/.ssh/id_ed25519
        ↓
Private Key 🔒

~/.ssh/id_ed25519.pub
        ↓
Public Key
```

* **Private key** → stays on your machine and must never be shared.
* **Public key** → can be copied to the server.

If the key already exists, you can use the existing key.

---

## 2. Copy Public Key to Server

```bash
ssh-copy-id user@target-ip
```

Example:

```bash
ssh-copy-id user@10.49.166.236
```

Enter the **target user's password** when asked.

The public key is added to:

```text
~/.ssh/authorized_keys
```

The private key is **never copied** to the server.

---

## 3. Login Using SSH Key

```bash
ssh user@target-ip
```

Example:

```bash
ssh user@10.49.166.236
```

SSH uses the private key to prove that you have the key matching the public key stored on the server.

```text
Client                         Server
Private Key 🔒                 Public Key
     │                              │
     │──── Cryptographic proof ────>│
     │                              │
     │<──── Authentication OK ──────│
     │                              │
     │          Login ✅             │
```

The private key itself is **not sent** to the server.

---

## 4. Use a Specific Private Key

If you have multiple keys:

```bash
ssh -i ~/.ssh/id_ed25519 user@target-ip
```

`-i` tells SSH **which private key to use**.

---

## 5. Protect the Private Key

```bash
chmod 600 ~/.ssh/id_ed25519
```

`600` means:

```text
Owner  → Read + Write
Group  → No access
Others → No access
```

SSH may refuse to use a private key if its permissions are too open.

---

## 6. Check Your Public Key

```bash
cat ~/.ssh/id_ed25519.pub
```

Never share the contents of:

```text
~/.ssh/id_ed25519
```

because that is your **private key**.

---

## Complete Hands-on Flow

```text
1. ssh-keygen -t ed25519
          ↓
   Generate key pair

2. ssh-copy-id user@target-ip
          ↓
   Public key → Server

3. ssh user@target-ip
          ↓
   SSH verifies your private key
          ↓
   Login ✅
```

## Easy Difference

```text
Public Key  → Stored on server
Private Key → Stays on your machine 🔒
ssh-copy-id → Copies public key
ssh          → Connects to server
-i           → Selects private key
chmod 600    → Protects private key
```
# SSH Private Key — Task 5

## Check the Private Key

Go to the Task-5 directory:

```bash
cd ~/Public-Crypto-Basics/Task-5
```

List the files:

```bash
ls
```

Example:

```text
id_rsa_1593558668558.id_rsa
```

Check the first line of the private key:

```bash
head -n 1 id_rsa_1593558668558.id_rsa
```

If it shows:

```text
-----BEGIN RSA PRIVATE KEY-----
```

### Answer

**Algorithm: RSA**
<img width="946" height="335" alt="image" src="https://github.com/user-attachments/assets/22f0ad6d-43ec-4002-b6c7-9a198d562f5c" />






# Digital Signatures & Certificates

## 1. Digital Signature

A **digital signature** is used to verify the **authenticity and integrity** of a digital document or message.

It answers two questions:

* **Authenticity:** Who signed/created it?
* **Integrity:** Was it changed after signing?

### Basic idea

```text
Private Key → Create Digital Signature
Public Key  → Verify Digital Signature
```

The **private key must remain secret**.

---

## 2. How Digital Signatures Work

Instead of signing the entire document, a **hash** of the document is normally signed.

```text
Document
   ↓
Hash
   ↓
Sign hash using Private Key
   ↓
Digital Signature
```

The sender shares:

```text
Original Document + Digital Signature
```

The receiver uses the sender's **public key** to verify the signature and compares the document's hash.

If the document was modified, the hash will be different and verification will fail.

---

## 3. Digital Signature vs Electronic Signature

### Electronic Signature

Example:

```text
Pasting an image of a handwritten signature
```

Anyone can copy and paste the image, so it does not provide cryptographic proof of integrity.

### Digital Signature

Uses **cryptography and keys**:

```text
Private Key → Sign
Public Key  → Verify
```

It provides cryptographic verification of the signature and document integrity.

---

# Certificates

## 4. What is a Certificate?

A **digital certificate** is used to prove the identity of a website or other entity.

Example:

```text
Browser
   ↓
HTTPS website
   ↓
TLS Certificate
   ↓
"This certificate belongs to this website"
```

Certificates are commonly used with **HTTPS/TLS**.

---

## 5. Certificate Authority (CA)

**CA = Certificate Authority**

A CA is a trusted organisation that issues/signs digital certificates.

Your browser and operating system already contain a list of trusted **Root CAs**.

---

## 6. Chain of Trust

Certificates work through a **chain of trust**.

```text
Root CA
   ↓
Intermediate CA
   ↓
Website Certificate
   ↓
Website
```

The browser trusts the website certificate because it can trace the certificate back to a trusted CA.

---

## 7. HTTPS + Certificates

When you visit an HTTPS website:

```text
Browser
   ↓
HTTPS/TLS
   ↓
Website Certificate
   ↓
Certificate verification
   ↓
Secure connection
```

The certificate helps the browser verify the website's identity.

---

## 8. Let's Encrypt

**Let's Encrypt** provides **free TLS certificates** for domains you control.

It allows websites to use HTTPS without paying for a certificate.

---

