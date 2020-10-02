# ARM_Opcodes

Meaning | Mnemonic | Opcode | Status flags
-|-|-|-
Equal | EQ | 0 0 0 0 | Z=1
Not Equal | NE | 0 0 0 1 | Z=0
Carry Set | CS | 0 0 1 0 | C=1
Carry Clear | CC | 0 0 1 1 | C=0
Unsigned Higher or Same | HS | 0 0 1 0 | C=1
Unsigned Lower | LO | 0 0 1 1 | C=0
Minus/Negative | MI | 0 1 0 0 | N=1
Plus/Positive or Zero | PL | 0 1 0 1 | N=0
Overflow | VS | 0 1 1 0 | V=1
No Overflow | VC | 0 1 1 1 | V=0
Unsigned Higher | HI | 1 0 0 0 | C=1, Z=0
Unsigned Lower or Same | LS | 1 0 0 1 | C=0, Z=1
Signed Greater than or Equal | GE | 1 0 1 0 | N=V
Signed Less than | LT | 1 0 1 1 | N!=V
Signed Greater than | GT | 1 1 0 0 | Z=0, N=V
Signed Less than or Equal | LE | 1 1 0 1 | Z=1, N!=V
Always | AL | 1 1 1 0 | -
Never | NE | 1 1 1 1 | -
