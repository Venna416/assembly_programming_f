# 05.asm – 64-bit Stack Operations with Different Values

## Introduction

This program demonstrates how PUSH and POP instructions work with 64-bit registers. It shows how hexadecimal values are stored on the stack and retrieved in reverse order using the LIFO principle.

## Program Execution

The program begins by loading two hexadecimal values into registers.

The instruction `mov rax, 0x1122334455667788` stores a 64-bit hexadecimal value in RAX.

Next, `mov rbx, 0x1234` stores the hexadecimal value 0x1234 in RBX.

The program then executes `push rax`, which places the value in RAX onto the stack. Since the program operates in 64-bit mode, RSP decreases by 8 bytes.

The instruction `push rbx` places the value in RBX onto the stack and decreases RSP by another 8 bytes.

The NOP instruction does not perform any operation.

The program then retrieves the values using POP instructions.

The first `pop rbx` retrieves the last value pushed, which is 0x1234, and stores it in RBX.

The next `pop rax` retrieves 0x1122334455667788 and stores it in RAX.

The program finishes by loading 60 into RAX, clearing RDI and executing SYSCALL to terminate successfully.

## Stack Pointer Changes

Assuming the original RSP value is S:

| Instruction | RSP value |
|----------------|--------|
| Initial state  | S      |
| `push rax`     | S - 8  |
| `push rbx`     | S - 16 |
| `pop rbx`      | S - 8  |
| `pop rax`      | S      |

Each PUSH operation decreases RSP by 8 bytes, while each POP operation increases it by 8 bytes.

## How the Stack Works in This Program

The stack is used as temporary storage for two hexadecimal values.

The program demonstrates the LIFO principle, where the last value pushed onto the stack is the first one retrieved.

Although the values have different numerical sizes, both PUSH operations reserve 8 bytes because the program uses 64-bit registers.

This demonstrates that the stack operation uses the register's operand size rather than the number of hexadecimal digits representing the value.

## Observations

- The program executes successfully without displaying output.
- RAX initially stores 0x1122334455667788.
- RBX initially stores 0x1234.
- Each PUSH operation decreases RSP by 8 bytes.
- Each POP operation increases RSP by 8 bytes.
- The values are retrieved in reverse order.
- Both values occupy 8 bytes on the stack.
- After both POP operations, RSP returns to its original position.
- The program demonstrates stack operations using hexadecimal values in 64-bit mode.
