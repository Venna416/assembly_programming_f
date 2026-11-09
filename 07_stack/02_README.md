# 02.asm – Stack Frames and Local Variables

## Introduction

This program demonstrates how stack frames are created and used in 64-bit assembly language. It shows how a function saves the previous base pointer, reserves space for local variables, accesses values stored on the stack and restores the stack before returning.

## Program Execution

The program starts at `_start` and executes `call work`. The CALL instruction transfers execution to the work function and automatically pushes the return address onto the stack.

Inside the work function, `push rbp` saves the previous base pointer. The RSP register decreases by 8 bytes.

The instruction `mov rbp, rsp` copies the current stack pointer into RBP. This establishes the base of the new stack frame.

Next, `sub rsp, 16` reserves 16 bytes of memory on the stack for local variables.

The program stores two values in this reserved space:
- `mov qword [rbp - 8], 100` stores 100 at the first local variable location.
- `mov qword [rbp - 16], 200` stores 200 at the second local variable location.

The values are then retrieved using `mov rax, [rbp - 8]` and `mov rbx, [rbp - 16]`. This places 100 in RAX and 200 in RBX.

The NOP instruction does not perform any operation.

## Stack Pointer Changes

Assuming the original RSP value is S:

| Instruction           | RSP value |
|-------------          |-----------|
| Initial state         |     S     |
| `call work`           |   S - 8   |
| `push rbp`            |   S - 16  |
| `mov rbp, rsp`        |   S - 16  |
| `sub rsp, 16`         |   S - 32  |
| Store local variables |   S - 32  |
| `mov rsp, rbp`        |   S - 16  |
| `pop rbp`             |   S - 8   |
| `ret`                 |    S      |

The stack pointer decreases as space is allocated and increases as the function restores the stack.

## How the Stack Works in This Program

The stack is used to store the return address, save the previous base pointer and provide temporary storage for local variables.

RBP acts as a stable reference point for accessing the local variables, while RSP tracks the current top of the stack.

The two local variables are accessed using negative offsets from RBP. This allows the program to retrieve values without changing the stack pointer.

## Returning from the Function

After accessing the local variables, the program executes `mov rsp, rbp`. This releases the 16 bytes reserved for local variables.

The `pop rbp` instruction restores the previous base pointer.

Finally, `ret` removes the saved return address from the stack and transfers execution back to the instruction following `call work` in `_start`.

The program then executes the Linux exit system call and terminates with an exit status of zero.

## Observations

- The program executes successfully without displaying output.
- CALL automatically pushes a return address onto the stack.
- PUSH RBP saves the previous base pointer.
- RBP provides a stable reference for accessing local variables.
- SUB RSP, 16 reserves 16 bytes for local variables.
- Reading and writing local variables does not automatically change RSP.
- The function restores the stack before returning.
- RSP returns to its original value after RET.
