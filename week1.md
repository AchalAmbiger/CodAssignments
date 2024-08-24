1)Adding two words using different datatypes
.data
a: .word 0x00000001,0x12345678
.text
la x10,a
lw x11,0(x10)
lw x12,4(x10)
add x13,x11,x12
sw x13,8(x10)


2)write a program to add -3 with +1 using RV32I.Assume the number to be 8 byte sign numbers.
.data
a: .byte -3,1
.text
la x10,a
lw x11,0(x10)
lw x12,1(x10)
add x13,x11,x12
sw x13,2(x10)


3)copy 8 bit sign number into 32 bit register
(sign extension)
.data
a: .byte -3,1
.text
la x10,a
lb x11,0(x10)
lb x12,1(x10)
add x13,x11,x12
sb x13,2(x10)


4)write a program to addd two unsigned 8 bit numbers. the numbers given are 0xFD, 0x01

5)write a program to add two 32 bit numbers .numbers given are 0x80000002 ,0x9123456A.these are unsigned numbers.data
a: .word 0x80000002,0x9123456A
.text
la x10,a
lw x11,0(x10)
lw x12,4(x10)
add x13,x11,x12
sw x13,8(x10)

