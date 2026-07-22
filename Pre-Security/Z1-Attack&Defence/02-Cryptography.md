<img width="1893" height="837" alt="image" src="https://github.com/user-attachments/assets/b5de657b-1422-44fc-bf27-2dd8107b399b" />
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

