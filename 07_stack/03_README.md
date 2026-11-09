# 03.asm – Function Calls and Return Addresses

## Introduction

This program demonstrates how the CALL and RET instructions work in 64-bit assembly language. It shows how the stack is used to store a return address when a function is called and how that address is retrieved when the function finishes executing.

## Program Execution

The program begins at `_start` and loads the value 10 into the RAX register using `mov rax, 10`.

Next, `call calculate` transfers execution to the calculate function. Before jumping to the function, CALL automatically pushes the return address onto the stack. The return address points to the instruction immediately following the CALL instruction.

Inside the calculate function, `add rax, 5` adds 5 to the existing value in RAX.

The calculation is:

10 + 5 = 15

The result is stored in RAX.

The `ret` instruction retrieves the saved return address from the stack and transfers execution back to the instruction following the original CALL instruction.

The program then reaches the `after_call` section, where the NOP instruction performs no operation.

Finally, the program loads 60 into RAX to invoke the Linux 64-bit exit system call, clears RDI to set the exit status to zero and executes SYSCALL.

## Stack Pointer Changes

Assuming the original RSP value is S:

| Instruction       | RSP value |
|-------------------|-----------|
| Initial state     | S         |
| `mov rax, 10`     | S         |
| `call calculate`  | S - 8     |
| `add rax, 5`      | S - 8     |
| `ret`             | S         |
| `nop`             | S         | 

The CALL instruction decreases RSP by 8 bytes because it pushes the return address onto the stack. RET increases RSP by 8 bytes when it retrieves that address.

## How the Stack Works in This Program

The stack is used to temporarily store the return address during the function call.

This allows the processor to know where execution should continue after the function finishes.

The program does not explicitly use PUSH or POP instructions. Instead, CALL and RET perform the necessary stack operations automatically.

## Observations

- The program executes successfully without displaying output.
- The CALL instruction automatically pushes the return address onto the stack.
- RSP decreases by 8 bytes during the function call.
- The calculate function adds 5 to the original value of 10.
- The result of 15 is stored in RAX before returning.
- RET retrieves the return address and restores RSP.
- The program demonstrates how functions use the stack to manage execution flow
