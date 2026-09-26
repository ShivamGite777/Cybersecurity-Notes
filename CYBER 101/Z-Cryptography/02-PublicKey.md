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
