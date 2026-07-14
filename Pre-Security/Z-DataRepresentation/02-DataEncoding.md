### Character Encoding


## Representation vs Encoding

# Representation

How data is stored inside a computer.

```
Letter → Number → Binary
```

Example:

```
A → 65 → 01000001
```
## Encoding

A rule that tells the computer:

> "Which number represents which character."

Example:

| Character | Number |
| --------- | ------ |
| A         | 65     |
| B         | 66     |
| C         | 67     |


#  Example

Text:

```
CAT
```

Stored as:

```
C = 67
A = 65
T = 84
```

The computer stores:

```
67 65 84
```
 
#  Wrong Encoding (Gibberish)

If a file is saved using one encoding and opened with another, strange symbols appear.

Example:

```
Correct:
Café

Wrong:
CafÃ©
```

This is called an **Encoding Mismatch**.
<img width="1048" height="528" alt="image" src="https://github.com/user-attachments/assets/6e464730-ef2f-4e04-ba49-cc0da14a418c" />

#  ASCII

* Full form: **American Standard Code for Information Interchange**
* Uses **7 bits**
* Supports **128 English characters**
* Cannot store emojis or many foreign languages.

# Unicode

* Universal character standard.
* Supports **all languages**.
* Supports **symbols and emojis** 😊.

# UTF Encodings

### UTF-8

* Most common encoding.
* Used on websites.
* Uses **1–4 bytes**.

### UTF-16

* Uses **2 or 4 bytes**.
* Common in Windows and Java.

### UTF-32

* Always uses **4 bytes**.
* Easier but uses more memory.

# Emoji Encoding

Even emojis have Unicode values.

Example:

```
😊 → U+1F60A
```

The computer stores the Unicode number, not the picture.

# **Representation** → How data is stored.
* **Encoding** → Maps numbers to characters.
* **ASCII** → 128 English characters.
* **Unicode** → Supports all languages and emojis.
* **UTF-8** → Most widely used encoding.
* **Wrong encoding** → Causes gibberish text.

# Character encoding is a method of assigning numbers to characters so computers can store and display text correctly.

