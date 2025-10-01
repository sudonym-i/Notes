# 68000 Assembly Instructions - Detailed Explanation

## General Format

```
instruction.size source, destination
```

- **size:** .b (byte), .w (word), .l (longword)
- **source:** Where data comes from (unchanged)
- **destination:** Where result goes (modified)

---

## 1. DATA TRANSFER INSTRUCTIONS

### MOVE - Copy Data

**Syntax:** `move.size source, destination`

**What it does:** Copies data from source to destination. Source remains unchanged.

**Examples:**

```assembly
move.w #100, D0        ; D0 = 100 (immediate to register)
move.l D1, D2          ; D2 = contents of D1
move.b (A0), D3        ; D3 = byte at address in A0
move.w D4, value       ; Store D4 at memory location 'value'
```

**Affects flags:** N, Z (V and C cleared to 0)

- **N:** Set if result is negative
- **Z:** Set if result is zero

**Common use:** Almost every program uses MOVE constantly to transfer data around

---

### CLR - Clear (Set to Zero)

**Syntax:** `clr.size destination`

**What it does:** Sets the destination to zero. Faster than `move.w #0, destination`

**Examples:**

```assembly
clr.w D0               ; D0 = 0
clr.l (A0)             ; Clear longword at address in A0
clr.b count            ; Set variable 'count' to 0
```

**Affects flags:** N=0, Z=1, V=0, C=0 (always the same since result is always zero)

**Common use:** Initializing variables or counters to zero

---

### EXG - Exchange

**Syntax:** `exg Rx, Ry`

**What it does:** Swaps the contents of two registers. Both must be the same type (both data or both address registers).

**Examples:**

```assembly
exg D0, D1             ; Swap contents of D0 and D1
exg A0, A1             ; Swap contents of A0 and A1
; exg D0, A0           ; ERROR - can't mix types
```

**Affects flags:** None

**Common use:** Swapping values without needing a temporary variable

---

### LEA - Load Effective Address

**Syntax:** `lea source, An`

**What it does:** Loads an **address** into an address register (not the data at that address).

**Examples:**

```assembly
lea buffer, A0         ; A0 = address of 'buffer'
lea 100, A1            ; A1 = 100 (the address 100)
```

**Affects flags:** None

**Common use:** Setting up pointers to arrays or data structures

**Important:** LEA loads the ADDRESS, MOVE loads the DATA

```assembly
lea value, A0          ; A0 points to value
move.w value, D0       ; D0 = contents of value
move.w (A0), D0        ; D0 = contents at address in A0 (same as above)
```

---

### SWAP - Swap Halves

**Syntax:** `swap Dn`

**What it does:** Exchanges the upper and lower 16-bit words of a data register.

**Examples:**

```assembly
; D0 = $12345678
swap D0                ; D0 = $56781234
```

**Affects flags:** N, Z, V=0, C=0

**Common use:** Manipulating 32-bit values, accessing high/low words

---

## 2. ARITHMETIC INSTRUCTIONS

### ADD - Addition

**Syntax:** `add.size source, destination`

**What it does:** Adds source to destination. Result stored in destination. **Formula:** destination = destination + source

**Examples:**

```assembly
add.w #5, D0           ; D0 = D0 + 5
add.l D1, D2           ; D2 = D2 + D1
add.b (A0), D3         ; D3 = D3 + byte at address in A0
```

**Affects flags:** N, Z, V, C

- **N:** Result is negative
- **Z:** Result is zero
- **V:** Signed overflow occurred
- **C:** Unsigned carry occurred

**Common use:** Arithmetic calculations, incrementing counters

---

### SUB - Subtraction

**Syntax:** `sub.size source, destination`

**What it does:** Subtracts source from destination. Result stored in destination. **Formula:** destination = destination - source

**Examples:**

```assembly
sub.w #10, D0          ; D0 = D0 - 10
sub.l D1, D2           ; D2 = D2 - D1
sub.b D3, D4           ; D4 = D4 - D3
```

**Affects flags:** N, Z, V, C

- **V:** Signed overflow (e.g., positive - negative = negative)
- **C:** Unsigned borrow (result "wraps around")

**Common use:** Arithmetic, decrementing counters, computing differences

---

### MULS / MULU - Multiply

**Syntax:**

- `muls.w source, Dn` (signed)
- `mulu.w source, Dn` (unsigned)

**What it does:** Multiplies 16-bit source by low 16 bits of Dn, stores 32-bit result in Dn.

**Examples:**

```assembly
move.w #10, D0
muls.w #5, D0          ; D0 = 10 * 5 = 50 (32-bit result)

move.w #-3, D1
muls.w #4, D1          ; D1 = -3 * 4 = -12 (signed)

move.w #65535, D2
mulu.w #2, D2          ; D2 = 65535 * 2 (unsigned)
```

**Affects flags:** N, Z, V=0, C=0

**Key difference:**

- **MULS:** Treats numbers as signed (two's complement)
- **MULU:** Treats numbers as unsigned

**Common use:** Multiplication, array indexing calculations

---

### DIVS / DIVU - Division

**Syntax:**

- `divs.w source, Dn` (signed)
- `divu.w source, Dn` (unsigned)

**What it does:** Divides 32-bit value in Dn by 16-bit source.

- **Quotient:** Stored in lower 16 bits of Dn
- **Remainder:** Stored in upper 16 bits of Dn

**Examples:**

```assembly
move.l #50, D0
divs.w #7, D0          ; D0.w = 7 (quotient), D0 upper word = 1 (remainder)
                       ; 50 ÷ 7 = 7 remainder 1

move.l #100, D1
divu.w #3, D1          ; D1.w = 33, D1 upper = 1
                       ; 100 ÷ 3 = 33 remainder 1
```

**Affects flags:** N, Z, V (set on overflow/divide-by-zero), C=0

**Common use:** Integer division, modulo operations (use remainder)

**Warning:** Dividing by zero causes an exception (error)!

---

### NEG - Negate

**Syntax:** `neg.size destination`

**What it does:** Replaces destination with its two's complement negative. **Formula:** destination = 0 - destination

**Examples:**

```assembly
move.w #5, D0
neg.w D0               ; D0 = -5

move.w #-10, D1
neg.w D1               ; D1 = 10
```

**Affects flags:** N, Z, V, C

**Common use:** Changing sign of a number, absolute value calculations

---

### EXT - Extend Sign

**Syntax:**

- `ext.w Dn` (byte → word)
- `ext.l Dn` (word → longword)

**What it does:** Sign-extends a smaller value to a larger size by copying the sign bit.

**Examples:**

```assembly
move.b #-5, D0         ; D0.b = $FB (1111 1011 in binary)
ext.w D0               ; D0.w = $FFFB (sign bit copied to upper byte)
ext.l D0               ; D0.l = $FFFFFFFB (sign bit copied to all upper bits)

move.b #5, D1          ; D1.b = $05
ext.w D1               ; D1.w = $0005 (zeros filled in)
```

**Affects flags:** N, Z, V=0, C=0

**Common use:** Converting signed bytes/words to larger sizes before arithmetic

**Why needed:** Before doing math on small signed values, extend them to prevent errors

```assembly
move.b #-1, D0         ; D0 = $??????FF (rest is garbage)
ext.w D0               ; D0 = $????FFFF (now properly -1 as a word)
add.w #5, D0           ; D0 = 4 (correct!)
```

---

## 3. BITWISE LOGIC INSTRUCTIONS

### AND - Bitwise AND

**Syntax:** `and.size source, destination`

**What it does:** Performs bitwise AND. Each bit: result is 1 only if both bits are 1.

**Truth table:**

```
0 AND 0 = 0
0 AND 1 = 0
1 AND 0 = 0
1 AND 1 = 1
```

**Examples:**

```assembly
move.b #%11001100, D0
and.b #%11110000, D0   ; D0 = %11000000

; Common use: Extract specific bits (masking)
move.b #%10110101, D1
and.b #%00001111, D1   ; D1 = %00000101 (keep only lower 4 bits)
```

**Affects flags:** N, Z, V=0, C=0

**Common use:**

- Masking (extracting specific bits)
- Clearing specific bits to 0
- Testing if bits are set

---

### OR - Bitwise OR

**Syntax:** `or.size source, destination`

**What it does:** Performs bitwise OR. Each bit: result is 1 if either bit is 1.

**Truth table:**

```
0 OR 0 = 0
0 OR 1 = 1
1 OR 0 = 1
1 OR 1 = 1
```

**Examples:**

```assembly
move.b #%11000000, D0
or.b #%00001111, D0    ; D0 = %11001111

; Common use: Set specific bits to 1
move.b #%10100000, D1
or.b #%00000011, D1    ; D1 = %10100011 (set lower 2 bits)
```

**Affects flags:** N, Z, V=0, C=0

**Common use:**

- Setting specific bits to 1
- Combining bit patterns

---

### EOR - Exclusive OR (XOR)

**Syntax:** `eor.size source, destination`

**What it does:** Performs bitwise XOR. Each bit: result is 1 if bits are different.

**Truth table:**

```
0 XOR 0 = 0
0 XOR 1 = 1
1 XOR 0 = 1
1 XOR 1 = 0
```

**Examples:**

```assembly
move.b #%11001100, D0
eor.b #%11110000, D0   ; D0 = %00111100

; Common use: Toggle specific bits
move.b #%10101010, D1
eor.b #%00001111, D1   ; D1 = %10100101 (toggle lower 4 bits)
```

**Affects flags:** N, Z, V=0, C=0

**Common use:**

- Toggling bits (0→1, 1→0)
- Simple encryption
- XOR with itself = 0: `eor.w D0, D0` clears D0

---

### NOT - Bitwise NOT

**Syntax:** `not.size destination`

**What it does:** Flips all bits (0→1, 1→0). This is one's complement.

**Examples:**

```assembly
move.b #%11001100, D0
not.b D0               ; D0 = %00110011

move.w #$00FF, D1
not.w D1               ; D1 = $FF00
```

**Affects flags:** N, Z, V=0, C=0

**Common use:**

- Inverting bits
- Creating bit masks
- Part of negation process

**Note:** NOT is different from NEG

- NOT: Flips bits (one's complement)
- NEG: Two's complement negative (flip bits + add 1)

---

## 4. SHIFTING & ROTATING INSTRUCTIONS

### ASL - Arithmetic Shift Left

**Syntax:** `asl.size count, Dn` or `asl.size #n, Dn`

**What it does:** Shifts bits left, fills right with 0, last bit shifted out goes to C flag.

**Visual:**

```
Before: 0110 1101
After:  1101 1010
        ↑        ↑
        C        0 filled in
```

**Examples:**

```assembly
move.b #%00001111, D0
asl.b #1, D0           ; D0 = %00011110, C = 0

move.w #$0040, D1
asl.w #2, D1           ; D1 = $0100 (multiply by 4)
```

**Affects flags:** N, Z, V, C (C = last bit shifted out)

**Common use:**

- Multiply by powers of 2 (each shift = × 2)
- Bit manipulation

---

### ASR - Arithmetic Shift Right

**Syntax:** `asr.size count, Dn` or `asr.size #n, Dn`

**What it does:** Shifts bits right, **preserves sign bit**, last bit shifted out goes to C flag.

**Visual (signed number):**

```
Before: 1110 1100  (negative)
After:  1111 0110  (still negative - sign preserved)
        ↑        ↑
     sign kept   C
```

**Examples:**

```assembly
move.b #%11110000, D0  ; -16 in two's complement
asr.b #1, D0           ; D0 = %11111000 = -8 (divide by 2, sign kept)

move.w #100, D1
asr.w #2, D1           ; D1 = 25 (divide by 4)
```

**Affects flags:** N, Z, V=0, C (C = last bit shifted out)

**Common use:**

- Divide signed numbers by powers of 2
- Bit manipulation while preserving sign

---

### LSL - Logical Shift Left

**Syntax:** `lsl.size count, Dn` or `lsl.size #n, Dn`

**What it does:** Identical to ASL (shifts left, fills with 0).

**Examples:**

```assembly
move.b #%00001010, D0
lsl.b #2, D0           ; D0 = %00101000
```

**Affects flags:** N, Z, V=0, C

**Common use:** Same as ASL - multiply by powers of 2

---

### LSR - Logical Shift Right

**Syntax:** `lsr.size count, Dn` or `lsr.size #n, Dn`

**What it does:** Shifts bits right, fills left with 0 (does NOT preserve sign).

**Visual:**

```
Before: 1110 1100
After:  0111 0110
        ↑        ↑
        0        C
```

**Examples:**

```assembly
move.b #%11110000, D0
lsr.b #1, D0           ; D0 = %01111000 (sign NOT preserved)

move.w #100, D1
lsr.w #2, D1           ; D1 = 25 (divide unsigned by 4)
```

**Affects flags:** N, Z, V=0, C

**Common use:**

- Divide unsigned numbers by powers of 2
- Extract upper bits

**Key difference ASR vs LSR:**

- **ASR:** Preserves sign (for signed division)
- **LSR:** Fills with 0 (for unsigned division)

---

### ROL - Rotate Left

**Syntax:** `rol.size count, Dn` or `rol.size #n, Dn`

**What it does:** Rotates bits left, bit shifted out wraps to the right end.

**Visual:**

```
Before: 1010 0011
After:  0100 0111
        ↑↓
     wraps around
```

**Examples:**

```assembly
move.b #%10110001, D0
rol.b #1, D0           ; D0 = %01110011
```

**Affects flags:** N, Z, V=0, C (C = last bit rotated out)

**Common use:**

- Circular bit patterns
- Bit manipulation without losing data

---

### ROR - Rotate Right

**Syntax:** `ror.size count, Dn` or `ror.size #n, Dn`

**What it does:** Rotates bits right, bit shifted out wraps to the left end.

**Visual:**

```
Before: 1010 0011
After:  1101 0001
           ↓↑
     wraps around
```

**Examples:**

```assembly
move.b #%10110001, D0
ror.b #1, D0           ; D0 = %11011000
```

**Affects flags:** N, Z, V=0, C

**Common use:** Same as ROL, but in opposite direction

---

## 5. SINGLE BIT OPERATIONS

### BSET - Bit Set

**Syntax:** `bset #n, destination` or `bset Dn, destination`

**What it does:** Sets bit n to 1 (where n is bit position 0-7 for byte, 0-31 for long).

**Examples:**

```assembly
move.b #%00000000, D0
bset #3, D0            ; D0 = %00001000 (bit 3 set to 1)
bset #0, D0            ; D0 = %00001001 (bit 0 set to 1)
```

**Affects flags:** Z = opposite of bit's previous value

**Common use:** Setting status flags, enabling features

---

### BCLR - Bit Clear

**Syntax:** `bclr #n, destination`

**What it does:** Clears bit n to 0.

**Examples:**

```assembly
move.b #%11111111, D0
bclr #3, D0            ; D0 = %11110111 (bit 3 cleared)
```

**Affects flags:** Z = opposite of bit's previous value

**Common use:** Clearing status flags, disabling features

---

### BCHG - Bit Change (Toggle)

**Syntax:** `bchg #n, destination`

**What it does:** Toggles bit n (0→1, 1→0).

**Examples:**

```assembly
move.b #%10101010, D0
bchg #0, D0            ; D0 = %10101011 (bit 0: 0→1)
bchg #0, D0            ; D0 = %10101010 (bit 0: 1→0)
```

**Affects flags:** Z = opposite of bit's previous value

**Common use:** Toggling states, flipping flags

---

### BTST - Bit Test

**Syntax:** `btst #n, source`

**What it does:** Tests if bit n is set, but doesn't change anything. Sets Z flag based on result.

**Examples:**

```assembly
move.b #%00001000, D0
btst #3, D0            ; Z = 0 (bit 3 is 1)
btst #2, D0            ; Z = 1 (bit 2 is 0)
```

**Affects flags:** Z = opposite of bit tested

**Common use:** Checking status flags before making decisions

---

## 6. TESTING & COMPARISON

### CMP - Compare

**Syntax:** `cmp.size source, destination`

**What it does:** Performs subtraction (destination - source) but **doesn't store result**. Only sets flags.

**Examples:**

```assembly
move.w #10, D0
cmp.w #5, D0           ; Compare D0 to 5 (10 - 5)
                       ; D0 unchanged, but Z=0, N=0

move.w #5, D1
cmp.w #5, D1           ; Compare D1 to 5 (5 - 5)
                       ; D1 unchanged, Z=1
```

**Affects flags:** N, Z, V, C (same as SUB)

**Common use:** Testing conditions before branching

```assembly
cmp.w #100, D0         ; Is D0 equal to 100?
beq equal_label        ; Branch if equal (Z=1)
```

**How to interpret flags after CMP:**

- **Z=1:** Values are equal
- **Z=0, N=0:** destination > source
- **Z=0, N=1:** destination < source

---

### TST - Test

**Syntax:** `tst.size destination`

**What it does:** Compares destination to zero (doesn't change destination). Sets flags.

**Examples:**

```assembly
move.w #0, D0
tst.w D0               ; Z=1, N=0

move.w #-5, D1
tst.w D1               ; Z=0, N=1 (negative)

move.w #10, D2
tst.w D2               ; Z=0, N=0 (positive)
```

**Affects flags:** N, Z, V=0, C=0

**Common use:** Checking if value is zero, positive, or negative before branching

---

## 7. MISCELLANEOUS

### NOP - No Operation

**Syntax:** `nop`

**What it does:** Does nothing. Just takes up time.

**Affects flags:** None

**Common use:**

- Timing delays
- Placeholder while debugging
- Required for certain hardware timing

---

## QUICK REFERENCE: Flag Effects

|Instruction|N|Z|V|C|Notes|
|---|---|---|---|---|---|
|MOVE|✓|✓|0|0||
|CLR|0|1|0|0|Always same|
|EXG|-|-|-|-|No flags|
|LEA|-|-|-|-|No flags|
|SWAP|✓|✓|0|0||
|ADD/SUB|✓|✓|✓|✓|All flags|
|MUL/DIV|✓|✓|0|0||
|NEG|✓|✓|✓|✓||
|EXT|✓|✓|0|0||
|AND/OR/EOR|✓|✓|0|0||
|NOT|✓|✓|0|0||
|Shifts/Rotates|✓|✓|*|✓|V varies|
|CMP/TST|✓|✓|✓|✓|Like SUB|
|NOP|-|-|-|-|No flags|

✓ = affected, 0 = cleared, - = unchanged, * = special

---

## Common Patterns & Tips

### Initialize a register to zero

```assembly
clr.w D0               ; Faster and clearer than move.w #0, D0
```

### Multiply by constant power of 2

```assembly
lsl.w #3, D0           ; Multiply by 8 (faster than muls)
```

### Divide by constant power of 2

```assembly
asr.w #2, D0           ; Divide by 4 (signed)
lsr.w #2, D0           ; Divide by 4 (unsigned)
```

### Check if value is zero

```assembly
tst.w D0               ; Better than cmp.w #0, D0
```

### Set a pointer to an array

```assembly
lea array, A0          ; A0 now points to array
```

### Get absolute value

```assembly
tst.w D0               ; Check if negative
bpl skip               ; Branch if positive
neg.w D0               ; Make positive
skip:
```

### Extract lower 4 bits

```assembly
and.b #$0F, D0         ; Mask: keep bits 0-3, clear 4-7
```

### Set bit 5 to 1

```assembly
or.b #%00100000, D0    ; OR with mask
; or
bset #5, D0            ; Direct bit set
```