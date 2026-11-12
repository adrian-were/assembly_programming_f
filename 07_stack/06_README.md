# 06.asm

## Stack Execution Flow
This program is the 32-bit equivalent of `05.asm`, demonstrating how the stack's LIFO property can be used to swap 32-bit register values.

1. **Initialization:** `eax` is loaded with the 32-bit hex value `0x11223344`, and `ebx` is loaded with `0x1234`.
2. **Pushing Data:**
   * `push eax` places `0x11223344` onto the stack, subtracting 4 from `ESP`.
   * `push ebx` places `0x1234` onto the stack, subtracting another 4 from `ESP`.
3. **Popping Data in Reverse Order:**
   * `pop ebx` pulls the top of the stack (`0x1234`) and stores it back into `ebx`. `ESP` increments by 4.
   * `pop eax` pulls the next value (`0x11223344`) and stores it back into `eax`. `ESP` increments by 4.
4. **Program Exit:** The i386 Linux `sys_exit` is triggered using `int 0x80` (`eax = 1`).

# Observations
Just like the 64-bit counterpart, because the programmer popped into `ebx` first and `eax` second, the data was restored to its exact original location. The stack operated perfectly to "store and restore" state, leaving `eax` and `ebx` exactly as they were before the stack operations began.