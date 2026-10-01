# Addition

## add1.asm

### Description

This program demonstrates 8-bit addition.

The program adds two 8-bit values stored in memory.

### Operation

120 + 10 = 130

# Addition

## add1.asm

### Operation

The program adds two 8-bit numbers:

num1 = 120
num2 = 10

The operation performed is:

120 + 10 = 130

The result is stored in AL and then moved to the result variable.

### GDB Results

AL = 0x82 = 130

GDB also displays AL as:

AL = -126

This is because 0x82 represents 130 as an unsigned 8-bit value, but -126 when interpreted as a signed 8-bit value.

EFLAGS = 0xA96

Flags displayed:

PF AF SF IF OF

Therefore:

CF = 0
OF = 1
PF = 1
AF = 1

### Result

The final result is:

130


---

## add2.asm

### Operation

The program adds two 16-bit numbers:

num1 = 32000
num2 = 500

The operation performed is:

32000 + 500 = 32500

The result is stored in AX and then moved to the result variable.

### GDB Results

AX = 0x7EF4 = 32500

EAX = 0x7EF4 = 32500

EFLAGS = 0x202

Flags displayed:

IF

Therefore:

CF = 0
OF = 0
ZF = 0
SF = 0
PF = 0
AF = 0

### Result

The final result is:

32500


---

## add3.asm

### Operation

This program demonstrates addition with carry using the ADC instruction.

The values used are:

num1 = 0xFFFF
num2 = 1

The first operation is:

0xFFFF + 1 = 0x0000

This produces a carry:

CF = 1

The program then executes:

adc ax, 0

ADC adds the value of the Carry Flag to AX.

Therefore:

0x0000 + CF
= 0x0000 + 1
= 0x0001

### Result

The ADC instruction demonstrates how a carry from a previous addition can be included in a subsequent addition.
