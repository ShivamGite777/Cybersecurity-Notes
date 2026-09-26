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
