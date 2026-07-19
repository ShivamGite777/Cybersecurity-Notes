
### Computer Color Representation

# how computers represent colors using **Binary** and **Hexadecimal**.

## RGB Color Model

Computers create every color by mixing three primary colors:

* 🔴 Red (R)
* 🟢 Green (G)
* 🔵 Blue (B)

Each color has its own brightness level.

## 🎨 First 8 Colors

Suppose each RGB light has only **2 states**:

* **0 = OFF**
* **1 = ON**

Since there are 3 colors:

```text
2 × 2 × 2 = 8 Colors
```

Each color is represented using **3 bits**.

| Binary | Meaning      | Color      |
| ------ | ------------ | ---------- |
| 000    | All OFF      | ⚫ Black    |
| 001    | Blue ON      | 🔵 Blue    |
| 010    | Green ON     | 🟢 Green   |
| 100    | Red ON       | 🔴 Red     |
| 011    | Green + Blue | 🩵 Cyan    |
| 101    | Red + Blue   | 🩷 Magenta |
| 110    | Red + Green  | 🟨 Yellow  |
| 111    | All ON       | ⚪ White    |

## What is a Bit?

A **Bit (Binary Digit)** is the smallest unit of data.

A bit stores only:

```text
0 = OFF
1 = ON
```

## From 8 Colors to 16 Million Colors

Modern computers are not limited to ON/OFF.

Each RGB color has **256 brightness levels**.

```text
Red   = 0 → 255
Green = 0 → 255
Blue  = 0 → 255
```

Total colors:

```text
256 × 256 × 256
=
16,777,216 Colors
```

---

# 💾 What is a Byte?

```text
1 Byte = 8 Bits
```

Since each RGB color uses **8 bits**:

* Red = 1 Byte
* Green = 1 Byte
* Blue = 1 Byte

Total:

```text
3 Bytes
=
24 Bits
```

This is called **24-bit Color**.

## Why 256 Values?

8 bits can represent:

```text
2⁸ = 256 Values
```

Example:

```text
00000000 = 0
11111111 = 255
```

## Hexadecimal Representation

Binary numbers are long.

Hexadecimal shortens them.

Every **4 binary bits** become **1 hexadecimal digit**.

| Hex | Binary |
| --- | ------ |
| 0   | 0000   |
| 1   | 0001   |
| 2   | 0010   |
| 3   | 0011   |
| 4   | 0100   |
| 5   | 0101   |
| 6   | 0110   |
| 7   | 0111   |
| 8   | 1000   |
| 9   | 1001   |
| A   | 1010   |
| B   | 1011   |
| C   | 1100   |
| D   | 1101   |
| E   | 1110   |
| F   | 1111   |


## Example

Binary:

```text
10100011 11101010 00101010
```

Hexadecimal:

```text
A3EA2A
```

Much easier to read and write.

## Color Format

A color is stored as:

```text
RR GG BB
```

Example:

```text
#EB0037
```

Where:

* **EB** → Red
* **00** → Green
* **37** → Blue

Binary:

```text
11101011 00000000 00110111
```

## Key Points

* Computers use the **RGB color model**.
* **R = Red, G = Green, B = Blue**.
* **1 Bit = 0 or 1**.
* **1 Byte = 8 Bits**.
* **Each RGB value uses 1 Byte**.
* **One color = 3 Bytes = 24 Bits**.
* **24-bit color = 16,777,216 possible colors**.
* **Every 4 binary bits = 1 hexadecimal digit**.
* Hexadecimal makes binary values shorter and easier to read.

 ### Numbers: Decimal, Binary & Hexadecimal 

##  Decimal (Base-10)

* Uses digits **0–9**
* Number value is based on **powers of 10**
* Example:

  * **213 = 2×10² + 1×10¹ + 3×10⁰**

## Binary (Base-2)

* Uses only **0 and 1**
* Used by **computers**
* Number value is based on **powers of 2**

| Binary | Decimal |
| ------ | ------: |
| 0000   |       0 |
| 0001   |       1 |
| 0010   |       2 |
| 0011   |       3 |
| 0100   |       4 |
| 1000   |       8 |
| 1111   |      15 |

### Memory Trick

```text
8   4   2   1
```

Example:

```text
1101

8 + 4 + 0 + 1 = 13
```
## Hexadecimal (Base-16)

* Uses **0–9** and **A–F**
* Short form of binary
* **4 Binary Bits = 1 Hex Digit**

| Hex | Decimal |
| :-: | ------: |
|  A  |      10 |
|  B  |      11 |
|  C  |      12 |
|  D  |      13 |
|  E  |      14 |
|  F  |      15 |

Example:

```text
1010 = A
1101 = D

10101101 = AD
```
##  Octal (Base-8)

* Uses digits **0–7**
* **3 Binary Bits = 1 Octal Digit**

Example:

```text
111111

↓

111 111

↓

77₈
```

#  Quick Revision

| System      | Base | Digits   |
| ----------- | ---- | -------- |
| Decimal     | 10   | 0–9      |
| Binary      | 2    | 0,1      |
| Octal       | 8    | 0–7      |
| Hexadecimal | 16   | 0–9, A–F |




### ASCII (American Standard Code for Information Interchange)

## What I Learned

 Computers understand only **0s and 1s (Binary)**.
 Text must be converted into numbers before it can be stored.
 **ASCII** is a character encoding standard that assigns a unique number to each English character.
 Introduced in **1963**.
 Uses **7 bits**, allowing **128 characters (0–127)**.

# Why Do We Need ASCII?

Humans understand:

```text
TryHackMe
```

Computers understand:

```text
01010100 01110010 01111001...
```

ASCII acts as a **translator** between characters and numbers.

# How ASCII Works

```
Character
     ↓
ASCII Number
     ↓
Binary
     ↓
Stored in File
```

Example:

| Character | Decimal | Hex | Binary |
|-----------|--------:|----:|----------------|
| A | 65 | 41 | 01000001 |
| B | 66 | 42 | 01000010 |
| a | 97 | 61 | 01100001 |
| b | 98 | 62 | 01100010 |
| 0 | 48 | 30 | 00110000 |
| 9 | 57 | 39 | 00111001 |

---

# Example: "TryHackMe"

ASCII Values:

| Character | Decimal | Hex |
|-----------|--------:|----:|
| T | 84 | 54 |
| r | 114 | 72 |
| y | 121 | 79 |
| H | 72 | 48 |
| a | 97 | 61 |
| c | 99 | 63 |
| k | 107 | 6B |
| M | 77 | 4D |
| e | 101 | 65 |

---

# Binary Representation

```text
01010100 01110010 01111001
01001000 01100001 01100011
01101011 01001101 01100101
00001010
```

> `00001010` = New Line (`\n`)


# Hex Representation

```text
54 72 79 48 61 63 6B 4D 65 0A
```

Cybersecurity professionals usually use **Hex** because it is easier to read than binary.

# ASCII Character Order

Letters and numbers are stored in order.

```
A = 65
B = 66
C = 67
```

```
a = 97
b = 98
c = 99
```

```
0 = 48
1 = 49
2 = 50
```

This makes character comparison and sorting easier.

# ASCII Limitation

ASCII only supports **English characters**.

It **cannot** represent:

```text
é
ñ
ü
ł
č
ș
😊
```

# Supporting Other Languages

New encoding standards were introduced.

### ISO-8859-1 (Latin-1)

Supports Western European languages.

Examples:

- é
- ñ
- ü
- ç

---

### ISO-8859-2 (Latin-2)

Supports Central & Eastern European languages.

Examples:

- ł
- č
- ř
- ș


# Encoding Mismatch

If a file is saved using one encoding and opened using another, characters may appear incorrectly.

Example:

```text
Correct:
Café

Wrong:
CafÃ©
```

This is called an **Encoding Mismatch**.

---

# Memory Trick

```text
Character
      ↓
ASCII Number
      ↓
Binary
      ↓
Stored in File
      ↓
Displayed as Text
```

# Example:

```text
T
↓
84
↓
01010100
↓
54 (Hex)
```


### Unicode 

## What I Learned

* ASCII supports only **English characters (128)**.
* Different countries created different encodings (ISO-8859-1, ISO-8859-2, etc.).
* Different encodings caused **encoding mismatch** (wrong characters displayed).
* **Unicode** solves this problem by giving every character in every language a unique code point.

# Why ASCII Was Not Enough

ASCII cannot represent:

* ñ
* €
* あ
* ب
* 😊

Different encoding standards caused compatibility issues.

Example:

```text
Saved as:
Ø

Opened with different encoding:
Ř
```

This is called an **Encoding Mismatch**.

# What is Unicode?

**Unicode** is a universal character encoding standard.

* Supports all modern and historical languages
* Supports symbols
* Supports emojis
* Every character has a **unique Unicode code point**



# Unicode Examples

| Character | Unicode |
| --------- | ------- |
| A         | U+0041  |
| Ω         | U+03A9  |
| あ         | U+3042  |
| ت         | U+062A  |
| 😊        | U+1F60A |
| 龍         | U+9F8D  |
| ♞         | U+265E  |


# Unicode Code Point

Every character has a unique ID called a **Code Point**.

Example:

```text
A  → U+0041

😊 → U+1F60A

龍 → U+9F8D
```
# UTF (Unicode Transformation Format)

UTF is the method used to store Unicode characters.

## UTF-8

* Uses **1–4 Bytes**
* Most common encoding
* Used by websites and Linux
* ASCII characters use only **1 Byte**

Examples:

| Character | Bytes |
| --------- | ----: |
| A         |     1 |
| Ω         |     2 |
| 😊        |     4 |

---

## UTF-16

* Uses **2 or 4 Bytes**
* Most common characters → 2 Bytes
* Emoji & rare characters → 4 Bytes

Examples:

```text
A  → U+0041

🔥 → U+D83D U+DD25
```

---

## UTF-32

* Always uses **4 Bytes**
* Easy to understand
* Uses more storage

Examples:

```text
A  → U+00000041

😊 → U+0001F60A
```

# Unicode Character Examples

### Chinese

```text
龍

Unicode:
U+9F8D
```

Meaning: **Dragon**

---

### Emoji

```text
😊

Unicode:
U+1F60A
``

### Japanese

```text
ツ

Unicode:
U+30C4
```

---

### Arabic

```text
ت

Unicode:
U+062A
```


### Chess Piece

```text
♞

Unicode:
U+265E
```

# ASCII vs Unicode

| ASCII          | Unicode             |
| -------------- | ------------------- |
| English only   | All languages       |
| 128 characters | 157,000+ characters |
| 7-bit          | Universal standard  |
| No Emoji       | Supports Emoji      |
| Limited        | Worldwide support   |

---

# Memory Trick

```text
ASCII
↓

English Only 🇺🇸
```

```text
Unicode
↓

Whole World 🌍
```

```text
Unicode Character
        ↓
Code Point
        ↓
UTF-8 / UTF-16 / UTF-32
        ↓
Stored in Computer
```

# Key Points

* Unicode is a **universal character encoding standard**.
* Every character has a **unique code point**.
* Solves encoding mismatch problems.
* Supports all languages and emojis.
* UTF-8 is the most commonly used encoding on the web.
