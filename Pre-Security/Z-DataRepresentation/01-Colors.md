
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
