# 03.asm 

## Stack Execution Flow
This program demonstrates the stack's primary role in controlling program execution flow through `call` and `ret` instructions.

1. **Initialization:** The program starts by placing `10` into `rax`.
2. **Subroutine Call:** The `call calculate` instruction is executed.Under the hood, this pushes the memory address of the next instruction (labeled `after_call`) onto the stack. `RSP` decrements by 8 bytes. Execution jumps to the `calculate` label.
3. **Subroutine Execution:** Inside `calculate`, the program adds `5` to the existing value in `rax` (making it `15`).
4. **Returning to Caller:** The `ret` instruction is executed.It pops the top 8 bytes from the stack—which is the `after_call` return address saved earlier—into the Instruction Pointer (`RIP`). `RSP` increments by 8 bytes.
5. **Program Exit:** Execution resumes exactly at `after_call`, proceeding to cleanly exit the program via the `sys_exit` syscall.

# Observations
When stepping through this with a debugger, it is clear that `call` and `ret` are fundamentally just specialized `push` and `pop` operations targeting the instruction pointer. The stack acts as a breadcrumb trail allowing the program to "remember" where it left off.