# 01.asm – Basic Stack Operations

## Introduction

This program demonstrates how the stack works in 64-bit assembly language using the PUSH and POP instructions. It shows how values are stored on the stack and retrieved using the Last In, First Out (LIFO) principle.

## Program Execution

The program begins by loading the value 100 into the RAX register and 200 into the RBX register.

The `push rax` instruction places 100 onto the stack. The stack pointer (RSP) decreases by 8 bytes because the program operates in 64-bit mode.

Next, `push rbx` places 200 onto the stack. RSP decreases by another 8 bytes.

The `nop` instruction does not perform any operation.

The program then retrieves the values using POP instructions. The first `pop rcx` removes 200 from the stack and stores it in RCX. RSP increases by 8 bytes.

The next `pop rdx` removes 100 and stores it in RDX. RSP increases by another 8 bytes, returning it to its original position.

## Stack Pointer Changes

| Instruction   | RSP change | Operation 
|-------------  |------------|------------  
| Initial state | 0          | Original stack position 
| `push rax`    | -8 bytes   | Pushes 100 
| `push rbx`    | -8 bytes   | Pushes 200 
| `pop rcx`     | +8 bytes   | Retrieves 200 
| `pop rdx`     | +8 bytes   | Retrieves 100 

## How the Stack Works in This Program

The program demonstrates the LIFO principle, meaning the last value pushed onto the stack is the first one removed.

Although 100 is pushed first, it is retrieved second. The value 200 is pushed last and retrieved first.

The stack is used as temporary storage for the two values while they are being transferred between registers.

## Program Termination

After the stack operations are completed, the program loads 60 into RAX, which represents the Linux 64-bit exit system call.

It then clears RDI using `xor rdi, rdi`, setting the exit status to zero. Finally, `syscall` terminates the program successfully.

## Observations

- The program executes successfully without displaying any output.
- Each PUSH operation decreases RSP by 8 bytes.
- Each POP operation increases RSP by 8 bytes.
- The values are retrieved in reverse order from which they were pushed.
- After both POP operations, RSP returns to its original position.
- The NOP instructions do not affect the stack or register values.
