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

