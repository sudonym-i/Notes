# Study Notes: Positional Number Systems & Base Conversion

## Objectives
- Understand Positional Number Systems
- Learn Conversion Between Bases
- Explore Related Bases

---

## 1. Positional Number Systems

### Why Computers Use Binary Instead of Decimal
- **Humans** naturally use base 10 (decimal).
- **Computers**, however, use binary (base 2) because:
  - Electricity is most reliable with two distinct states, represented as **0 (off)** and **1 (on)**.
  - This simplifies hardware design and arithmetic operations.

#### Binary Representation in Hardware
- **Voltages** represent bits:
  - **+5V** = 1 (on)
  - **0V** = 0 (off)
- **Regions**:
  - Each voltage region is interpreted as either 0 or 1.
  - There is an **undefined region** between them to prevent errors due to minor voltage changes.
  - More base regions (e.g., base 10) would require precise voltage control, increasing cost and heat.

### Additional Reasons for Binary
- **Bi-state systems** are easiest to design.
- **Binary arithmetic** is simpler for hardware circuits (e.g., adders).

---

## 2. Features of Decimal (Base 10) System

- **Base**: 10
- **Digits**: 0 through 9 (max digit = base - 1)
- **Total Digits**: 10

### Positional Value Example

Number: **4321₁₀**

- Positions (right to left): 3 2 1 0
- Expanded notation:
  - 4 × 10³ + 3 × 10² + 2 × 10¹ + 1 × 10⁰
  - = 4000 + 300 + 20 + 1 = **4321**

#### Key Points
- **Position determines value**: Each digit's value depends on its position.
- **Positions** are numbered from **right (least significant) to left (most significant)**, starting at zero.

#### Generalized Expanded Notation

For a number in base **B**:

`dn*Bⁿ + dn-1*Bⁿ⁻¹ + ... + d1*B¹ + d0*B⁰`

Where:
- `dn, dn-1, ..., d0` are the digits.
- `n` is the position (starting from the rightmost digit as position 0).

---

## 3. Key Features of Positional Number Systems

| Feature     | Base 10        | Base B           |
|-------------|----------------|------------------|
| # of Digits | 10             | B                |
| Range       | 0 to 9         | 0 to (B - 1)     |
| Value       | Expanded Notation | Expanded Notation |

### Digits Beyond 9
- For bases > 10, use **letters**:
  - A = 10, B = 11, ..., up to Z (base 36)

### **Base Subscript is Required**
- To avoid confusion, always include a subscript for the base:
  - Example: `5016` means 80 in decimal (`80₁₀`)

---

## 4. Binary Example (Base 2)

- **Digits**: 0, 1
- **Example**: 11010₂
- **Positions**: 4 3 2 1 0

Expanded notation:
- 1 × 2⁴ + 1 × 2³ + 0 × 2² + 1 × 2¹ + 0 × 2⁰
- = 16 + 8 + 0 + 2 + 0 = **26₁₀**

---

## 5. Base 5 Example

- **Digits**: 0, 1, 2, 3, 4
- **Example**: 130₅
- Expanded notation:
  - 1 × 5² + 3 × 5¹ + 0 × 5⁰
  - = 25 + 15 + 0 = **40₁₀**

---

## 6. Base 16 Example (Hexadecimal)

- **Digits**: 0-9, A-F (A=10, B=11, ..., F=15)
- **Example**: 84312₁₆
  - Digits above 9 use letters for clarity.

---

## 7. Conversion From Any Base to Decimal

### Method 1: Expanded Notation
- Use the generalized formula:
  - `dn*Bⁿ + dn-1*Bⁿ⁻¹ + ... + d1*B¹ + d0*B⁰`

### Method 2: Horner’s Rule
- Simplifies calculation by **removing exponents**:
  1. Start from the leftmost digit.
  2. Multiply by the base and add the next digit sequentially.
  3. Repeat until all digits are processed.

Example for number `dn dn-1 ... d0` in base B:
- (((dn × B + dn-1) × B + dn-2) × B + ... + d0)

---

## 8. Summary

- **Positional number systems** use digit position to determine value.
- **Binary** is used by computers for reliability and simplicity.
- **Expanded notation** and **Horner’s Rule** allow conversion between bases.
- **Base subscript** is crucial to avoid confusion.
- **Digits in higher bases** use letters beyond 9.

---

## Key Terms

- **Base (Radix):** The number of unique digits, including zero, used to represent numbers.
- **Bit:** Binary digit (0 or 1).
- **Expanded Notation:** Expression of a number as a sum of digits times powers of the base.
- **Horner’s Rule:** Algorithm for efficient base conversion.


----
## Negative Numbers and stuff

Do assignment -> Must be handed in online AND in in person/mailbox


### Signed fixed-length Binary Numbers

- Signed magnitude - Has the negative/positive bit in the *most significant bit*

When converting to a specific representation, always add the type (e.g SM for signed magnitude)

46
-
32 + 4

0 0100100 base 2, SM


-75
- Rem 11 --> rem 3
64 + 8 +2 + 1

1  1001011 Base 2, SM

- Drawback of signed magnitude, we now have 2 zeros +0 & -0




Bitwise operations apply to all bits in being referred to

AND
OR
XOR

all use these operations:
- Set ( =1 )
- Clear ( =0 )
- toggle (Flip bit)

ALL BINARY NUMBERS ARE READ BACKWARDS BY COMPUTERS