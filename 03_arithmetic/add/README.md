Add Operations Flags Analysis

## add1.asm (120 + 10 = 130)
**Operation:** `add al, [num2]` (8-bit addition)
**Binary result:** `10000010` (130 in unsigned, -126 in signed)

`Carry Flag (CF) - Cleared (0):` There was no carry out of the most significant bit because 130 does not exceed the 8-bit unsigned maximum of 255.
`Overflow Flag (OF) - Set (1):` Adding two positive numbers (120 and 10) resulted in a negative number in signed representation (-126), exceeding the 8-bit signed maximum of 127.
`Sign Flag (SF) - Set (1):` The most significant bit of the binary result (`10000010`) is 1, indicating a negative value.
`Zero Flag (ZF) - Cleared (0):` The final result is 130, not zero.

## add2.asm (32000 + 500 = 32500)
**Operation:** `add ax, [num2]` (16-bit addition)
**Binary result:** `01111110 11110100` (32500)

`Carry Flag (CF) - Cleared (0):` There was no carry out of the most significant bit because 32500 does not exceed the 16-bit unsigned maximum of 65,535.
`Overflow Flag (OF) - Cleared (0):` The result comfortably fits within the 16-bit signed maximum of 32,767, so no signed overflow occurred.
`Sign Flag (SF) - Cleared (0):` The most significant bit of the binary result is 0, indicating a positive value.
`Zero Flag (ZF) - Cleared (0):` The final result is 32,500, not zero.