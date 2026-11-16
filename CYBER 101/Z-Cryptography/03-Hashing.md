# Hash Functions
A **Hash Function** is a mathematical algorithm that takes input data of any size and converts it into a fixed-size output called a **Hash Value** or **Hash Digest**.

### Example

```text
Input:  Hello World
          |
          v
    Hash Function
       (SHA-256)
          |
          v
Output: A591A6D40BF420404A011733CFB7B190D62C65BF0BCDA32B57B277D9AD9F146E
```

### Characteristics of Hash Functions

1. **No Key Required:** Hashing does not require an encryption key.
2. **Fixed Output Size:** The output length remains fixed regardless of input size.
3. **One-Way Function:** It is computationally impractical to recover the original input from a secure hash.
4. **Avalanche Effect:** Even a small change in input produces a significantly different hash.
5. **Fast Computation:** Cryptographic hash functions are generally fast to calculate.

---

## 2. Difference Between Hashing and Encryption

| Hashing | Encryption |
|---|---|
| One-way process | Reversible process |
| No key required | Requires a key |
| Produces a hash digest | Produces ciphertext |
| Used for data integrity and password verification | Used for data confidentiality |
| Original input cannot practically be recovered | Original data can be recovered using the correct key |

**Example:**

- Hashing: `Hello → Hash Value`
- Encryption: `Hello → Ciphertext → Decryption → Hello`

**Remember:** Hashing is not encryption. A hash cannot be decrypted.

---

## 3. Understanding the T and U Example

Consider two files:

**file1.txt**
```text
T
```

**file2.txt**
```text
U
```

Both characters differ by only one bit in binary representation.

### ASCII Representation

| Character | Hexadecimal | Binary |
|---|---|---|
| T | 54 | 01010100 |
| U | 55 | 01010101 |

Only the last bit changes.

### Hash Comparison

Even though the input changes by only one bit, the resulting hashes are completely different.

| Algorithm | Output Size | Hexadecimal Length |
|---|---:|---:|
| MD5 | 128 bits | 32 characters |
| SHA-1 | 160 bits | 40 characters |
| SHA-256 | 256 bits | 64 characters |
| SHA-512 | 512 bits | 128 characters |

### Important Linux Commands

```bash
cat file1.txt
cat file2.txt
```
Displays file contents.

```bash
hexdump -C file1.txt
```
Displays file contents in hexadecimal and ASCII format.

```bash
md5sum file1.txt
```
Calculates the MD5 hash.

```bash
sha1sum file1.txt
```
Calculates the SHA-1 hash.

```bash
sha256sum file1.txt
```
Calculates the SHA-256 hash.

```bash
sha512sum file1.txt
```
Calculates the SHA-512 hash.

```bash
sha256sum *.txt
```
Calculates SHA-256 hashes of all `.txt` files in the current directory.

**Note:** `*.txt` represents all files ending with `.txt`.

---

## 4. Avalanche Effect

The **Avalanche Effect** means that even a very small change in the input data causes a significant and unpredictable change in the resulting hash value.

### Example

```text
Input 1: T
SHA-256: e632b7095b0bf32c260fa4c539e9fd7b852d0de454e9be26f24d0d6f91d069d3

Input 2: U
SHA-256: a25513c7e0f6eaa80a3337ee18081b9e2ed09e00af8531c8f7bb2542764027e7
```

Although T and U differ by only one bit, their hash values are completely different.

### Importance

- Helps detect modifications in files.
- Helps verify downloaded software.
- Helps identify tampered data.
- Supports data integrity verification.

---

## 5. Why is Hashing Important?

Hashing plays an important role in cybersecurity.

### A. Password Security

Websites should not store passwords in plain text.

Instead, they store password hashes using secure password-hashing algorithms.

**Registration Process:**

```text
User enters password
        |
        v
Password Hashing Algorithm
     (Argon2id)
        |
        v
Password Hash Stored in Database
```

**Login Process:**

1. User enters their password.
2. The system verifies the submitted password against the stored password hash.
3. If verification succeeds, the user is allowed to log in.

**Important:** Password hashing algorithms include:

- Argon2id
- bcrypt
- scrypt

A salt is random data added to a password before hashing. It helps prevent precomputed hash attacks and ensures identical passwords can have different stored hashes.

### B. Data Integrity

**Data Integrity** means ensuring that data has not been modified or tampered with.

Example:

1. Download Kali Linux ISO from its official website.
2. Obtain its official SHA-256 checksum.
3. Calculate the SHA-256 hash of the downloaded ISO.
4. Compare both hash values.

If both hashes match, it provides strong evidence that the downloaded file matches the published file.

If they do not match, the file may have been modified or corrupted.

---

## 6. What is a Hash Collision?

A **Hash Collision** occurs when two different inputs produce the same hash output.

### Example

```text
Input 1 → Hash Function → ABC123

Input 2 → Hash Function → ABC123
```

Both inputs are different, but their hash values are identical.

### Why Do Hash Collisions Occur?

A hash function has a fixed number of possible outputs, but it can accept practically unlimited input values.

Therefore, collisions are mathematically unavoidable.

---

## 7. Pigeonhole Principle

The **Pigeonhole Principle** states that if the number of items is greater than the number of available containers, at least one container must hold more than one item.

### Example

- Number of pigeons = 21
- Number of pigeonholes = 16

At least two pigeons must share one pigeonhole.

The same concept applies to hash functions.

### 4-Bit Hash Example

Suppose a hash function produces a 4-bit output.

Number of possible outputs:

```text
2^4 = 16
```

Therefore, only 16 different hash values are possible.

If we provide 21 different inputs, at least two inputs must produce the same hash.

This is called a **Hash Collision**.

**Remember:** A good hash function makes finding collisions computationally impractical.

---

## 8. Why Are MD5 and SHA-1 Insecure?

MD5 and SHA-1 are considered insecure because practical collision attacks have been demonstrated against them.

### Comparison

| Algorithm | Output Size | Security Status |
|---|---:|---|
| MD5 | 128 bits | Broken for collision resistance |
| SHA-1 | 160 bits | Broken for collision resistance |
| SHA-256 | 256 bits | Currently considered secure for general cryptographic hashing |
| SHA-512 | 512 bits | Currently considered secure for general cryptographic hashing |

### Collision Attack Example

```text
File A → MD5 → Same Hash

File B → MD5 → Same Hash
```

Although File A and File B contain different data, their MD5 hashes are identical.

### Important Security Recommendations

- Avoid MD5 for security-sensitive integrity verification.
- Avoid SHA-1 for collision-resistant security applications.
- Use SHA-256 or SHA-3 for general cryptographic integrity checking.
- Use Argon2id, bcrypt or scrypt for password storage.

---

## 9. SOC Analyst Perspective

Hashing is very useful in Security Operations Centers (SOC).

Suppose a SOC Analyst receives an alert about a suspicious executable file on an employee's computer.

The analyst calculates its SHA-256 hash and searches it in threat intelligence platforms.

### Tools Used

1. **VirusTotal:** Checks file hashes against multiple antivirus and threat intelligence engines.
2. **MalwareBazaar:** Provides information about known malware samples.
3. **Threat Intelligence Platforms:** Help identify known malicious files and indicators of compromise (IOCs).

### SOC Use Cases

- Identifying known malware using file hashes.
- Checking file integrity.
- Investigating suspicious downloads.
- Comparing files across compromised systems.
- Searching threat intelligence databases.
- Supporting malware investigations.

**Important:** A hash match can help identify known malware, but a hash not found in a threat intelligence database does not guarantee that a file is safe.

---

## 10. Important Terminologies

| Term | Meaning |
|---|---|
| Hash Function | Converts input data into a fixed-size digest |
| Hash Digest | Output produced by a hash function |
| Avalanche Effect | Small input change causes a significant output change |
| Hash Collision | Different inputs produce the same hash |
| Pigeonhole Principle | More inputs than outputs guarantees collisions |
| Data Integrity | Ensuring data has not been modified |
| Salt | Random data added before password hashing |
| Plain Text | Original readable data |
| Ciphertext | Encrypted data |
| SHA-256 | Cryptographic hash algorithm producing 256-bit output |
| IOC | Indicator of Compromise |

---
## 11. Practice Commands

Try these commands in your Kali Linux terminal:

```bash
cd ~/Hashing-Basics/Task-2/

ls

cat file1.txt
cat file2.txt

hexdump -C file1.txt
hexdump -C file2.txt

md5sum *.txt
sha1sum *.txt
sha256sum *.txt
sha512sum *.txt
```

