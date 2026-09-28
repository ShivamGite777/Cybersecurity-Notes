# Hash Functions

A **hash function** takes input data of any size and produces a fixed-size output called a **hash** or **digest**.

```text
Input Data
    ↓
Hash Function
    ↓
Hash / Digest
```

### Simple Idea

> A hash is like a **digital fingerprint** of data.

If the data changes, its hash should also change.

---

## Hashing vs Encryption

| Hashing                      | Encryption                      |
| ---------------------------- | ------------------------------- |
| No key required              | Uses a key                      |
| One-way process              | Can be decrypted                |
| Produces a fixed-size digest | Produces encrypted data         |
| Mainly used for integrity    | Mainly used for confidentiality |

---

## Important Property: Small Change = Big Hash Change

Consider:

```text
T = 54 (hex)
  = 01010100 (binary)

U = 55 (hex)
  = 01010101 (binary)
```

Only **1 bit** is different:

```text
01010100
01010101
       ↑
   1 bit changed
```

But their hashes will be completely different:

```text
T → Hash Function → Hash A

U → Hash Function → Hash B
```

```text
Hash A ≠ Hash B
```

This property is called the **Avalanche Effect**.

---

## Why is Hashing Useful?

Hashing is mainly used to check **data integrity**.

### Example

Suppose you download a file.

```text
Original File
     ↓
   SHA-256
     ↓
  Hash A
```

After downloading:

```text
Downloaded File
      ↓
    SHA-256
      ↓
    Hash B
```

If:

```text
Hash A == Hash B
```

The file has most likely not been changed.

If:

```text
Hash A != Hash B
```

The file has been changed or corrupted.

---

## Common Uses of Hashing

```text
File Integrity
     ↓
Password Storage
     ↓
Digital Signatures
     ↓
Data Verification
```

---

## Key Points

```text
Hash Function
     ↓
Any-size input
     ↓
Fixed-size output
     ↓
Called Hash / Digest
```

* No key is required.
* Hashing is not encryption.
* Hashes are designed to be difficult to reverse.
* A small input change should produce a very different hash.
* Hashing is commonly used to verify **integrity**.
