# COMP 2655 Midterm 1 - Study Notes

## 1. Computer Architecture vs. Organization

**Computer Organization:**

- The **hardware design** of a computer
- Deals with the physical structure, functionality, and interconnection of functional components
- Example: How the CPU is physically wired, circuit design

**Computer Architecture:**

- The **set of resources** provided by hardware for the assembly programmer
- What the programmer can see and use (registers, instruction set, memory addressing)
- Example: Available instructions, number of registers, addressing modes

**Key Difference:** Organization is _how_ it's built; architecture is _what_ the programmer can use.

---

## 2. Programming Language Levels

### High-Level Languages (C++, Python, Java)

**Pros:**

- Easy to read and write
- Portable across different computers
- Abstract away hardware details

**Cons:**

- Slower execution
- Less control over hardware
- Larger program size

### Assembly Language

**Pros:**

- Direct hardware control
- Faster execution than high-level
- Smaller program size
- Human-readable (unlike machine code)

**Cons:**

- Not portable (CPU-specific)
- Harder to write and maintain
- More verbose

### Machine Language (Binary)

**Pros:**

- What the CPU actually executes
- Fastest possible execution

**Cons:**

- Nearly impossible for humans to read/write
- Completely non-portable

---

## 3. Number Systems & Conversions

### Positional Number Systems

- Each digit position has a **value based on its position**
- Position numbering starts from 0 at the rightmost digit
- General formula: `dn × base^n + ... + d1 × base^1 + d0 × base^0`

**Example:** 4321₁₀ = 4×10³ + 3×10² + 2×10¹ + 1×10⁰

### Important Bases

- **Binary (base 2):** Digits 0-1
- **Octal (base 8):** Digits 0-7
- **Decimal (base 10):** Digits 0-9
- **Hexadecimal (base 16):** Digits 0-9, A-F

### Horner's Rule

An efficient method to convert from any base to decimal.

**Example:** Convert 1403₅ to decimal

- Start from leftmost digit
- 1 × 5 = 5
- (5 + 4) × 5 = 45
- (45 + 0) × 5 = 225
- 225 + 3 = **228₁₀**

### Related Bases (Hex ↔ Binary)

- 1 hex digit = 4 binary digits
- **Example:** A7₁₆ = 1010 0111₂

---

## 4. Fixed-Length Binary Numbers

### Unsigned Binary

- **8-bit range:** 0 to 255 (0 to 2⁸-1)
- **16-bit range:** 0 to 65,535
- MSBit = Most Significant Bit (leftmost)
- LSBit = Least Significant Bit (rightmost)

---

## 5. Signed Number Representations

### Signed Magnitude

- **MSBit is the sign bit:** 0 = positive, 1 = negative
- Remaining bits represent magnitude
- **Problem:** Two representations of zero (0000 and 1000)
- **8-bit range:** -127 to +127

**Example (4-bit):**

- +5 = 0101
- -5 = 1101

### One's Complement

- Negate by **flipping all bits**
- **Problem:** Still has two zeros
- **8-bit range:** -127 to +127

**Example (4-bit):**

- +5 = 0101
- -5 = 1010 (flip all bits)

### Two's Complement ⭐ (Most Common)

- Negate by: **flip all bits, then add 1**
- **Only one zero!**
- **8-bit range:** -128 to +127
- MSBit still indicates sign

**Example (4-bit):**

- +5 = 0101
- -5 = 1010 + 1 = 1011

**Important:** Negative range is one larger than positive range!

---

## 6. Binary Addition & Subtraction

### Addition Rules (any bit position)

- 0 + 0 = 0
- 0 + 1 = 1
- 1 + 0 = 1
- 1 + 1 = 10 (result is 0, carry 1)

**Process:** Add right to left, carrying as needed

### Subtraction

- Can convert to addition: A - B = A + (-B)
- For two's complement, just add the negative

---

## 7. Error Detection

### Unsigned Carry

- Occurs when adding two unsigned numbers produces a result **too large** for the fixed length
- **Detection:** A carry out of the MSBit position

### Signed Overflow

- Occurs in two's complement when:
    - Adding two large **positive** numbers → negative result
    - Adding two large **negative** numbers → positive result
- **Detection:** Carry into MSBit ≠ carry out of MSBit
- **Rule:** Overflow only when both operands have the **same sign**, but result has **different sign**

---

## 8. Bitwise Operations

### Logical Operations (bit-by-bit)

- **NOT:** Flip each bit (0→1, 1→0)
- **AND:** Result is 1 only if both bits are 1
- **OR:** Result is 1 if either bit is 1
- **XOR:** Result is 1 if bits are different

### Shifting Operations

**Logical Shift Left (LSL):**

- Shift bits left, fill right with 0s
- Each shift = multiply by 2

**Logical Shift Right (LSR):**

- Shift bits right, fill left with 0s
- Each shift = divide by 2 (unsigned)

**Arithmetic Shift Right (ASR):**

- Shift right but preserve sign bit
- Use for signed division by 2

**Rotate:**

- Bits shifted out wrap around to the other end

### Masking

- Use AND to **extract** specific bits (mask = 1 for bits you want)
- Use OR to **set** specific bits to 1
- Use XOR to **toggle** specific bits

---

## 9. Character & Boolean Representation

### ASCII

- **7-bit code** (128 characters), usually stored in 8 bits
- Control characters: 0-31
- Digits: 48-57 ('0' = 48)
- Uppercase: 65-90 ('A' = 65)
- Lowercase: 97-122 ('a' = 97)

**Note:** Lowercase - Uppercase = 32 (easy conversion)

### Booleans

- Typically stored as a byte
- 0 = false, non-zero = true

---

## 10. Von Neumann Architecture

### Key Characteristics

1. Memory stores **both instructions and data**
2. Memory is **addressable** (each location has an address)
3. Execution is **sequential** by default
4. CPU controls execution

### Main Components

**CPU (Central Processing Unit):**

- **CU (Control Unit):** Fetches and decodes instructions
- **ALU (Arithmetic Logic Unit):** Performs calculations
- **Registers:** Fast storage inside CPU

**Main Memory:**

- Stores programs and data
- **ROM:** Read-Only Memory (permanent)
- **RAM:** Random Access Memory (temporary)

**Bus:**

- **Address Bus:** Carries memory addresses (CPU → Memory)
- **Data Bus:** Carries data (bidirectional)
- **Control Bus:** Carries control signals

**Clock:**

- Synchronizes all operations

---

## 11. Memory Organization

### Addressing

- **Byte-addressable:** Each byte has its own address
- **Address space:** Total addressable memory

**Formula:** Address bus width of n bits = 2ⁿ addressable locations

### Endianness

**Big-Endian:**

- Most significant byte at lowest address
- "Big end first"

**Little-Endian:**

- Least significant byte at lowest address
- "Little end first"

**Example:** Store 0x1234 at address 1000:

- Big-endian: [1000]=12, [1001]=34
- Little-endian: [1000]=34, [1001]=12

---

## 12. 68000 Registers

### Data Registers

- **D0-D7:** Eight 32-bit registers
- Used for arithmetic, logic, data manipulation

### Address Registers

- **A0-A7:** Eight 32-bit registers
- Used to hold memory addresses
- **A7 = Stack Pointer (SP)**

### Special Registers

- **PC (Program Counter):** Address of next instruction
- **SR (Status Register):** Contains condition codes

**Condition Codes (flags):**

- **N (Negative):** Result is negative
- **Z (Zero):** Result is zero
- **V (Overflow):** Signed overflow occurred
- **C (Carry):** Unsigned carry occurred

---

## 13. 68000 Assembly Syntax

### Line Format

```
[label]  opcode[.size]  [operands]  [;comment]
```

### Size Descriptors

- **.b** = byte (8 bits)
- **.w** = word (16 bits) [default if omitted]
- **.l** = longword (32 bits)

### Two-Operand Format

```
opcode  source, destination
```

Result goes in destination; source unchanged.

---

## 14. Addressing Modes

### Immediate (#)

- Operand **is** the value specified
- **Example:** `move.w #5,D0` → D0 = 5
- Can **only** be source operand

### Register Direct

- Operand is in the register
- **Example:** `move.w D1,D0` → D0 = contents of D1

### Absolute

- Operand is at the memory address specified
- **Example:** `move.w value,D0` → D0 = contents of memory at "value"

### Address Register Indirect

- Register **contains an address**; operand is at that address
- **Example:** `move.w (A0),D0` → D0 = contents of memory pointed to by A0
- Think of A0 as a pointer

---

## 15. Instruction Categories

### Data Transfer

- **move:** Copy data
- **clr:** Clear (set to zero)
- **exg:** Exchange two registers
- **lea:** Load Effective Address
- **swap:** Swap halves of register

### Arithmetic

- **add, sub:** Addition, subtraction
- **muls, mulu:** Signed/unsigned multiply
- **divs, divu:** Signed/unsigned divide
- **neg:** Negate
- **ext:** Extend (sign-extend for type conversion)

### Bitwise Logic

- **and, or, eor, not:** Logical operations

### Shifting & Rotating

- **asl, asr:** Arithmetic shift
- **lsl, lsr:** Logical shift
- **rol, ror:** Rotate

### Testing

- **cmp:** Compare (like subtraction but doesn't store result)
- **tst:** Test (compare to zero)

---

## 16. Assembler Directives

### dc (Define Constant)

```
value:  dc.w  100    ; Reserve word, initialize to 100
```

### ds (Define Storage)

```
buffer: ds.b  10     ; Reserve 10 bytes, initialized to 0
```

### equ (Equate)

```
SIZE    equ   100    ; Assembler constant
```

### even

- Align next item to word boundary (even address)

---

## 17. Programming Errors

### Assembly-Time Errors

- Syntax errors
- Undefined labels
- Caught by assembler

### Run-Time Errors

- **Address Error:** Accessing word/long at odd address
- **Bus Error:** Accessing invalid memory location
- Caught during execution

---

## Key Skills to Practice

1. **Convert between bases** (especially binary ↔ hex, using Horner's rule)
2. **Represent signed numbers** in all three systems
3. **Perform binary addition/subtraction**
4. **Detect overflow/carry**
5. **Calculate bitwise operations** (especially shifts and masks)
6. **Hand-execute 68000 instructions** (know effect on registers and flags)
7. **Calculate address bus width** from memory size
8. **Understand endianness** problems
9. **Write simple 68000 assembly** with correct syntax
10. **Identify addressing modes** from instruction syntax

---

## Study Strategy

Focus on practicing conversions and hand-execution. Understanding _why_ two's complement works is more important than memorizing the table. Make sure you can explain the difference between carry and overflow!