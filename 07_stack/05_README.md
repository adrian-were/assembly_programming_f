# 05.asm 

## Stack Execution Flow
This program utilizes the stack's LIFO (Last-In-First-Out) architecture to effortlessly swap the values stored in two 64-bit registers without needing a temporary third register.

1. **Initialization:** At `_start`, `rax` is loaded with `0x1122334455667788`, and `rbx` is loaded with `0x1234`.
2. **Pushing Data:** 
   * `push rax` places `0x1122334455667788` onto the stack. `RSP` decrements by 8.
   * `push rbx` places `0x1234` onto the top of the stack[cite: 6]. `RSP` decrements by another 8.
3. **Popping Data in Reverse Order:**
   * `pop rbx` executes first.Because `0x1234` is at the top of the stack, it is popped right back into `rbx`. `RSP` increments by 8.
   * `pop rax` executes next.The original value of `rax` (`0x1122334455667788`) is now at the top of the stack, so it is popped back into `rax`. `RSP` increments by 8.
4. **Program Exit:** Standard 64-bit `sys_exit` is called (`rax = 60`).

# Observations
Because the popping order matches the original register sequence exactly (rather than being inversed like in `01.asm`), the values in the registers end up completely unchanged. The values are pushed `rax` then `rbx`, and then popped back into `rbx` then `rax`, restoring them to their initial states.