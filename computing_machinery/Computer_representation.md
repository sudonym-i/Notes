---
title: Number Representation - Signed Magnitude, 1's Complement, and 2's Complement
tags: [computer-science, binary, number-systems, digital-logic]
---

# Number Representation: Signed Magnitude, 1's Complement, and 2's Complement

When representing signed integers in computer systems, several methods are used. These methods differ in how they handle positive and negative numbers, and each has its own advantages and disadvantages, particularly concerning arithmetic operations and the representation of zero.

## 1. Signed Magnitude Representation

Signed magnitude is the most straightforward way to represent signed integers.

### Concept
*   The leftmost bit (Most Significant Bit - MSB) is designated as the **sign bit**.
    *   `0` indicates a positive number.
    *   `1` indicates a negative number.
*   The remaining bits represent the **magnitude** (absolute value) of the number.

### Example (using 8 bits)
*   **Positive 5:** `00000101` (Sign bit `0`, magnitude `0000101` which is 5)
*   **Negative 5:** `10000101` (Sign bit `1`, magnitude `0000101` which is 5)

### Range (for $n$ bits)
*   From $-(2^{n-1} - 1)$ to $(2^{n-1} - 1)$
*   For 8 bits: $-(2^{8-1} - 1)$ to $(2^{8-1} - 1)$ = $-(2^7 - 1)$ to $(2^7 - 1)$ = $-127$ to $127$.

### Characteristics
*   **Two representations for zero:**
    *   `+0`: `00000000`
    *   `-0`: `10000000`
*   **Arithmetic is complex:** Addition and subtraction require checking signs and comparing magnitudes, often leading to separate logic for different cases.

---

## 2. 1's Complement Representation

1's complement is another method for representing signed integers, primarily used as an intermediate step to understanding 2's complement.

### Concept
*   **Positive numbers:** Represented in the same way as unsigned binary or signed magnitude (MSB is `0`).
*   **Negative numbers:** Obtained by **inverting all the bits** (0s become 1s, and 1s become 0s) of its positive counterpart. This is also known as taking the "1's complement" of the positive number.

### Example (using 8 bits)
*   **Positive 5:** `00000101`
*   **Negative 5:**
    1.  Start with positive 5: `00000101`
    2.  Invert all bits: `11111010`

### Range (for $n$ bits)
*   From $-(2^{n-1} - 1)$ to $(2^{n-1} - 1)$
*   For 8 bits: $-127$ to $127$.

### Characteristics
*   **Two representations for zero:**
    *   `+0`: `00000000`
    *   `-0`: `11111111`
*   **Arithmetic:** Addition is simpler than signed magnitude, but it requires an "end-around carry" if a carry is generated from the most significant bit. This carry is added back to the result.
*   **Sign bit:** The MSB still indicates the sign (`0` for positive, `1` for negative).

---

## 3. 2's Complement Representation

2's complement is the most common method for representing signed integers in modern computer systems due to its efficiency in arithmetic operations.

### Concept
*   **Positive numbers:** Represented in the same way as unsigned binary or signed magnitude (MSB is `0`).
*   **Negative numbers:** Obtained by:
    1.  Taking the 1's complement of the positive counterpart.
    2.  **Adding 1** to the result of the 1's complement.

### Example (using 8 bits)
*   **Positive 5:** `00000101`
*   **Negative 5:**
    1.  Start with positive 5: `00000101`
    2.  Take 1's complement: `11111010`
    3.  Add 1: `11111010 + 1 = 11111011`

### Range (for $n$ bits)
*   From $-2^{n-1}$ to $(2^{n-1} - 1)$
*   For 8 bits: $-2^{8-1}$ to $(2^{8-1} - 1)$ = $-2^7$ to $(2^7 - 1)$ = $-128$ to $127$.
    *   Notice that 2's complement can represent one more negative number than positive numbers. This is because there is only one representation for zero.

### Characteristics
*   **Single representation for zero:** `00000000`
*   **Arithmetic is simple:** Addition and subtraction can be performed using the same hardware logic as unsigned binary addition, regardless of the signs of the numbers. Subtraction is typically performed by adding the 2's complement of the subtrahend. Any carry out of the MSB is simply discarded.
*   **Sign bit:** The MSB still indicates the sign (`0` for positive, `1` for negative).
*   **Most widely used:** Due to its efficient arithmetic and single zero representation.

---

## Comparison Summary

| Feature                 | Signed Magnitude                | 1's Complement                                  | 2's Complement                          |
| :---------------------- | :------------------------------ | :---------------------------------------------- | :-------------------------------------- |
| **Positive Numbers**    | Same as unsigned                | Same as unsigned                                | Same as unsigned                        |
| **Negative Numbers**    | Sign bit + magnitude            | Invert all bits of positive                     | Invert all bits of positive, then add 1 |
| **Zero Representation** | Two (`+0`, `-0`)                | Two (`+0`, `-0`)                                | One (`0`)                               |
| **Range ($n$ bits)**    | $-(2^{n-1}-1)$ to $(2^{n-1}-1)$ | $-(2^{n-1}-1)$ to $(2^{n-1}-1)$                 | $-2^{n-1}$ to $(2^{n-1}-1)$             |
| **Arithmetic**          | Complex                         | Requires end-around carry                       | Simple (standard binary addition)       |
| **Hardware Complexity** | High                            | Moderate                                        | Low                                     |
| **Usage**               | Rarely used for arithmetic      | Historically, some systems; conceptually useful | **Most common in modern computers**     |

---
title: Number Representation - Signed Magnitude, 1's Complement, 2's Complement, and Arbitrary Base Complements
tags: [computer-science, binary, number-systems, digital-logic, arbitrary-base]
---

# Number Representation: Signed Magnitude, 1's Complement, 2's Complement, and Arbitrary Base Complements

When representing signed integers in computer systems, several methods are used. These methods differ in how they handle positive and negative numbers, and each has its own advantages and disadvantages, particularly concerning arithmetic operations and the representation of zero.

## 1. Signed Magnitude Representation

Signed magnitude is the most straightforward way to represent signed integers.

### Concept
*   The leftmost bit (Most Significant Bit - MSB) is designated as the **sign bit**.
    *   `0` indicates a positive number.
    *   `1` indicates a negative number.
*   The remaining bits represent the **magnitude** (absolute value) of the number.

### Example (using 8 bits)
*   **Positive 5:** `00000101` (Sign bit `0`, magnitude `0000101` which is 5)
*   **Negative 5:** `10000101` (Sign bit `1`, magnitude `0000101` which is 5)

### Range (for $n$ bits)
*   From $-(2^{n-1} - 1)$ to $(2^{n-1} - 1)$
*   For 8 bits: $-(2^{8-1} - 1)$ to $(2^{8-1} - 1)$ = $-(2^7 - 1)$ to $(2^7 - 1)$ = $-127$ to $127$.
S
### Characteristics
*   **Two representations for zero:**
    *   `+0`: `00000000`
    *   `-0`: `10000000`
*   **Arithmetic is complex:** Addition and subtraction require checking signs and comparing magnitudes, often leading to separate logic for different cases.

---

## 2. 1's Complement Representation

1's complement is another method for representing signed integers, primarily used as an intermediate step to understanding 2's complement.

### Concept
*   **Positive numbers:** Represented in the same way as unsigned binary or signed magnitude (MSB is `0`).
*   **Negative numbers:** Obtained by **inverting all the bits** (0s become 1s, and 1s become 0s) of its positive counterpart. This is also known as taking the "1's complement" of the positive number.

### Example (using 8 bits)
*   **Positive 5:** `00000101`
*   **Negative 5:**
    1.  Start with positive 5: `00000101`
    2.  Invert all bits: `11111010`

### Range (for $n$ bits)
*   From $-(2^{n-1} - 1)$ to $(2^{n-1} - 1)$
*   For 8 bits: $-127$ to $127$.

### Characteristics
*   **Two representations for zero:**
    *   `+0`: `00000000`
    *   `-0`: `11111111`
*   **Arithmetic:** Addition is simpler than signed magnitude, but it requires an "end-around carry" if a carry is generated from the most significant bit. This carry is added back to the result.
*   **Sign bit:** The MSB still indicates the sign (`0` for positive, `1` for negative).

---

## 3. 2's Complement Representation

2's complement is the most common method for representing signed integers in modern computer systems due to its efficiency in arithmetic operations.

### Concept
*   **Positive numbers:** Represented in the same way as unsigned binary or signed magnitude (MSB is `0`).
*   **Negative numbers:** Obtained by:
    1.  Taking the 1's complement of the positive counterpart.
    2.  **Adding 1** to the result of the 1's complement.

### Example (using 8 bits)
*   **Positive 5:** `00000101`
*   **Negative 5:**
    1.  Start with positive 5: `00000101`
    2.  Take 1's complement: `11111010`
    3.  Add 1: `11111010 + 1 = 11111011`

### Range (for $n$ bits)
*   From $-2^{n-1}$ to $(2^{n-1} - 1)$
*   For 8 bits: $-2^{8-1}$ to $(2^{8-1} - 1)$ = $-2^7$ to $(2^7 - 1)$ = $-128$ to $127$.
    *   Notice that 2's complement can represent one more negative number than positive numbers. This is because there is only one representation for zero.

### Characteristics
*   **Single representation for zero:** `00000000`
*   **Arithmetic is simple:** Addition and subtraction can be performed using the same hardware logic as unsigned binary addition, regardless of the signs of the numbers. Subtraction is typically performed by adding the 2's complement of the subtrahend. Any carry out of the MSB is simply discarded.
*   **Sign bit:** The MSB still indicates the sign (`0` for positive, `1` for negative).
*   **Most widely used:** Due to its efficient arithmetic and single zero representation.

---

## 4. Arbitrary Base Complements (Radix and Radix-1)

The concepts of 1's complement and 2's complement can be generalized to any arbitrary base (radix) $r$. These are known as the $(r-1)$'s complement and $r$'s complement.

### General Concept
For a number $N$ with $n$ digits in base $r$:
*   The largest possible $n$-digit number in base $r$ is $r^n - 1$. For example, in base 10 with 3 digits, the largest number is $10^3 - 1 = 999$. In base 2 with 3 digits, it's $2^3 - 1 = 111_2 = 7_{10}$.

### 4.1. $(r-1)$'s Complement (Diminished Radix Complement)

This is the generalization of 1's complement.

#### Concept
To find the $(r-1)$'s complement of an $n$-digit number $N$ in base $r$:
*   Subtract each digit of $N$ from $(r-1)$.
*   Alternatively, it can be calculated as $(r^n - 1) - N$.

#### Example (Base 10, 4 digits)
*   Find the 9's complement of $N = 3456_{10}$:
    *   Subtract each digit from 9:
        *   $9 - 3 = 6$
        *   $9 - 4 = 5$
        *   $9 - 5 = 4$
        *   $9 - 6 = 3$
    *   The 9's complement is $6543_{10}$.
    *   Using the formula: $(10^4 - 1) - 3456 = 9999 - 3456 = 6543_{10}$.

#### Example (Base 8, 3 digits)
*   Find the 7's complement of $N = 253_8$:
    *   Subtract each digit from 7:
        *   $7 - 2 = 5$
        *   $7 - 5 = 2$
        *   $7 - 3 = 4$
    *   The 7's complement is $524_8$.
    *   Using the formula: $(8^3 - 1) - 253_8 = (512 - 1)_{10} - (2 \cdot 8^2 + 5 \cdot 8^1 + 3 \cdot 8^0)_{10} = 511_{10} - 171_{10} = 340_{10}$.
        *   To convert $340_{10}$ to base 8: $340 / 8 = 42$ R $4$, $42 / 8 = 5$ R $2$, $5 / 8 = 0$ R $5$. So $340_{10} = 524_8$.

#### Characteristics
*   Similar to 1's complement, it has two representations for zero (e.g., `0000` and `9999` in 4-digit base 10).
*   Arithmetic often involves an "end-around carry" for subtraction.

### 4.2. $r$'s Complement (Radix Complement)

This is the generalization of 2's complement.

#### Concept
To find the $r$'s complement of an $n$-digit number $N$ in base $r$:
*   Find the $(r-1)$'s complement of $N$.
*   **Add 1** to the least significant digit of the $(r-1)$'s complement.
*   Alternatively, it can be calculated as $r^n - N$.

#### Example (Base 10, 4 digits)
*   Find the 10's complement of $N = 3456_{10}$:
    1.  Find the 9's complement: $6543_{10}$
    2.  Add 1: $6543 + 1 = 6544_{10}$
    *   Using the formula: $10^4 - 3456 = 10000 - 3456 = 6544_{10}$.

#### Example (Base 8, 3 digits)
*   Find the 8's complement of $N = 253_8$:
    1.  Find the 7's complement: $524_8$
    2.  Add 1: $524_8 + 1_8 = 525_8$
    *   Using the formula: $8^3 - 253_8 = 512_{10} - 171_{10} = 341_{10}$.
        *   To convert $341_{10}$ to base 8: $341 / 8 = 42$ R $5$, $42 / 8 = 5$ R $2$, $5 / 8 = 0$ R $5$. So $341_{10} = 525_8$.

#### Characteristics
*   Has a single representation for zero.
*   Arithmetic (especially subtraction by addition of the complement) is very efficient, as any carry out of the most significant position is simply discarded. This is why it's widely used in computers.

---

## Comparison Summary

| Feature                 | Signed Magnitude                | 1's Complement                                  | 2's Complement                          | $(r-1)$'s Complement                 | $r$'s Complement                                  |
| :---------------------- | :------------------------------ | :---------------------------------------------- | :-------------------------------------- | :----------------------------------- | :------------------------------------------------ |
| **Positive Numbers**    | Same as unsigned                | Same as unsigned                                | Same as unsigned                        | Same as unsigned                     | Same as unsigned                                  |
| **Negative Numbers**    | Sign bit + magnitude            | Invert all bits of positive                     | Invert all bits of positive, then add 1 | Subtract each digit from $(r-1)$     | $(r-1)$'s complement + 1                          |
| **Zero Representation** | Two (`+0`, `-0`)                | Two (`+0`, `-0`)                                | One (`0`)                               | Two (e.g., `000`, `(r-1)(r-1)(r-1)`) | One (`0`)                                         |
| **Range ($n$ digits)**  | $-(r^{n-1}-1)$ to $(r^{n-1}-1)$ | $-(r^{n-1}-1)$ to $(r^{n-1}-1)$                 | $-r^{n-1}$ to $(r^{n-1}-1)$             | $-(r^{n-1}-1)$ to $(r^{n-1}-1)$      | $-r^{n-1}$ to $(r^{n-1}-1)$                       |
| **Arithmetic**          | Complex                         | Requires end-around carry                       | Simple (standard binary addition)       | Requires end-around carry            | Simple (standard addition)                        |
| **Hardware Complexity** | High                            | Moderate                                        | Low                                     | Moderate                             | Low                                               |
| **Usage**               | Rarely used for arithmetic      | Historically, some systems; conceptually useful | **Most common in modern computers**     | Conceptual generalization            | **Widely used for arithmetic in arbitrary bases** |

------

# Carry Error and Signed Overflow Error in Machine Language

## Carry Error

### Definition

A carry error occurs during arithmetic operations when the result of an unsigned integer addition exceeds the maximum representable value for the given bit width.

### Key Characteristics

- Happens in unsigned arithmetic operations
- Indicates that the result is too large to fit in the allocated bit space
- Typically detected by a carry flag in the processor's status register

### Example

```
8-bit unsigned addition:
  11111111 (255 in decimal)
+        1
  --------
 100000000 (Carry occurs - result exceeds 8-bit range)
```

### Representation

- When a carry occurs, the carry flag (C flag) is set to 1
- Processor can use this flag to handle multi-precision arithmetic

## Signed Overflow Error

### Definition

A signed overflow error happens when an arithmetic operation produces a result that cannot be represented within the range of the signed integer's bit representation.

### Key Characteristics

- Occurs in signed integer arithmetic
- Different from carry error in unsigned arithmetic
- Detected by comparing the sign bits before and after the operation

### Two's Complement Representation

In two's complement:

- Leftmost bit represents the sign (0 for positive, 1 for negative)
- Range for 8-bit signed integer: -128 to 127

### Detection Mechanism

Overflow occurs when:

1. Adding two positive numbers results in a negative number
2. Adding two negative numbers results in a positive number

### Example

```
8-bit signed addition:
  01111111 (+127)
+  00000001 (+1)
  --------
  10000000 (Signed Overflow - result is incorrectly interpreted as -128)
```

## Comparison

|Characteristic'|Carry Error'|Signed Overflow Error'|
|---|---|---|
|Arithmetic Type'|Unsigned|Signed|
|Flag Indication'|Carry Flag|Overflow Flag|
|Bit Interpretation'|Total magnitude|Sign and magnitude|

## Practical Implications

- Critical in low-level programming
- Important for:
    - Embedded systems
    - Compiler design
    - Security-sensitive computations
    - Numerical computing

## Prevention Strategies

1. Range checking before operations
2. Using larger integer types
3. Implementing explicit overflow handling
4. Using saturating arithmetic operations

## Code Example (Pseudo-assembly)

```
; Check for unsigned carry
ADD R1, R2
BCS carry_occurred  ; Branch if Carry Set

; Check for signed overflow
ADD R1, R2
BVS overflow_occurred  ; Branch if Overflow Set
```
