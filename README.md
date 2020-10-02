Mnemonic | Description and examples
---------|----------
ADD | Add
 | | ADD R3, R2, R3 = 03 30 82 E0
 | | ADD R2, R2, #1 = 01 20 82 E2
 | | ADD R1, R1, #4 = 04 10 81 E2
 | | ADD SP, SP, #4 = 04 D0 8D E2
AND | Logical AND
 | | AND R10, R9, R10     = 0A A0 09 E0
 | | AND R10, R4, R10     = 0A A0 04 E0
 | | AND R11, R11, #0xF8  = F8 B0 0B E2
 | | ANDS R3, R10, #0xFF  = FF 30 1A E2
 | | ANDS R3, R0, #0xFF   = FF 30 10 E2
B | Branch
 | | B   = xx xx xx EA (branch)
 | | BEQ = xx xx xx 0A (if zero, Z)
 | | BNE = xx xx xx 1A (if not equal, -Z)
 | | BGE = xx xx xx AA (if greater or equal, N*V/-N*-V)
 | | BHI = xx xx xx 8A (if higher, -C*-Z)
 | | BLT = xx xx xx BA (if less than, N*-V/-N*V)
 | | BCC = xx xx xx 3A (if carry clear)
 | | BCS = xx xx xx 2A (if carry set)
 | | BPL = xx xx xx 5A
 | | BMI = xx xx xx 4A (if negative, set N)
 | | BLS = xx xx xx 9A (if lower or same, C/Z)
 | | BGT = xx xx xx CA (if greater than, N*V*-Z/-N*-V*-Z)
 | | BLE = xx xx xx DA (if less or equal, Z/N*-V/-N*V)
 | | Examples:
 | | 00022714 B   loc_22734 = 06 00 00 EA (h34-h14=h20, minus pipeline length: h20-h8=h18, right shift 2 bits: h18/4=h6)(*)
 | | 000226B8 BLE loc_226E4 = 09 00 00 DA (hE4-hB8=h2C, minus pipeline length: h2C-h8=h24, right shift 2 bits: h24/4=h9)(*)
 | | * The offset for branch instructions is calculated by the assembler:
 | | - By taking the difference between the branch instruction and the target address minus 8 (to allow for the pipeline).
 | | - This gives a 26 bit offset which is right shifted 2 bits (as the bottom two bits are always zero as instructions are word aligned) and stored into the instruction encoding.
BIC | Bit Clear
BL | Branch and Link
 | | BL   = xx xx 00 EB
 | | BLEQ = xx xx 00 0B
BX | Branch and Exchange
CDP | Coprocessor Data Processing
CMN | Compare Negative
CMP | Compare
 | | CMP (reg, reg) = xx xx 5X E1
 | | CMP R0, R3     = 03 00 50 E1
 | | CMP (reg, val) = 00 00 53 E3
 | | CMP R0, #0     = 00 00 50 E3
 | | CMP R5, #0     = 00 00 55 E3
 | | CMPEQ R3, #1   = 01 00 53 03
EOR | Logical Exclusive OR (XOR)
LDC | Load Coprocessor
LDM | Load Multiple
LDR | Load Register
 | | LDR R0, [R1, #0x38]   = 38 00 91 E5
 | | LDR R0, [R5]          = 00 00 95 E5
 | | LDR R2, [R3]          = 00 20 93 E5
 | | LDR R1, [R6]          = 00 10 96 E5
 | | LDREQ R3, [R7, #0x10] = 10 30 97 05
 | | LDREQ R0, [R3, #0x8]  = 08 00 93 05
 | | 
LDRB | Load Register Byte
 | | LDRB R2, [R0, #2] = 02 20 D0 E5
LDRBT | Load Register Byte Translate
LDRH | Load Register Half Word
LDRSB | Load Register Signed Byte
 | | LDRSB R3, [SP, #2] = D2 30 DD E1
LDRSH | Load Register Signed Half Word
 | | LDRSH R1, [R6, #0x54] = F4 15 D6 E1
 | | LDRSH R1, [R6, #0x56] = F6 15 D6 E1
LDRT | Load Register Translate
MCR | Move to Coprocessor from ARM reg
MLA | Multiply Accumulate
MOV | Move
 | | MOV (reg, reg)     = xx xx A0 E1
 | | MOV (reg, value)   = xx xx A0 E3
 | | MOVEQ (reg, reg)   = xx xx A0 01
 | | MOVNE (reg, reg)   = xx xx A0 11
 | | MOVEQ (reg, value) = xx xx A0 03
 | | MOVNE (reg, value) = xx xx A0 13
 | | MOVGE (reg, value) = xx xx A0 A3
 | | MOVHI (reg, value) = xx xx A0 83
 | | Examples:
 | | MOV R0, #1            = 01 00 A0 E3
 | | MOV R1, #0            = 00 10 A0 E3
 | | MOV R4, R0            = 00 40 A0 E1
 | | MOV R7, R1            = 01 70 A0 E1
 | | MOV R3, R0, LSL#16    = 00 38 A0 E1
 | | MOV R3, R3, LSR#16    = 23 38 A0 E1
 | | MOVS R10, R11, ASR#31 = CB AF B0 E1
 | | MOVS R11, R1, ASR#31  = C1 BF B0 E1
 | | MOVEQ R5, #0          = 00 50 A0 03
 | | MOV R0, #0x7F00       = 7F 0C A0 E3 (0C: 0-> R0, C -> mC = h100, h7F x h100 = h7F00)(*)
 | | MOV R3, #0x9C00       = 27 3B A0 E3 (3B: 3-> R3, B -> mB = h400, h27 x h4   = h9C00)(*)
 | | * where value = first 2 bytes * mX (x = Byte 4)
 | | m1 := $40000000;
 | | m2 := $10000000;
 | | m3 := $4000000;
 | | m4 := $1000000;
 | | m5 := $400000;
 | | m6 := $100000;
 | | m7 := $40000;
 | | m8 := $10000;
 | | m9 := $4000;
 | | mA := $1000;
 | | mB := $400;
 | | mC := $100;
 | | mD := $40;
 | | mE := $10;
 | | mF := $4;
 | | 
MRC | Move to ARM reg from Coprocessor
MRS | Move from Status Register
MSR | Move to Status Register
MUL | Multiply
 | | MUL R11, R2, R4 = 92 04 0B E0
 | | MUL R9, R11, R3 = 9B 03 09 E0
 | | MUL R0, R2, R0  = 92 00 00 E0
MVN | Move Negative
NOP | Not a real ARM mnemonic, but effectively equivalent to a NOP
 | | MOV R0, R0 = 00 00 A0 E1 (copy value of R0 into itself, safe)
 | | Thumb: MOV R8, R8 = 46 C0 (MOV R0, R0 would affect the flags)
ORR | Logical OR
 | | ORR R3, R3, #0xC       = 0C 30 83 E3
 | | ORR R3, R3, #0x3C      = 3C 30 83 E3
 | | ORRS R1, R1, #0×80     = 80 10 91 E3
 | | ORRS R3, R2, R3, LSL#8 = 03 34 92 E1
 | | ORRS R5, R2, R3, LSL#8 = 03 54 92 E1
RET | Return
 | | RET = 0E F0 A0 E1
RSB | Reverse Subtract
 | | RSBMI R10, R1, #0 = 00 A0 61 42
 | | RSBGT R6, R1, R4  = 04 60 61 C0
 | | RSBMI R4, R2, #0  = 00 40 62 42
RSC | Reverse Subtract with Carry
SBC | Subtract with Carry
SMLAL | Signed Long Multiply Accumulate
SMULL | Signed Long Multiply
STC | Store Coprocessor
STM | Store Multiple
STR | Store Register
 | | STR R0, [R7] = 00 00 87 E5
STRB | Store Register Byte
 | | STRB R1, [R0, R3]  = 03 10 C0 E7
 | | STRB R11, [LR]     = 00 B0 CE E5
 | | STRB R11, [LR, #1] = 01 B0 CE E5
STRBT | Store Register Byte Translate
STRH | Store Register Half Word
 | | STRH R3, [R4,#0xC] = BC 30 C4 E1
 | | STRH R3, [R4,#0xE] = BE 30 C4 E1
 | | STRH R3, [R1]      = B0 30 C1 E1
STRT | Store Register Translate
SUB | Subtract
 | | SUB SP, SP, #0×38 = 38 D0 4D E2
 | | SUB R3, R11, R0   = 00 30 4B E0
SWI | Software Interrupt
SWP | Swap
SWPB | Swap Byte
TEQ | Test Equivalence
TST | Test
UMLAL | Unsigned Long Multiply Accumulate
UMULL | Unsigned Long Multiply

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
