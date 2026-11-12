# 04.asm

## Stack Execution Flow
This program sets up a stack frame identical to `02.asm`, but utilizes 32-bit architecture and registers.

1. **Function Call:** Execution starts at `_start` with `call work`, pushing a 32-bit return address onto the stack and decrementing the Stack Pointer (`ESP`) by 4 bytes.
2. **Function Prologue:** Inside the `work` routine, `push ebp` saves the base pointer (decrementing `ESP` by 4).`mov ebp, esp` creates the new stack frame.
3. **Local Variables Allocation:** `sub esp, 8` allocates 8 bytes on the stack for local variable storage.
4. **Data Storage and Retrieval:** The program stores `100` at `[ebp - 4]` and `200` at `[ebp - 8]` using 32-bit data size (`dword`)[cite: 5]. These values are then loaded into `eax` and `ebx`, respectively.
5. **Function Epilogue:** The local space is deallocated via `mov esp, ebp`, and the caller's base pointer is restored with `pop ebp`.
6. **Return:** The `ret` instruction pops the return address into the Instruction Pointer (`EIP`), and the program uses the Linux i386 exit syscall (`int 0x80` with `eax = 1`) to terminate.

# Observations
The exact same logic governs stack frames in both 32-bit and 64-bit mode. The primary operational difference observed is the offset scale: pushes, pops, and address offsets shift by 4 bytes at a time (due to `ESP`/`EBP`) rather than the 8 bytes seen with `RSP`/`RBP`.