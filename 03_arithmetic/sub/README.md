# Subtraction

## sub1.asm

### Operation

The program subtracts two 8-bit numbers:

num1 = 50
num2 = 80

The operation performed is:

50 - 80 = -30

The subtraction is performed using the AL register.

### GDB Results

AL = 0xE2 = 226 unsigned

When interpreted as a signed 8-bit value:

AL = -30

EFLAGS = 0x287

Flags displayed:

CF PF SF IF

Therefore:

CF = 1
PF = 1
SF = 1
OF = 0

### Result

The final signed result is:

-30


---

## sub2.asm

### Operation

The program subtracts two 16-bit numbers:

num1 = 1000
num2 = 2000

The operation performed is:

1000 - 2000 = -1000

The subtraction is performed using the AX register.

### GDB Results

AX = 0xFC18 = 64536 unsigned

When interpreted as a signed 16-bit value:

AX = -1000

EFLAGS = 0x287

Flags displayed:

CF PF SF IF

Therefore:

CF = 1
PF = 1
SF = 1
OF = 0

### Result

The final signed result is:

-1000


