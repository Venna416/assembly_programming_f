# 06.asm – 32-bit Stack Operations with Different Values

## Introduction

This program demonstrates how PUSH and POP instructions work with 32-bit registers. It shows how hexadecimal values are stored on the stack and retrieved in reverse order using the Last In, First Out (LIFO) principle.

## Program Execution

The program begins with `BITS 32`, which tells NASM to assemble the program in 32-bit mode.

At `_start`, the instruction `mov eax, 0x11223344` loads a hexadecimal value into EAX.

Next, `mov ebx, 0x1234` loads another hexadecimal value into EBX.

The program then executes `push eax`, which places the value in EAX onto the stack. Since this is a 32-bit program, ESP decreases by 4 bytes.

The instruction `push ebx` places the value in EBX onto the stack and decreases ESP by another 4 bytes.

The NOP instruction does not perform any operation.

The values are then retrieved using POP instructions.

The first `pop ebx` retrieves the last value pushed, which is 0x1234, and stores it in EBX.

The next `pop eax` retrieves 0x11223344 and stores it in EAX.

Finally, the program loads 1 into EAX to invoke the Linux 32-bit exit system call. It clears EBX to set the exit status to zero and executes `int 0x80` to terminate.

## Stack Pointer Changes

Assuming the original ESP value is S:

| Instruction     | ESP value 
|-----------------|-------|
| Initial state   | S     |
| `push eax`      | S - 4 |
| `push ebx`      | S - 8 |
| `pop ebx`       | S - 4 |
| `pop eax`       | S     |

Each PUSH operation decreases ESP by 4 bytes, while each POP operation increases ESP by 4 bytes.

## How the Stack Works in This Program

The stack is used as temporary storage for two hexadecimal values.

The program demonstrates the LIFO principle, where the last value pushed onto the stack is the first one retrieved.

Since the program uses 32-bit registers, each PUSH operation reserves 4 bytes on the stack, regardless of the numerical size of the value being stored.

## Observations

- The program executes successfully without displaying output.
- EAX initially stores 0x11223344.
- EBX initially stores 0x1234.
- Each PUSH operation decreases ESP by 4 bytes.
- Each POP operation increases ESP by 4 bytes.
- The values are retrieved in reverse order.
- Both values occupy 4 bytes on the stack.
- After both POP operations, ESP returns to its original position.
- The program demonstrates stack operations using hexadecimal values in 32-bit mode.
