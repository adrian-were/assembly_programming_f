# 02.asm

## Stack Execution Flow
This program demonstrates how the stack is used to manage function calls, create stack frames, and store local variables in 64-bit architecture.

1. **Function Call:** Execution starts at `_start` with `call work`.This instruction pushes the return address (the address of the subsequent `mov rax, 60` instruction) onto the stack and decrements `RSP` by 8 bytes.
2. **Function Prologue:** Inside `work`, `push rbp` saves the caller's base pointer onto the stack (`RSP` - 8).`mov rbp, rsp` establishes a new stack frame for this function, anchoring `RBP` to the current `RSP`.
3. **Local Variables Allocation:** `sub rsp, 16` allocates 16 bytes of space on the stack for local variables. 
4. **Data Storage and Retrieval:** 
   * The program stores `100` at `[rbp - 8]` and `200` at `[rbp - 16]`.
   * It immediately reads these values back, loading `100` into `rax` and `200` into `rbx`.
5. **Function Epilogue:** 
   * `mov rsp, rbp` deallocates the local variables by moving the stack pointer back to the base pointer[cite: 3].
   * `pop rbp` restores the original caller's base pointer and increments `RSP` by 8.
6. **Return:** `ret` pops the return address off the stack into the instruction pointer (`RIP`), returning control to `_start` to execute the `sys_exit` syscall.

# Observations
By using `rbp` as a fixed reference point, the program easily accesses local variables regardless of how much data is subsequently pushed onto the stack. The stack frame effectively isolates the `work` function's operations from the `_start` execution environment.