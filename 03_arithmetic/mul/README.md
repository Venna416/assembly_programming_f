# Multiplication

## mul1.asm

### Operation

The program multiplies two 8-bit numbers:

num1 = 25
num2 = 10

The operation performed is:

25 × 10 = 250

The `MUL` instruction uses AL as the first operand and stores the 16-bit result in AX.

### GDB Results

AX = 0x00FA = 250

EFLAGS = 0x202

Flags displayed:

IF

Therefore:

CF = 0
OF = 0

### Result

The final result is:

250


---

## mul2.asm

### Operation

The program multiplies two 16-bit numbers:

num1 = 3000
num2 = 200

The operation performed is:

3000 × 200 = 600000

For 16-bit multiplication, the 32-bit result is stored in DX:AX.

AX contains the lower 16 bits of the result.

DX contains the upper 16 bits of the result.

### GDB Results

AX = 0x27C0 = 10176

DX = 0x0009 = 9

EFLAGS = 0xA03

Flags displayed:

CF IF OF

Therefore:

CF = 1
OF = 1

The complete result is:

DX:AX = 0009:27C0

Therefore:

3000 × 200 = 600000

### Result

The final result is:

600000



---


