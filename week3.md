Assembly Code for Byte Extraction and Shifting
This assembly program performs byte-by-byte extraction from a 32-bit word stored in memory and shifts each byte left by a dynamic amount before adding it to an accumulator. The final result is stored back in memory.

Key Operations:

Loads a 32-bit word (0x12345678) into register x11
Extracts bytes using ANDI and shifts them left by a varying amount
Adds the shifted bytes to an accumulator (x17)
Loops through all 4 bytes
Stores the result back into memory after processing









.data 
a: .word 0x12345678
.text
la x10,a
lw x11,0(x10)
addi x13,x13,24
addi x20,x20,4

loop:

andi x14,x11,0xff
sll x16,x14,x13
add x17,x17,x16
srli x11,x11,8
addi x13,x13,-8
addi x20,x20,-1
bne x0,x20,loop

sw x17,4(x10)
