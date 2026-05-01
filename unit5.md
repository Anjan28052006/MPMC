# ARM Architecture – Exam Ready Notes

---

## 🔹 1. Load/Store Architecture

### 📌 Definition

ARM follows a **Load/Store Architecture**, which means:

* Only **LDR (Load)** and **STR (Store)** instructions access memory
* All operations (ADD, SUB, etc.) are performed on **registers only**

---

### 📌 Key Rule

❌ Direct memory operation is NOT allowed

```
ADD mem, #5   (Invalid)
```

✅ Correct method:

```
LDR R1, [R2]
ADD R1, R1, #5
STR R1, [R2]
```

---

### 📌 Flow of Execution

Memory → Register → Operation → Register → Memory

---

### 📌 Key Points

* Registers are faster than memory
* Improves speed and efficiency
* Simplifies CPU design

---

## 🔹 2. ARM State vs Thumb State

### 📌 Definition

ARM processors operate in two states:

| State | Instruction Size | Feature          |
| ----- | ---------------- | ---------------- |
| ARM   | 32-bit           | High performance |
| Thumb | 16-bit           | Memory efficient |

---

### 📌 ARM State

* Uses full 32-bit instructions
* More powerful and flexible

---

### 📌 Thumb State

* Uses 16-bit compressed instructions
* Saves memory
* Slightly less powerful

---

### 📌 Switching Between States

* Done using branch instruction like:

```
BX R1
```

* Controlled by least significant bit of address

---

### 📌 Key Points

* ARM → Speed
* Thumb → Memory saving

---

## 🔹 3. Conditional Execution

### 📌 Definition

Conditional execution allows instructions to execute **only if a condition is true**

---

### 📌 Based on Flags

Uses flags from CPSR:

* Z (Zero)
* N (Negative)
* C (Carry)
* V (Overflow)

---

### 📌 Example

```
CMP R1, R2
ADDEQ R0, R0, #1
```

👉 ADD executes only if R1 == R2

---

### 📌 Common Conditions

| Condition | Meaning      |
| --------- | ------------ |
| EQ        | Equal (Z=1)  |
| NE        | Not Equal    |
| GT        | Greater Than |
| LT        | Less Than    |

---

### 📌 Advantage

* Reduces branching
* Improves performance
* Avoids pipeline breaks

---

### 📌 ARM vs Thumb

* ARM: Almost all instructions are conditional
* Thumb: Limited conditional execution (uses IT instruction)

---

## 🔹 Final Summary (Exam Point)

* ARM is a **Load/Store architecture**
* Memory is accessed only using **LDR/STR**
* Supports two states:

  * ARM (32-bit, fast)
  * Thumb (16-bit, compact)
* Supports **conditional execution** to reduce branching

---

# ARM Instruction Set – Complete Exam Answer (Detailed Notes)

---

## 🔹 1. Introduction

ARM (Advanced RISC Machine) is a **RISC-based processor architecture** widely used in embedded systems, mobile devices, and IoT.

### 📌 Key Characteristics:

* Uses **simple and fixed-length instructions**
* Focuses on **high performance and low power consumption**
* Based on **Load/Store architecture**

---

## 🔹 2. Features of ARM Instruction Set

### ✅ 1. RISC Architecture

* Simple instructions
* Faster execution
* Each instruction performs a small task

---

### ✅ 2. Load/Store Architecture

* Only **LDR** and **STR** access memory
* All operations are performed on registers

📌 Example:

```
LDR R1, [R2]
ADD R1, R1, #5
STR R1, [R2]
```

---

### ✅ 3. Large Register Set

* 16 registers (R0–R15)

| Register | Purpose              |
| -------- | -------------------- |
| R0–R12   | General purpose      |
| R13      | Stack Pointer (SP)   |
| R14      | Link Register (LR)   |
| R15      | Program Counter (PC) |

---

### ✅ 4. Conditional Execution

* Most instructions can be executed conditionally
* Reduces branching

📌 Example:

```
ADDEQ R1, R2, R3
```

---

### ✅ 5. Pipelining Support

* Improves execution speed
* Multiple instructions processed simultaneously

---

## 🔹 3. Types of ARM Instructions

---

### 🔸 1. Data Processing Instructions

👉 Perform operations on registers

📌 Examples:

```
ADD R0, R1, R2
SUB R0, R1, R2
AND R0, R1, R2
ORR R0, R1, R2
MOV R1, #10
CMP R1, R2
```

📌 Key Point:

* No direct memory access

---

### 🔸 2. Load and Store Instructions

👉 Used to access memory

📌 Examples:

```
LDR R1, [R2]
STR R1, [R2]
```

📌 Key Point:

* Only way to access memory

---

### 🔸 3. Branch Instructions

👉 Used for control flow (loops, conditions, functions)

📌 Examples:

```
B label
BEQ label
BNE label
BL function
```

📌 Key Point:

* BL is used for function calls

---

## 🔹 4. Addressing Modes

👉 Define how operands are accessed

### 📌 Types:

* Immediate addressing → `#value`
* Register addressing → registers only
* Register indirect → `[R2]`
* Offset addressing → `[R2, #4]`
* Pre-indexed → `[R2, #4]!`
* Post-indexed → `[R2], #4`

---

## 🔹 5. Condition Flags (CPSR)

👉 Used for decision making

| Flag | Meaning  |
| ---- | -------- |
| Z    | Zero     |
| N    | Negative |
| C    | Carry    |
| V    | Overflow |

📌 Example:

```
CMP R1, R2
BEQ label
```

---

## 🔹 6. ARM and Thumb States

| State | Instruction Size | Feature          |
| ----- | ---------------- | ---------------- |
| ARM   | 32-bit           | High performance |
| Thumb | 16-bit           | Memory efficient |

📌 Switching:

```
BX R1
```

---

## 🔹 7. Memory Representation (Theory)

Memory is represented as:

```
mem<data_size>[address]
```

📌 Example:

```
mem32[1000] = 25
```

📌 Used only for explanation (not actual instructions)

---

## 🔹 8. Advantages of ARM Instruction Set

* High speed execution
* Low power consumption
* Efficient memory usage
* Simple instruction design

---

## 🔹 9. Conclusion

ARM instruction set is efficient, simple, and optimized for performance. Its load/store architecture, conditional execution, and multiple addressing modes make it suitable for modern embedded and mobile systems.

---

# Memory Representation in ARM – Detailed Notes

---

## 🔹 1. Basic Concept of Memory

Memory (RAM) is a collection of storage locations where each location has:

* A unique **address**
* A **value** stored at that address

👉 Think of memory like a table:

| Address | Value |
| ------- | ----- |
| 1000    | 10    |
| 1004    | 20    |
| 1008    | 30    |

---

## 🔹 2. Internal Representation (Theory Notation)

In textbooks and exams, memory is represented as:

```
mem<data_size>[address]
```

---

## 🔹 3. Meaning of Each Component

### ✅ mem

* Represents **memory (RAM)**

### ✅ data_size

* Size of data stored at that location

| Data Size | Meaning  | Bytes |
| --------- | -------- | ----- |
| 8         | Byte     | 1     |
| 16        | Halfword | 2     |
| 32        | Word     | 4     |

### ✅ address

* Location in memory

---

## 🔹 4. Examples

### Example 1

```
mem32[1000] = 25
```

👉 A 32-bit value 25 is stored at address 1000

---

### Example 2 (Array Representation)

```
mem32[1000] = 10
mem32[1004] = 20
mem32[1008] = 30
```

👉 Explanation:

* Each value takes 4 bytes (32-bit)
* Address increases by 4
* This is how arrays are stored in memory

---

## 🔹 5. Important: Memory is Byte Addressable

Even though we write mem32, memory is actually stored as **bytes (8 bits)**.

### Example:

```
mem32[1000] = 0x12345678
```

👉 Internally stored as:

| Address | Value (Hex) |
| ------- | ----------- |
| 1000    | 78          |
| 1001    | 56          |
| 1002    | 34          |
| 1003    | 12          |

👉 This is called **Little Endian format** (used in ARM)

---

## 🔹 6. How ARM Instructions Use Memory

### Instruction:

```
LDR R1, [R2]
```

### Internal Meaning:

```
R1 = mem32[R2]
```

---

### Instruction:

```
STR R1, [R2]
```

### Internal Meaning:

```
mem32[R2] = R1
```

---

## 🔹 7. Example with Pre and Post Conditions

### Pre-condition:

```
R2 = 1000
mem32[1000] = 50
```

### Instruction:

```
LDR R1, [R2]
```

### Post-condition:

```
R1 = 50
```

---

## 🔹 8. Key Points for Exam

* Memory is represented as mem<data_size>[address]
* This is **theoretical notation**, not actual instruction
* ARM memory is **byte addressable**
* Data sizes determine how addresses increase
* LDR reads from memory, STR writes to memory

---

![alt text](image.png)

# Data Processing Instructions in ARM – Detailed Exam Notes

---

## 🔹 1. Introduction

Data processing instructions are one of the most important groups of instructions in the ARM instruction set.

These instructions are used to perform operations such as:

* Arithmetic operations
* Logical operations
* Data movement
* Comparison operations

---

## 🔹 2. Important Point

Data processing instructions operate on the contents of **registers**.

They **do not directly affect memory**.

This means ARM first loads data from memory into registers, performs the operation inside the CPU, and then stores the result back to memory if needed.

---

## 🔹 3. Why Data Processing Instructions Use Registers

ARM is a **Load/Store architecture**.

So:

* Memory can be accessed only using `LDR` and `STR`
* Arithmetic and logical operations are done only on registers

### Example:

```asm
LDR R1, [R2]      ; Load value from memory into R1
ADD R3, R1, #5    ; Process data in register
STR R3, [R2]      ; Store result back to memory
```

---

## 🔹 4. General Syntax of Data Processing Instructions

```asm
<operation>{<cond>}{S} Rd, Rn, Operand2
```

---

## 🔹 5. Meaning of Each Part

### ✅ operation

This is the instruction name.

Examples:

```asm
ADD, SUB, AND, ORR, MOV, CMP
```

---

### ✅ cond

This is the optional condition field.

It tells the processor to execute the instruction only if a condition is satisfied.

Examples:

```asm
EQ, NE, GT, LT
```

### Example:

```asm
ADDEQ R0, R1, R2
```

Meaning:

* Add only if equal condition is true

---

### ✅ S

The `S` suffix is optional.

If `S` is used, the instruction updates condition flags in CPSR.

### Example:

```asm
ADDS R0, R1, R2
```

Meaning:

* R0 = R1 + R2
* Flags are also updated

---

### ✅ Rd

`Rd` means destination register.

It stores the final result.

### Example:

```asm
ADD R0, R1, R2
```

Here:

* R0 is destination register

---

### ✅ Rn

`Rn` is the first source register.

### Example:

```asm
ADD R0, R1, R2
```

Here:

* R1 is first operand/source register

---

### ✅ Operand2

Operand2 is the second operand.

It can be:

* Register
* Immediate value
* Shifted register

### Examples:

```asm
ADD R0, R1, R2      ; Operand2 is register
ADD R0, R1, #5      ; Operand2 is immediate value
ADD R0, R1, R2, LSL #1  ; Operand2 is shifted register
```

---

# 🔹 6. Classification of Data Processing Instructions

Data processing instructions are mainly classified into two types:

1. Manipulation instructions
2. Comparison instructions

---

# 🔸 A. Manipulation Instructions

Manipulation instructions perform actual operations and store the result in a destination register.

They have a destination register `Rd`.

### General form:

```asm
Instruction Rd, Rn, Operand2
```

---

## 1. Arithmetic Instructions

Arithmetic instructions perform mathematical operations.

---

### ✅ ADD – Addition

```asm
ADD R0, R1, R2
```

Meaning:

```asm
R0 = R1 + R2
```

Example:
If:

```asm
R1 = 5
R2 = 3
```

Then:

```asm
R0 = 8
```

---

### ✅ ADC – Add with Carry

```asm
ADC R0, R1, R2
```

Meaning:

```asm
R0 = R1 + R2 + Carry
```

It is used when adding large numbers that require carry from previous addition.

---

### ✅ SUB – Subtraction

```asm
SUB R0, R1, R2
```

Meaning:

```asm
R0 = R1 - R2
```

Example:
If:

```asm
R1 = 10
R2 = 4
```

Then:

```asm
R0 = 6
```

---

### ✅ SBC – Subtract with Carry

```asm
SBC R0, R1, R2
```

Meaning:

```asm
R0 = R1 - R2 - NOT Carry
```

It is mainly used in multi-word subtraction.

---

### ✅ RSB – Reverse Subtract

```asm
RSB R0, R1, R2
```

Meaning:

```asm
R0 = R2 - R1
```

This is different from SUB.

### Difference:

```asm
SUB R0, R1, R2   ; R0 = R1 - R2
RSB R0, R1, R2   ; R0 = R2 - R1
```

---

### ✅ RSC – Reverse Subtract with Carry

```asm
RSC R0, R1, R2
```

Meaning:

```asm
R0 = R2 - R1 - NOT Carry
```

It is used for reverse subtraction involving carry/borrow.

---

## 2. Logical Instructions

Logical instructions perform bitwise operations.

They work on individual bits of the operands.

---

### ✅ AND – Bitwise AND

```asm
AND R0, R1, R2
```

Meaning:

```asm
R0 = R1 AND R2
```

### Example:

```asm
R1 = 0101
R2 = 0011
```

Result:

```asm
R0 = 0001
```

Rule:

* 1 AND 1 = 1
* Otherwise = 0

---

### ✅ ORR – Bitwise OR

```asm
ORR R0, R1, R2
```

Meaning:

```asm
R0 = R1 OR R2
```

### Example:

```asm
R1 = 0101
R2 = 0011
```

Result:

```asm
R0 = 0111
```

Rule:

* If any one bit is 1, result is 1

---

### ✅ EOR – Exclusive OR

```asm
EOR R0, R1, R2
```

Meaning:

```asm
R0 = R1 XOR R2
```

### Example:

```asm
R1 = 0101
R2 = 0011
```

Result:

```asm
R0 = 0110
```

Rule:

* Same bits → 0
* Different bits → 1

---

### ✅ BIC – Bit Clear

```asm
BIC R0, R1, R2
```

Meaning:

```asm
R0 = R1 AND NOT R2
```

It clears selected bits.

### Example:

```asm
R1 = 1111
R2 = 0101
```

NOT R2:

```asm
1010
```

Result:

```asm
R0 = 1111 AND 1010 = 1010
```

---

### ✅ ORN – OR NOT

```asm
ORN R0, R1, R2
```

Meaning:

```asm
R0 = R1 OR NOT R2
```

It performs OR operation with the inverted value of Operand2.

---

## 3. Move Instructions

Move instructions are used to copy or move values into registers.

---

### ✅ MOV – Move

```asm
MOV R0, R1
```

Meaning:

```asm
R0 = R1
```

It copies the value of R1 into R0.

### Example:

```asm
MOV R0, #10
```

Meaning:

```asm
R0 = 10
```

---

### ✅ MVN – Move NOT

```asm
MVN R0, R1
```

Meaning:

```asm
R0 = NOT R1
```

It stores the bitwise complement of R1 into R0.

### Example:

If:

```asm
R1 = 00001111
```

Then:

```asm
R0 = 11110000
```

---

# 🔸 B. Comparison Instructions

Comparison instructions do not store a result in a destination register.

They only update the condition flags in CPSR.

They are mainly used before conditional branch instructions.

---

## Important Point

Comparison instructions are similar to normal data processing instructions with `S`, but they do not store the result.

Example:

```asm
CMP R0, R1
```

It performs:

```asm
R0 - R1
```

But it does not store the result. It only updates flags.

---

## 1. CMP – Compare

```asm
CMP R0, R1
```

Meaning:

```asm
R0 - R1
```

Flags are updated based on the result.

### Example:

```asm
CMP R0, R1
BEQ LABEL
```

If R0 equals R1, Z flag is set and branch occurs.

---

## 2. CMN – Compare Negative

```asm
CMN R0, R1
```

Meaning:

```asm
R0 + R1
```

It updates flags based on addition result.

It is similar to:

```asm
ADDS R0, R0, R1
```

But result is not stored.

---

## 3. TST – Test

```asm
TST R0, R1
```

Meaning:

```asm
R0 AND R1
```

It updates flags based on AND result.

It is commonly used to check whether particular bits are set or clear.

### Example:

```asm
TST R0, #1
```

Meaning:

* Checks whether the least significant bit of R0 is 1 or 0

---

## 4. TEQ – Test Equivalence

```asm
TEQ R0, R1
```

Meaning:

```asm
R0 XOR R1
```

It updates flags based on XOR result.

If R0 and R1 are equal, XOR result becomes 0, so Z flag is set.

---

# 🔹 7. Condition Flags Used

Data processing instructions can update flags if `S` is used.

The four main flags are:

| Flag | Meaning       |
| ---- | ------------- |
| N    | Negative flag |
| Z    | Zero flag     |
| C    | Carry flag    |
| V    | Overflow flag |

---

## Examples:

```asm
ADDS R0, R1, R2
```

Updates flags after addition.

```asm
SUBS R0, R1, R2
```

Updates flags after subtraction.

```asm
CMP R0, R1
```

Always updates flags, but does not store result.

---

# 🔹 8. Examples from Slide

---

## Example 1: ADD

```asm
ADD R0, R1, R2
```

Meaning:

```asm
R0 = R1 + R2
```

If:

```asm
R1 = 5
R2 = 6
```

Then:

```asm
R0 = 11
```

---

## Example 2: TEQ

```asm
TEQ R0, R1
```

Meaning:

```asm
R0 XOR R1
```

If R0 equals R1:

```asm
R0 XOR R1 = 0
```

So:

```asm
Z flag = 1
```

---

## Example 3: MOV

```asm
MOV R0, R1
```

Meaning:

```asm
R0 = R1
```

It copies the contents of R1 into R0.

---

# 🔹 9. Difference Between Manipulation and Comparison Instructions

| Manipulation Instructions                   | Comparison Instructions     |
| ------------------------------------------- | --------------------------- |
| Store result in destination register        | Do not store result         |
| Used for arithmetic/logical/move operations | Used only to set flags      |
| Example: ADD, SUB, AND, MOV                 | Example: CMP, CMN, TST, TEQ |

---

# 🔹 10. Exam-Ready Summary

Data processing instructions in ARM are used to perform arithmetic, logical, move, and comparison operations on register contents. These instructions do not directly access memory. Manipulation instructions store the result in a destination register, while comparison instructions only update the condition flags. The general syntax is `<operation>{cond}{S} Rd, Rn, Operand2`. Examples include ADD, SUB, AND, ORR, MOV, CMP, TST, and TEQ.

---

![alt text](image-1.png)
# Barrel Shifter in ARM – Exam Ready Notes

---

## 🔹 1. Introduction

The **barrel shifter** is a special hardware unit in the ARM processor that allows shifting or rotating of data bits efficiently.

It is mainly used in **data processing instructions** where the **second operand (Operand2)** can be modified before being used by the ALU.

---

## 🔹 2. Key Concept

In ARM instructions:

* Operand1 → directly goes to ALU
* Operand2 → passes through **barrel shifter** → then goes to ALU

---

## 🔹 3. Advantage of Barrel Shifter

* Allows **shift + operation in a single instruction**
* Improves performance
* Reduces number of instructions

### Example:

```asm
ADD R0, R1, R2, LSL #2
```

Meaning:

```asm
R0 = R1 + (R2 << 2)
```

---

## 🔹 4. Types of Shift Operations

---

### ✅ 1. LSL (Logical Shift Left)

```asm
Rm, LSL #n
```

* Shifts bits to the left
* Zeros are filled on the right

📌 Equivalent to multiplication by 2^n

Example:

```
5 (00000101) → LSL #1 → 10 (00001010)
```

---

### ✅ 2. LSR (Logical Shift Right)

```asm
Rm, LSR #n
```

* Shifts bits to the right
* Zeros are filled on the left

📌 Used for unsigned division by 2

Example:

```
8 (00001000) → LSR #1 → 4 (00000100)
```

---

### ✅ 3. ASR (Arithmetic Shift Right)

```asm
Rm, ASR #n
```

* Shifts bits to the right
* Sign bit (MSB) is preserved

📌 Used for signed numbers

---

### ✅ 4. ROR (Rotate Right)

```asm
Rm, ROR #n
```

* Bits shifted right
* Bits falling off re-enter from left

---

### ✅ 5. RRX (Rotate Right Extended)

```asm
Rm, RRX
```

* Rotate right by 1 bit using **Carry flag**

---

## 🔹 5. Shift Amount Specification

Shift amount can be specified in two ways:

---

### 🔸 1. Immediate Shift

```asm
ADD R0, R1, R2, LSL #2
```

* Shift value is constant

---

### 🔸 2. Register Shift

```asm
ADD R0, R1, R2, LSL R3
```

* Shift value is stored in register R3

---

## 🔹 6. General Syntax

```asm
<Instruction> Rd, Rn, Rm, <shift> #amount
```

Example:

```asm
ADD R0, R1, R2, LSL #2
```

---

## 🔹 7. Example with Logical Instruction

```asm
AND R0, R1, R2, LSR #1
```

Meaning:

```asm
R0 = R1 AND (R2 >> 1)
```

---

## 🔹 8. Carry Flag and Shifting

* When shifting occurs, the bit that is shifted out can be stored in the **Carry flag**
* If instruction has `S`, flags are updated

Example:

```asm
MOVS R0, R1, LSL #1
```

---

## 🔹 9. Key Points for Exam

* Barrel shifter modifies Operand2 before ALU operation
* Supports shift and rotate operations
* Improves efficiency by combining operations
* Used in arithmetic and logical instructions

---

## 🔹 10. Exam Summary

The barrel shifter in ARM allows the second operand to be shifted or rotated before being used in data processing instructions. It supports operations such as LSL, LSR, ASR, ROR, and RRX. This feature improves performance by combining shift and arithmetic operations in a single instruction.

---


