
### Cryptography 
Cryptography is the practice of protecting information by converting readable data into an unreadable form so that unauthorized people cannot understand it.

##  Important Terms

# Plaintext
The original, readable message.

Example:
`HELLO`

# Ciphertext
The encrypted, unreadable version of the message.

Example:
`KHOOR`

## Key
A secret value used to encrypt and decrypt data.

Think of it like a **password**.

# Algorithm
A set of rules used to encrypt and decrypt data.

> The algorithm can be public. The **key must remain secret**.

##  Encryption

Converts readable **plaintext** into unreadable **ciphertext**.

```text
Plaintext + Algorithm + Key → Ciphertext
```
## Decryption

Converts ciphertext back into the original plaintext.

Ciphertext + Algorithm + Key → Plaintex 


### Caesar Cipher & Symmetric Encryption

## Caesar Cipher

The **Caesar Cipher** is a simple encryption technique where each letter is shifted by a fixed number of positions in the alphabet.

The fixed number is called the **Key**.

### Example: Key = 3

 A → D
 B → E
 C → F
 X → A
 Y → B
 Z → C

### Encryption

```text
HELLO
  ↓ Key = 3
KHOOR
```

### Symmetric Encryption

Symmetric encryption uses the **same secret key** for both encryption and decryption.

## Key Points

 Same key is used to **encrypt** and **decrypt**.
 Both sender and receiver need a copy of the same key.
 The key must remain **secret** from everyone else.

```text
Plaintext
   ↓
Encryption + Secret Key
   ↓
Ciphertext
   ↓
Decryption + Same Secret Key
   ↓
Plaintext
```
## Advantages
Fast → Can encrypt large amounts of data quickly.
Efficient → Suitable for:
Files
Hard drives
Network traffic
## Hands-on


<img width="1900" height="871" alt="image" src="https://github.com/user-attachments/assets/8b87d14c-bba3-4da0-80f7-d733a29deb41" />

<img width="1893" height="837" alt="image" src="https://github.com/user-attachments/assets/b89fff07-9856-4bbd-b948-12444b545e9c" />

<img width="1907" height="652" alt="image" src="https://github.com/user-attachments/assets/c3481806-360c-419b-bf8d-fa6a5ee2be75" />

<img width="1911" height="667" alt="image" src="https://github.com/user-attachments/assets/4e0339d8-8f8f-472d-b429-7942d0092333" />


### Asymmetric Encryption

## Key Distribution Problem

In **symmetric encryption**, Alice and Bob use the **same secret key**.

The problem is: **How can they safely share the secret key?**

- Sending the key openly → attacker can steal it.
- Encrypting the key with another key → creates another key-sharing problem.

This is called the **Key Distribution Problem**.

## Asymmetric Encryption

Asymmetric encryption uses **two mathematically linked keys**:

- **Public Key** → Can be shared with everyone.
- **Private Key** → Must be kept secret by the owner.

## Main Idea

> 🔓 Encrypt with Public Key → 🔐 Decrypt with Private Key

If Alice wants to send Bob a secret message:

1. Bob creates a **Public Key + Private Key**.
2. Bob shares his **Public Key**.
3. Alice encrypts the message using Bob's **Public Key**.
4. Alice sends the encrypted message.
5. Bob decrypts it using his **Private Key**.

An attacker can intercept the encrypted message, but cannot decrypt it without Bob's private key.

<img width="835" height="702" alt="image" src="https://github.com/user-attachments/assets/e7a53f2b-cabd-4da4-a580-cec18d865ba5" />


## Mailbox Analogy

Think of a public mailbox:

**Public Key** = Mail slot → Anyone can put a message inside.
**Private Key** = Key to open the mailbox → Only Bob can access the messages.

So, anyone can send Bob a secret message, but only Bob can open and read it.


### Hybrid Approach

```text
Asymmetric Encryption
        ↓
Securely establish/share key
        ↓
Symmetric Encryption
        ↓
Fast and secure data transfer
```
## HTTPS

Asymmetric encryption is commonly used in **HTTPS**.

When you visit a secure website:

1. Website provides its **public key** through a certificate.
2. Browser verifies the certificate.
3. Asymmetric encryption helps securely establish a **shared secret key**.
4. The connection then uses **symmetric encryption** for fast data transfer.

## Viewing
<img width="815" height="822" alt="image" src="https://github.com/user-attachments/assets/64def758-df06-41c1-90ff-52c1df1be95d" />
<img width="623" height="413" alt="image" src="https://github.com/user-attachments/assets/3c6d1946-d479-4e92-b071-e031b4eac5e7" />
<img width="605" height="418" alt="image" src="https://github.com/user-attachments/assets/c2aaad6f-17c4-4cd4-9677-cbead3ff1af1" />
<img width="952" height="718" alt="image" src="https://github.com/user-attachments/assets/5fadb26d-ed80-472a-80e4-e7bf373d8d21" />

