# 04.asm – 32-bit Stack Frames and Local Variables

## Introduction

This program demonstrates how stack frames are created and used in 32-bit assembly language. It shows how the stack stores return addresses, saves the previous base pointer and provides space for local variables.

## Program Execution

The program starts with `BITS 32`, which tells NASM to assemble the program in 32-bit mode.

Execution begins at `_start`, where `call work` transfers control to the work function. CALL automatically pushes the return address onto the stack, decreasing ESP by 4 bytes.

Inside the work function, `push ebp` saves the previous base pointer. The instruction `mov ebp, esp` then establishes the base pointer for the new stack frame.

Next, `sub esp, 8` reserves 8 bytes of stack space for local variables.

The program stores two values in this space:

- `mov dword [ebp - 4], 100` stores 100 in the first local variable location.
- `mov dword [ebp - 8], 200` stores 200 in the second local variable location.

The values are then retrieved using `mov eax, [ebp - 4]` and `mov ebx, [ebp - 8]`. This places 100 in EAX and 200 in EBX.

The NOP instruction does not perform any operation.

## Stack Pointer Changes

Assuming the original ESP value is S:

| Instruction            | ESP value |
|------------------------|--------|
| Initial state          | S      |
| `call work`            | S - 4  |
| `push ebp`             | S - 8  |
| `mov ebp, esp`         | S - 8  |
| `sub esp, 8`           | S - 16 |
| Store local variables  | S - 16 |
| `mov esp, ebp`         | S - 8  |
| `pop ebp`              | S - 4  |
| `ret`                  | S      |

Each PUSH or CALL operation decreases ESP by 4 bytes in this 32-bit program. RET and POP restore the stack pointer.

## How the Stack Works in This Program

The stack is used to store the return address, save the previous base pointer and provide temporary storage for local variables.

EBP acts as a stable reference point for accessing local variables, while ESP tracks the current top of the stack.

The local variables are accessed using negative offsets from EBP. This allows the program to access stored values without changing ESP.

## Returning from the Function

After retrieving the local variables, `mov esp, ebp` releases the 8 bytes reserved for them.

The `pop ebp` instruction restores the previous base pointer.

Finally, `ret` retrieves the saved return address and returns execution to the instruction following `call work`.

The program then uses the Linux 32-bit exit system call. It loads 1 into EAX, clears EBX to set the exit status to zero and executes `int 0x80` to terminate.

## Observations

- The program executes successfully without displaying output.
- CALL automatically pushes a return address onto the stack.
- Each stack entry occupies 4 bytes in this 32-bit program.
- EBP provides a stable reference for accessing local variables.
- SUB ESP, 8 reserves 8 bytes for the two local variables.
- The program uses EAX and EBX to retrieve the stored values.
- The stack is restored before the function returns.
- ESP returns to its original value after RET.
