<br>

---

<br>

## 1. What are Bits and Bytes?

<br>

### Bits
- A **bit** is the most basic unit of data in a computer.
- A **bit** can hold a value of either $0$ or $1$ (binary digits).
- Computers process everything in binary, meaning all data, including numbers, text, images, and sounds, is represented using combinations of $0$s and $1$s.

<br>

### Bytes
- A **byte** consists of 8 bits.
- Example: $01101100$ is a byte made up of 8 bits.
- Bytes are the standard way of representing data in most systems, and memory/storage sizes are usually measured in bytes (KB, MB, GB, etc.).

<br>

---

<br>

## 2. The Binary Number System (Base 2)

<br>

### What is Binary?
- **Binary** is a base 2 number system, meaning it uses only two symbols: $0$ and $1$.
- Each binary digit (bit) represents an increasing power of $2$, starting from $2^0$ on the right.

<br>

### Decimal vs Binary
In the decimal system (base 10), each digit represents a power of $10$:
- Example: $352 = (3 \times 10^2) + (5 \times 10^1) + (2 \times 10^0)$

In the binary system (base 2), each digit represents a power of $2$:
- Example: $1011 = (1 \times 2^3) + (0 \times 2^2) + (1 \times 2^1) + (1 \times 2^0)$
  - So, $1011$ in binary equals $11$ in decimal.

<br>

### Binary Table Example

| Bit Position     | 7   | 6   | 5   | 4   | 3   | 2   | 1   | 0   |
|------------------|-----|-----|-----|-----|-----|-----|-----|-----|
| Power of 2       | $2^7$ | $2^6$ | $2^5$ | $2^4$ | $2^3$ | $2^2$ | $2^1$ | $2^0$ |
| Value (Decimal)  | $128$ | $64$  | $32$  | $16$  | $8$   | $4$   | $2$   | $1$   |

<br>

Let's look at how the binary number: $01011001$ is represented in memory:

| Bit Position     | 7   | 6   | 5   | 4   | 3   | 2   | 1   | 0   |
|------------------|-----|-----|-----|-----|-----|-----|-----|-----|
| Binary | $0$   | $1$   | $0$   | $1$   | $1$   | $0$   | $0$   | $1$   |
| Value (Decimal)  | $0$   | $64$  | $0$   | $16$  | $8$   | $0$   | $0$   | $1$   |

- In this table, the binary number $01011001$ translates to decimal as:
  - $(0 \times 128) + (1 \times 64) + (0 \times 32) + (1 \times 16) + (1 \times 8) + (0 \times 4) + (0 \times 2) + (1 \times 1) = 89$

<br>

---

<br>

## 3. How Data is Stored in Memory

- Computers store everything using binary.
- Memory (RAM, storage) is organized into addresses, and each address holds data in **binary** form.
- For example, a single character might be stored as one byte (8 bits), and an image might take up many thousands of bytes (measured in kilobytes or megabytes).

<br>

### How Binary Values Represent Characters (ASCII Encoding)
- Characters, such as letters and numbers, are stored using standard encoding systems like **ASCII**.
- ASCII assigns each character a numeric value. For example, the letter 'A' is represented as $65$ in decimal, which equals $01000001$ in binary.

| Character | ASCII (Decimal) | ASCII (Binary) |
|-----------|-----------------|----------------|
| A         | $65$            | $01000001$     |
| B         | $66$            | $01000010$     |
| C         | $67$            | $01000011$     |

<br>

---

<br>

## 4. Other Common Number Systems

<br>

### Hexadecimal (Base 16)
- The hexadecimal (or "hex") system is commonly used to represent binary data in a more human-readable form.
- In base 16, digits range from $0$ to $9$ and $A$ to $F$ (where $A = 10$, $B = 11$, $\ldots$, $F = 15$).
- Example: $10110111$ in binary can be grouped into two 4-bit parts: $1011$ and $0111$. In hex, $1011 = B$ and $0111 = 7$, so the number is $B7$ in hex.

<br>

### Octal (Base 8)
- Octal uses digits from $0$ to $7$ and is another base system used in computing.
- Example: $101101$ in binary can be grouped into 3-bit parts: $101$ and $101$, which correspond to $5$ and $5$ in octal, so the number is $55$ in octal.

<br>

### Conversion Cheat Sheet

| Binary  | Decimal | Hexadecimal | Octal |
|---------|---------|-------------|-------|
| $0000$  | $0$     | $0$         | $0$   |
| $0001$  | $1$     | $1$         | $1$   |
| $0010$  | $2$     | $2$         | $2$   |
| $0011$  | $3$     | $3$         | $3$   |
| $0100$  | $4$     | $4$         | $4$   |
| $0101$  | $5$     | $5$         | $5$   |
| $0110$  | $6$     | $6$         | $6$   |
| $0111$  | $7$     | $7$         | $7$   |
| $1000$  | $8$     | $8$         | $10$  |
| $1001$  | $9$     | $9$         | $11$  |
| $1010$  | $10$    | $A$         | $12$  |
| $1011$  | $11$    | $B$         | $13$  |
| $1100$  | $12$    | $C$         | $14$  |
| $1101$  | $13$    | $D$         | $15$  |
| $1110$  | $14$    | $E$         | $16$  |
| $1111$  | $15$    | $F$         | $17$  |

<br>

---

<br>

## 5. Binary Arithmetic (Adding Binary Numbers)

- Binary addition is similar to decimal addition, but with only two digits: $0$ and $1$.
- The rules for binary addition are:
  - $0 + 0 = 0$
  - $1 + 0 = 1$
  - $1 + 1 = 10$ (which is $2$ in decimal, carrying over the $1$)

<br>

### Example: Adding Binary Numbers
```plaintext
   1011  (11 in decimal)
+  0110  (6 in decimal)
-------
  10001  (17 in decimal)
```

<br>

## Summary
- **Bits** are the fundamental unit of data in computers, representing either $0$ or $1$.
- **Bytes** are composed of 8 bits and are the standard unit for measuring data.
- The **binary system** is a base-2 number system that represents all data in computers.
- Understanding binary helps in working with **hexadecimal**, **octal**, and basic **arithmetic** in computer systems.