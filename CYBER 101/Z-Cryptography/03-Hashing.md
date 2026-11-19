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




# Password Storage & Hashing
## 1. Uses of Hashing

Hashing has two important uses in Cyber Security:

- **Password Storage:** Securely storing passwords for authentication.
- **Data Integrity:** Checking whether a file or data has been modified.

### Authentication vs Password Manager

- **Authentication:** System only needs to verify that the user knows the password. It does not need to retrieve the original password.
- **Password Manager:** Must retrieve the original passwords, so it uses encryption instead of one-way password hashing.

## 2. Insecure Password Storage Practices

There are three insecure practices:

1. Storing passwords in plaintext.
2. Using deprecated encryption.
3. Using insecure hashing algorithms.

### A. Storing Passwords in Plaintext

- Plaintext means readable data without encryption or hashing.
- If a database is leaked, attackers can directly read passwords.
- Password reuse makes this more dangerous because one leaked password may compromise other accounts.

**Example – RockYou Breach (2009):**
- RockYou stored user passwords in plaintext.
- Its data breach exposed millions of passwords.
- The leaked passwords became the `rockyou.txt` wordlist.
- It contains over 14 million passwords.
- Location in Kali Linux: `/usr/share/wordlists/rockyou.txt`

### B. Using Insecure Encryption – Adobe Breach

- Adobe used a deprecated encryption format instead of secure password hashing.
- Password hints were stored in plaintext.
- Some hints revealed the actual passwords.
- This made password recovery easier for attackers.

**Remember:** Encryption is reversible with the correct key. Password storage should use secure password hashing.

### C. Using Insecure Hashing – LinkedIn Breach (2012)

- LinkedIn used SHA-1 to store passwords.
- SHA-1 is not suitable for secure password storage.
- No salt was used.
- Same passwords produced identical hashes.

**Remember:** Use Argon2id, bcrypt or scrypt for password storage.

## 3. Password Salting

**Salt:** A random value added to a password before hashing.

Example:

Without salt:
- User A: `letmein` → Hash A
- User B: `letmein` → Hash A

With salt:
- User A: `letmein + X7p9` → Hash A
- User B: `letmein + K2m5` → Hash B

### Benefits of Salt

1. Same passwords produce different hashes.
2. Protects against precomputed rainbow table attacks.
3. Makes attackers crack each account separately.

**Important:**
- Salt should be randomly generated.
- Each password should have a unique salt.
- Salt is not secret; it can be stored with the hash.

## 4. Important Commands – RockYou.txt

First, open the Kali Linux terminal.

| Command | Purpose |
|---|---|
| `pwd` | Shows current directory |
| `cd /usr/share/wordlists` | Opens the wordlists directory |
| `ls` | Lists files and folders |
| `cat rockyou.txt` | Displays the entire file |
| `head rockyou.txt` | Displays first 10 lines |
| `wc -l rockyou.txt` | Counts total lines |
| `sed -n '20p' rockyou.txt` | Displays only the 20th line |
| `tail rockyou.txt` | Displays last 10 lines |

## Commands

### 1. `pwd`
- `pwd` = Print Working Directory
- Shows current directory (you are currently in which folder).

### 2. `cd /usr/share/wordlists`
- `cd` = Change Directory (change folder).
- `/` = Root directory (main starting directory).
- `usr` = User-related system programs and resources.
- `share` = Shared data.
- `wordlists` = Folder containing wordlist files.

### 3. `ls`
- `ls` = List.
- Displays files and folders in the current directory.

### 4. `cat rockyou.txt`
- `cat` = Concatenate (displays file contents).
- `rockyou.txt` = Name of the text file.
- Displays the complete file.

### 5. `head rockyou.txt`
- `head` = Displays the beginning of a file.
- `rockyou.txt` = File name.
- By default, displays the first 10 lines.

### 6. `wc -l rockyou.txt`
- `wc` = Word Count (counts text).
- `-` = Introduces an option.
- `l` = Lines.
- `rockyou.txt` = File name.
- Counts the total number of lines.

### 7. `sed -n '20p' rockyou.txt`
- `sed` = Stream Editor (edits or processes text).
- `-` = Introduces an option.
- `n` = Suppresses automatic printing.
- `'20p'` = Selects and prints line number 20.
- `rockyou.txt` = File name.

### 8. `tail rockyou.txt`
- `tail` = Displays the ending of a file.
- `rockyou.txt` = File name.
- By default, displays the last 10 lines.



 
# Secure Password Storage & Rainbow Tables

## 1. Using Hashing to Store Passwords

- Instead of storing original passwords, websites store their hash values.
- During login, the entered password is hashed and verified against the stored hash.
- If a database is leaked, attackers must crack the hashes to discover passwords.
- Same password always produces the same hash if no salt is used.

## 2. Rainbow Table

**Definition:** A Rainbow Table is a precomputed lookup table containing password hashes and their corresponding plaintext passwords.

- Helps attackers identify passwords from leaked hashes.
- Stores previously calculated hash-password mappings.
- Saves cracking time but requires storage space.
- Mainly effective against unsalted hashes.

**Example:**

| Hash | Password |
|---|---|
| `e10adc3949ba59abbe56e057f20f883e` | `123456` |
| `e99a18c428cb38d5f260853678922e03` | `abc123` |

**Websites using hash lookup databases:**
- CrackStation
- Hashes.com

## 3. Protecting Against Rainbow Tables

**Salt:** A randomly generated value added to a password before hashing.

- Every user should have a unique salt.
- Salt can be added to the beginning or end of a password.
- Same passwords with different salts produce different hashes.
- Salt is stored with the password hash.
- Salt does not need to be secret.

**Example:**

Without Salt:
- User A: `letmein` → Hash A
- User B: `letmein` → Hash A

With Salt:
- User A: `letmein + X7p9` → Hash A
- User B: `letmein + K2m5` → Hash B

**Benefit:** Unique salts make precomputed Rainbow Tables ineffective against the salted hashes.

## 4. Example of Securely Storing Passwords

Follow these steps:

1. Select a secure password hashing algorithm: Argon2, Scrypt, Bcrypt or PBKDF2.
2. Generate a unique salt: `Y4UV*^(=go_!`
3. Combine password and salt:
   - Password: `AL4RMc10k`
   - Salt: `Y4UV*^(=go_!`
   - Combined: `AL4RMc10kY4UV*^(=go_!`
4. Calculate the hash of the combined input using the selected algorithm.
5. Store the generated hash and unique salt in the database.

**Note:** Modern password hashing libraries like Bcrypt and Scrypt automatically generate and manage salts.

## 5. Why Not Use Encryption to Store Passwords?

Encryption is reversible and requires a key.

**Problem with Encryption:**
- The original password can be recovered using the decryption key.
- The encryption key must be stored somewhere.
- If attackers obtain the key, they can decrypt all stored passwords.

**Why Hashing is Better:**
- Hashing is a one-way process.
- It does not require an encryption key.
- Original passwords do not need to be recovered.
- It allows secure password verification.

## 6. Hashing vs Encryption

| Hashing | Encryption |
|---|---|
| One-way process | Reversible process |
| No key required | Requires a key |
| Used for password verification | Used for data confidentiality |
| Original data cannot normally be recovered | Original data can be recovered using a key |




# Hash Recognition & Password Cracking – Cyber 101

## 1. Hash Recognition

**Hash Recognition:** Identifying which hashing algorithm was used to generate a hash.

- Hashes can be identified using their prefix, length, encoding and source context.
- Automated tools may confuse similar hash formats.
- Context is important when identifying hashes.

**Tools:**
- `hashID` – Identifies possible hash types.
- Hashcat Example Hashes – Reference for hash formats and modes.

Links:
- https://pypi.org/project/hashID/
- https://hashcat.net/wiki/doku.php?id=example_hashes

**Example:**
- Web application database → MD5 may be possible.
- Windows system → NTLM may be possible.

## 2. Linux Passwords

Linux password hashes are stored in:

- `/etc/shadow` – Stores password hashes and password aging information; normally accessible only to root.
- `/etc/passwd` – Stores user account information; normally readable by all users.

### Important Commands

```bash
sudo cat /etc/shadow
```
Displays the shadow file with administrator privileges.

```bash
man 5 shadow
```
Opens the manual for the Linux shadow file format.

```bash
man 5 crypt
```
Displays information about password hashing formats.

### Shadow File Structure

Each line contains 9 fields separated by colons (`:`).

```text
username:password:last_change:min:max:warn:inactive:expire:reserved
```

| Field | Meaning |
|---|---|
| 1 | Username |
| 2 | Password hash information |
| 3 | Last password change |
| 4 | Minimum password age |
| 5 | Maximum password age |
| 6 | Warning period |
| 7 | Inactive period |
| 8 | Account expiration |
| 9 | Reserved |

## 3. Linux Password Hash Format

Format:

```text
$prefix$options$salt$hash
```

| Component | Meaning |
|---|---|
| Prefix | Identifies hashing algorithm |
| Options | Algorithm parameters |
| Salt | Random value added before hashing |
| Hash | Final generated hash value |

### Common Linux Hash Prefixes

| Prefix | Algorithm |
|---|---|
| `$y$` | yescrypt |
| `$gy$` | gost-yescrypt |
| `$7$` | scrypt |
| `$2b$`, `$2y$`, `$2a$`, `$2x$` | bcrypt |
| `$6$` | sha512crypt |
| `$md5` | SunMD5 |
| `$1$` | md5crypt |

**Remember:** `$y$` identifies yescrypt.

### Example – Modern Linux Shadow Entry

```text
strategos:$y$j9T$76UzfgEM5PnymhQ7TlJey1$/OOSg64dhfF.TigVPdzqiFang6uZA4QA1pzzegKdVm4:19965:0:99999:7:::
```

Breakdown:

- `strategos` – Username
- `y` – yescrypt algorithm
- `j9T` – Algorithm parameters
- `76UzfgEM5PnymhQ7TlJey1` – Salt
- `/OOSg64dhfF.TigVPdzqiFang6uZA4QA1pzzegKdVm4` – Hash

## 4. MS Windows Passwords

- Windows uses NTLM (NT LAN Manager) password hashes.
- NTLM is based on MD4.
- NTLM hashes look visually similar to MD4 and MD5 hashes.
- Context is important to identify the correct hash type.

### Where are Windows Hashes Stored?

**SAM = Security Accounts Manager**

- Windows stores local account password hashes in the SAM database.
- Normal users are restricted from accessing these hashes.
- Tools like Mimikatz can extract credentials in authorized security testing.

### Types of Windows Hashes

| Type | Meaning |
|---|---|
| NT Hash | NTLM-based Windows password hash |
| LM Hash | Older and weaker LAN Manager hash |

## 5. macOS Passwords

Modern macOS stores local account passwords using:

- PBKDF2 with SHA-512.
- A unique salt.
- Administrator access is normally required.

**Storage location:**

```text
/var/db/dslocal/nodes/Default/users/
```

**Hashcat Mode:** `7100` – macOS PBKDF2-SHA512.

## 6. Important Tools & References

| Tool | Purpose |
|---|---|
| hashID | Identifies possible hash types |
| Hashcat | Password hash recovery and auditing |
| Mimikatz | Windows credential extraction |
| Hashcat Example Hashes | Reference for hash formats and modes |

