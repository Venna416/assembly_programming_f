# Division Examples

## div1.asm

### Description

This program demonstrates 8-bit unsigned division.

The dividend is stored in AX and the divisor is stored in BL.

For 8-bit division:

AX ÷ BL

The quotient is stored in AL and the remainder is stored in AH.

### Calculation

100 ÷ 7 = 14 remainder 2

### GDB Results

AL = 0x0E = 14
AH = 0x02 = 2

Therefore:

Quotient = 14
Remainder = 2

### Flags

The arithmetic flags after DIV are undefined and should not be interpreted as meaningful results.

---

## div2.asm

### Description

This program demonstrates 16-bit unsigned division.

The dividend is stored in DX:AX and the divisor is stored in BX.

For 16-bit division:

DX:AX ÷ BX

The quotient is stored in AX and the remainder is stored in DX.

### Calculation

50000 ÷ 300 = 166 remainder 200

### GDB Results

AX = 0x00A6 = 166
DX = 0x00C8 = 200
BX = 0x012C = 300

Therefore:

Quotient = 166
Remainder = 200

### Flags

The arithmetic flags after DIV are undefined and should not be interpreted as meaningful results.
