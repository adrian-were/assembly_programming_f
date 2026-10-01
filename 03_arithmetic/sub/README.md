# Subtraction Operations Flags Analysis

## sub1.asm (50 - 80 = -30)
**Operation:** `sub al, [num2]` (8-bit subtraction)
**Result:** -30 (signed), represented as `11100010` in binary (or 226 unsigned).

*   **Carry Flag (CF) - Set (1):** Subtracting a larger unsigned number (80) from a smaller one (50) requires a borrow out of the most significant bit.
*   **Overflow Flag (OF) - Cleared (0):** The signed result of -30 easily fits within the 8-bit signed range (-128 to +127), so no signed overflow occurred.
*   **Sign Flag (SF) - Set (1):** The result is a negative number, meaning the most significant bit is 1.
*   **Zero Flag (ZF) - Cleared (0):** The result is -30, which is not zero.

## sub2.asm (1000 - 2000 = -1000)
**Operation:** `sub ax, [num2]` (16-bit subtraction)
**Result:** -1000 (signed), represented as `11111100 00011000` in binary (or 64,536 unsigned).

*   **Carry Flag (CF) - Set (1):** Subtracting a larger unsigned value (2000) from a smaller one (1000) requires a borrow.
*   **Overflow Flag (OF) - Cleared (0):** The signed result of -1000 fits perfectly within the 16-bit signed range (-32,768 to 32,767), so no overflow occurred.
*   **Sign Flag (SF) - Set (1):** The result is negative, causing the 16th bit (most significant bit) to be set to 1.
*   **Zero Flag (ZF) - Cleared (0):** The final mathematical result is not zero.