Multiplication Operations Flags Analysis

## mul1.asm (25 * 10 = 250)
**Operation:** `mul byte [num2]` (8-bit unsigned multiplication)
**Result:** 250 (stored in the 16-bit `ax` register). The lower half `al` holds 250, and the upper half `ah` holds 0.

*   **Carry Flag (CF) - Cleared (0):** The upper half of the result (`ah`) is zero[cite: 10]. The entire result (250) fits within the lower 8-bit register (`al`), so no significant bits spilled over.
*   **Overflow Flag (OF) - Cleared (0):** Cleared for the same reason as the Carry Flag; the upper half of the result (`ah`) is zero.
*   **Sign Flag (SF) - Undefined:** The x86 `mul` instruction leaves this flag undefined, meaning its value cannot be reliably used.
*   **Zero Flag (ZF) - Undefined:** The x86 `mul` instruction leaves this flag undefined.

## mul2.asm (3000 * 200 = 600,000)
**Operation:** `mul word [num2]` (16-bit unsigned multiplication)
**Result:** 600,000 (stored across the 32-bit `DX:AX` register pair). 

*   **Carry Flag (CF) - Set (1):** The upper half of the result (`dx`) is non-zero[cite: 10]. The total value (600,000) exceeds the 16-bit maximum (65,535), causing the significant bits to spill into the `dx` register.
*   **Overflow Flag (OF) - Set (1):** Set for the same reason as the Carry Flag; the upper 16 bits (`dx`) contain significant, non-zero data.
*   **Sign Flag (SF) - Undefined:** The x86 `mul` instruction leaves this flag undefined.
*   **Zero Flag (ZF) - Undefined:** The x86 `mul` instruction leaves this flag undefined.