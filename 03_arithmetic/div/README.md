# Division Operations Flags Analysis

## div1.asm (100 / 7)
**Operation:** `div bl` (8-bit unsigned division)
**Mathematical Result:** Quotient = 14 (stored in `al`), Remainder = 2 (stored in `ah`)

`Carry Flag (CF) - Undefined:` - There is no carry out from the most significant bit.
`Overflow Flag (OF) - Undefined:` - The quotient 14 fits safely within the 8-bit signed capacity (-128 to 127), meaning no overflow occurred.
`Sign Flag (SF) - Undefined:` - The most significant bit (leftmost bit) of the binary result `00001110` is 0, a positive number.
`Zero Flag (ZF) - Undefined:` -  The final quotient is 14, not zero.

## div2.asm (50000 / 300)
**Operation:** `div bx` (16-bit unsigned division)[cite: 6]
**Mathematical Result:** Quotient = 166 (stored in `ax`)[cite: 6], Remainder = 200 (stored in `dx`)

`Carry Flag (CF) - Undefined:` - Instruction does not set the carry flag to reflect the remainder or borrowing. 
`Overflow Flag (OF) - Undefined:` - The quotient 166 easily fits within the 16-bit `ax` register.
`Sign Flag (SF) - Undefined:` -  The most significant bit of the 16-bit binary quotient `00000000 10100110` is 0, a positive number.
`Zero Flag (ZF) - Undefined:` - The final quotient is 166, not zero.