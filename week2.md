1)
.data
a: .dword 0xffffffffffffffff 0xffffffffffffffff
.text
la x10, a
lw x11, 0(x10) #1LSB
lw x12, 4(x10) #1MSB
lw x13, 8(x10) #2LSB
lw x14, 12(x10) #2MSB
add x15, x11, x13
sltu x16, x15, x13
add x17, x12, x14
sltu x18, x17, x13
add x17, x17, x16
sw x15,16(x10)
sw x17,20(x10)

2)
.data
a: .word 0x11111111 0x22222222 0x12354674 0x26483764 0x65749834
b: .word 0x23648276 0x83645273 0x83645263 0x97347262 0x82364372
c: .word 0,0,0,0,0
.text
la x10, a
la x11, b
la x12, c
lw x13, 0(x10)
lw x14, 0(x11)
add x15, x13, x14
sw x15, 0(x12) #first addition
lw x13, 4(x10)
lw x14, 4(x11)
add x15, x13, x14
sw x15, 4(x12) #second addition
lw x13, 8(x10)
lw x14, 8(x11)
add x15, x13, x14
sw x15, 8(x12) #third addition
lw x13, 12(x10)
lw x14, 12(x11)
add x15, x13, x14
sw x15, 12(x12) #fourth addition
lw x13, 16(x10)
lw x14, 16(x11)
add x15, x13, x14
sw x15, 16(x12) #fifth addition