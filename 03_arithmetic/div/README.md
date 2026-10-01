# Division Operations Flags Analysis

## div1.asm (100 / 7)
**Operation:** `div bl` (8-bit unsigned division)
**Mathematical Result:** Quotient = 14 (stored in `al`), Remainder = 2 (stored in `ah`)

`Carry Flag (CF) - Undefined:` - The `div` instruction leaves this flag in an undefined state.
`Overflow Flag (OF) - Undefined:` - The `div` instruction leaves this flag in an undefined state. A division error (like divide-by-zero or a quotient too large for the target register) would trigger a hardware exception (Interrupt 0), not an overflow flag.
`Sign Flag (SF) - Undefined:` - The `div` instruction leaves this flag in an undefined state.
`Zero Flag (ZF) - Undefined:` -  The `div` instruction leaves this flag in an undefined state, even if the resulting quotient is zero.

## div2.asm (50000 / 300)
**Operation:** `div bx` (16-bit unsigned division)[cite: 6]
**Mathematical Result:** Quotient = 166 (stored in `ax`)[cite: 6], Remainder = 200 (stored in `dx`)

`Carry Flag (CF) - Undefined:` - Instruction does not set the carry flag to reflect the remainder or borrowing. 
`Overflow Flag (OF) - Undefined:` - The quotient 166 easily fits within the 16-bit `ax` register.
`Sign Flag (SF) - Undefined:` -  The `div` instruction leaves this flag undefined.
`Zero Flag (ZF) - Undefined:` - The `div` instruction leaves this flag undefined.