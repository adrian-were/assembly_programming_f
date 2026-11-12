# 01.asm 

## Stack Execution Flow
This program demonstrates the Last-In-First-Out (LIFO) behavior of the stack using basic 64-bit registers.

1. **Initialization:** The execution begins at `_start`, loading the decimal value `100` into `rax` and `200` into `rbx`.
2. **Pushing to the Stack:** 
   * `push rax` pushes `100` onto the stack.The 64-bit stack pointer (`RSP`) decrements by 8 bytes.
   * `push rbx` pushes `200` onto the stack.`RSP` decrements by another 8 bytes.
3. **Popping from the Stack:**
   * `pop rcx` pops the top value (`200`) off the stack and stores it in `rcx`.`RSP` increments by 8 bytes. 
   * `pop rdx` pops the next value (`100`) off the stack into `rdx`.`RSP` increments by another 8 bytes, returning to its original position.
4. **Program Exit:** The program prepares the `sys_exit` syscall (`rax = 60`) with an exit code of 0 (`xor rdi, rdi`), and terminates.

# Observations
When testing this in a debugger, I observed that values are not permanently tied to the registers that pushed them. Because the stack operates as LIFO, the last value pushed (`200` from `rbx`) is the first one popped. Consequently, `rcx` ends up with the value `200`, and `rdx` ends up with `100`.