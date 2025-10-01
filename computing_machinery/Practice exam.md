# COMP 2655: Computer Architecture and Organization
## Midterm 1 Practice Examination
**Fall 2025**

---

**Student Name:** ___________________________

**Student ID:** ___________________________

---

## Instructions
- This examination contains **8 sections** with multiple questions.
- Answer all questions in the space provided.
- Show all your work. Partial credit may be awarded.
- For numerical answers, express final results in the base requested.
- You may use one letter-sized reference sheet (both sides).
- No electronic devices permitted except a basic calculator.
- **Time allowed: 120 minutes**

---

## Grading Table

| Section | Topic | Marks | Score |
|---------|-------|-------|-------|
| 1 | Introductory Material | /15 | |
| 2 | Number Systems | /20 | |
| 3 | Integer Representation | /25 | |
| 4 | Arithmetic & Error Detection | /20 | |
| 5 | Bit-Wise Operations | /15 | |
| 6 | Characters & Booleans | /10 | |
| 7 | Computer Architecture | /20 | |
| 8 | 68000 Assembly Language | /25 | |
| **TOTAL** | | **/150** | |

---

## Section 1: Introductory Material [15 marks]

### Question 1 [6 marks]

**(a)** Define the term *computer architecture*. **[2 marks]**

```
Answer:




```

**(b)** Define the term *computer organization*. **[2 marks]**

```
Answer:




```

**(c)** Explain the key difference between these two terms. **[2 marks]**

```
Answer:




```

---

### Question 2 [4 marks]

List four elements of a computer architecture that an assembly language programmer can directly access or manipulate.

```
Answer:
1.

2.

3.

4.
```

---

### Question 3 [5 marks]

Compare high-level programming languages and assembly language by:

**(a)** Stating two advantages of high-level languages over assembly. **[2 marks]**

```
Answer:
1.

2.
```

**(b)** Stating one advantage of assembly language over high-level languages. **[1 mark]**

```
Answer:


```

**(c)** Giving one situation where assembly language would be preferred. **[2 marks]**

```
Answer:



```

---

## Section 2: Number Systems and Conversions [20 marks]

### Question 4 [5 marks]

**(a)** In base 13, what is the range of valid digits? **[1 mark]**

```
Answer:

```

**(b)** How many unique digits exist in base 8? **[1 mark]**

```
Answer:

```

**(c)** What is the maximum digit value in hexadecimal (base 16)? **[1 mark]**

```
Answer:

```

**(d)** Why do modern computers use binary (base 2) instead of decimal (base 10)? Give two reasons. **[2 marks]**

```
Answer:
1.

2.
```

---

### Question 5 [6 marks]

Using Horner's rule, convert `3A7E₁₆` to decimal. Show all steps clearly.

```
Work:












Answer:

```

---

### Question 6 [5 marks]

Convert `187₁₀` to:

**(a)** Binary **[2 marks]**

```
Work:




Answer:

```

**(b)** Octal **[2 marks]**

```
Work:




Answer:

```

**(c)** Hexadecimal **[1 mark]**

```
Work:


Answer:

```

---

### Question 7 [4 marks]

Without converting to decimal first, convert `11010110₂` directly to:

**(a)** Hexadecimal **[2 marks]**

```
Work:



Answer:

```

**(b)** Octal **[2 marks]**

```
Work:



Answer:

```

---

## Section 3: Integer Representation [25 marks]

### Question 8 [8 marks]

Represent `+52₁₀` in 8-bit format using each of the following representations. Express your final answers in both binary and hexadecimal.

**(a)** Unsigned **[2 marks]**

```
Binary:

Hex:
```

**(b)** Signed magnitude **[2 marks]**

```
Binary:

Hex:
```

**(c)** Two's complement **[2 marks]**

```
Binary:

Hex:
```

**(d)** One's complement **[2 marks]**

```
Binary:

Hex:
```

---

### Question 9 [8 marks]

Repeat Question 8 for `-52₁₀` in all four representations.

**(a)** Unsigned **[2 marks]**

```
Answer/Explanation:


```

**(b)** Signed magnitude **[2 marks]**

```
Binary:

Hex:
```

**(c)** Two's complement **[2 marks]**

```
Work:



Binary:

Hex:
```

**(d)** One's complement **[2 marks]**

```
Work:



Binary:

Hex:
```

---

### Question 10 [6 marks]

For a 12-bit representation, state the minimum and maximum values (in decimal) that can be represented using:

**(a)** Unsigned **[2 marks]**

```
Minimum:

Maximum:
```

**(b)** Two's complement **[2 marks]**

```
Minimum:

Maximum:
```

**(c)** Signed magnitude **[2 marks]**

```
Minimum:

Maximum:
```

---

### Question 11 [3 marks]

**(a)** How many representations of zero exist in two's complement? **[1 mark]**

```
Answer:

```

**(b)** How many representations of zero exist in one's complement? **[1 mark]**

```
Answer:

```

**(c)** Why is having only one zero representation an advantage? **[1 mark]**

```
Answer:


```

---

## Section 4: Arithmetic and Error Detection [20 marks]

### Question 12 [6 marks]

Perform the following 8-bit unsigned binary addition. Show all work including any carry bits.

```
    11010110₂
  + 00111101₂
  ___________
```

**(a)** What is the result? **[3 marks]**

```
Work:




Answer:

```

**(b)** Did an error occur? If so, what type of error and how do you detect it? **[3 marks]**

```
Answer:




```

---

### Question 13 [7 marks]

Perform the following 8-bit two's complement addition:

```
    01101100₂
  + 01011010₂
  ___________
```

**(a)** What is the result in binary? **[3 marks]**

```
Work:




Answer:

```

**(b)** What are the signs of the two operands and the result? **[2 marks]**

```
Answer:
Operand 1:
Operand 2:
Result:
```

**(c)** Did overflow occur? Explain how you know. **[2 marks]**

```
Answer:



```

---

### Question 14 [4 marks]

Perform the following 8-bit two's complement subtraction:

```
    10101100₂
  - 00101110₂
  ___________
```

Show your work and indicate whether overflow occurred.

```
Work:








Overflow (Yes/No):

Explanation:


```

---

### Question 15 [3 marks]

Explain the difference between unsigned carry and signed overflow. When does each type of error occur?

```
Answer:
Unsigned carry:



Signed overflow:



```

---

## Section 5: Bit-Wise Operations [15 marks]

### Question 16 [8 marks]

Given `X = 10110100₂` and `Y = 11001010₂`, calculate:

**(a)** X AND Y **[2 marks]**

```
Work:
  10110100
& 11001010
___________

Answer:

```

**(b)** X OR Y **[2 marks]**

```
Work:
  10110100
| 11001010
___________

Answer:

```

**(c)** X XOR Y **[2 marks]**

```
Work:
  10110100
⊕ 11001010
___________

Answer:

```

**(d)** NOT X **[2 marks]**

```
Work:


Answer:

```

---

### Question 17 [7 marks]

Perform the following operations on the 8-bit value `10110011₂`:

**(a)** Logical shift left by 2 positions **[2 marks]**

```
Work:


Answer:

```

**(b)** Logical shift right by 3 positions **[2 marks]**

```
Work:


Answer:

```

**(c)** Arithmetic shift right by 2 positions **[2 marks]**

```
Work:


Answer:

```

**(d)** What is the key difference between logical and arithmetic right shifts? **[1 mark]**

```
Answer:


```

---

## Section 6: Characters and Booleans [10 marks]

### Question 18 [6 marks]

**(a)** What does ASCII stand for? **[1 mark]**

```
Answer:

```

**(b)** How many bits does standard ASCII use, and how many characters can it represent? **[2 marks]**

```
Answer:


```

**(c)** The ASCII code for 'A' is `65₁₀`. What simple arithmetic operation can convert any uppercase letter to its lowercase equivalent? **[2 marks]**

```
Answer:


```

**(d)** What is the ASCII code range for decimal digits ('0' through '9')? **[1 mark]**

```
Answer:

```

---

### Question 19 [4 marks]

**(a)** How is a Boolean TRUE value typically represented in a byte? **[2 marks]**

```
Answer:


```

**(b)** How is a Boolean FALSE value typically represented in a byte? **[2 marks]**

```
Answer:


```

---

## Section 7: Computer Architecture and Organization [20 marks]

### Question 20 [6 marks]

**(a)** What are two key characteristics of Von Neumann architecture? **[4 marks]**

```
Answer:
1.


2.


```

**(b)** How does Von Neumann architecture differ from Harvard architecture? **[2 marks]**

```
Answer:



```

---

### Question 21 [6 marks]

**(a)** What is the role of the Control Unit (CU) in the CPU? **[2 marks]**

```
Answer:



```

**(b)** What is the role of the Arithmetic Logic Unit (ALU)? **[2 marks]**

```
Answer:



```

**(c)** In the 68000 processor, what is the purpose of the Program Counter (PC)? **[2 marks]**

```
Answer:



```

---

### Question 22 [4 marks]

A computer system has a 24-bit address bus and a 16-bit data bus.

**(a)** How many unique memory locations can this system address? Express your answer as a power of 2 and in decimal with appropriate units (e.g., KB, MB). **[2 marks]**

```
Work:



Answer:

```

**(b)** How many bytes can be transferred in a single data bus operation? **[2 marks]**

```
Work:


Answer:

```

---

### Question 23 [4 marks]

Consider a 16-bit value `0xABCD` stored at memory address `0x2000` in a byte-addressable system.

**(a)** Show how this value is stored in memory using big-endian byte ordering. Indicate which byte is at which address. **[2 marks]**

```
Answer:
Address | Value
--------|------
0x2000  |
0x2001  |
```

**(b)** Show how this value is stored using little-endian byte ordering. **[2 marks]**

```
Answer:
Address | Value
--------|------
0x2000  |
0x2001  |
```

---

## Section 8: 68000 Assembly Language [25 marks]

### Question 24 [4 marks]

For the following line of 68000 assembly code, identify each field:

```assembly
    LOOP    add.l    #5,D0    ; Increment counter
```

**(a)** Label field: ___________________________

**(b)** Opcode field: ___________________________

**(c)** Operand field: ___________________________

**(d)** Comment field: ___________________________

---

### Question 25 [3 marks]

What are the three categories of instructions in a CPU's instruction set? Give one example of each from the 68000.

```
Answer:
1.


2.


3.


```

---

### Question 26 [4 marks]

Define the term *addressing mode*. Why are multiple addressing modes useful?

```
Answer:
Definition:



Why useful:



```

---

### Question 27 [8 marks]

For each of the following 68000 instructions, identify the addressing mode(s) used and briefly describe what the operand is:

**(a)** `move.l #100,D3` **[2 marks]**

```
Addressing mode(s):

Description:

```

**(b)** `move.w D2,D5` **[2 marks]**

```
Addressing mode(s):

Description:

```

**(c)** `move.b RESULT,D1` **[2 marks]**

```
Addressing mode(s):

Description:

```

**(d)** `move.l (A0),D4` **[2 marks]**

```
Addressing mode(s):

Description:

```

---

### Question 28 [6 marks]

Each of the following 68000 code snippets contains an error. Identify the error, explain exactly what is wrong, and show how to fix it.

**(a)** `move.l 25,D0` **[2 marks]**

```
Error:

Explanation:

Fix:
```

**(b)** `add.w D0,#5` **[2 marks]**

```
Error:

Explanation:

Fix:
```

**(c)** `move.b D0,A0` **[2 marks]**

```
Error:

Explanation:

Fix:
```

---

### Question 29 — Hand Execution [20 marks]

Hand-execute each of the following 68000 instructions. Start each instruction with the register contents and condition codes shown below. **DO NOT** treat these as a sequence.

**Initial values:**
- `D0.L = $12345678`
- `D1.L = $FFFF00AB`
- `N = 0, Z = 0, V = 0, C = 0`

For each instruction, provide:
- The updated contents of D0 and D1 (in hexadecimal)
- The updated condition codes (N, Z, V, C)

---

**(a)** `add.b D1,D0` **[5 marks]**

```
Work:








Final state:
D0.L = $
D1.L = $
N =    Z =    V =    C =
```

---

**(b)** `sub.w D0,D1` **[5 marks]**

```
Work:








Final state:
D0.L = $
D1.L = $
N =    Z =    V =    C =
```

---

**(c)** `and.l D1,D0` **[5 marks]**

```
Work:








Final state:
D0.L = $
D1.L = $
N =    Z =    V =    C =
```

---

**(d)** `lsl.w #3,D0` **[5 marks]**

```
Work:








Final state:
D0.L = $
D1.L = $
N =    Z =    V =    C =
```

---

## Extra Workspace

Use this space for rough work or if you need additional space for any question. Clearly indicate which question you are answering.

```


















```

---

## END OF EXAMINATION

---

**Tags:** #comp2655 #midterm #practice-test #computer-architecture #assembly-language