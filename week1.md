
1)
.data
a: .word 0x00000001,0x12345678
.text
la x10,a
lw x11,0(x10)
lw x12,4(x10)
add x13,x11,x12
sw x13,8(x10)


2)
.data
a: .byte -3,1
.text
la x10,a
lw x11,0(x10)
lw x12,1(x10)
add x13,x11,x12
sw x13,2(x10)


3)
(sign extension)
.data
a: .byte -3,1
.text
la x10,a
lb x11,0(x10)
lb x12,1(x10)
add x13,x11,x12
sb x13,2(x10)


4)

5)
a: .word 0x80000002,0x9123456A
.text
la x10,a
lw x11,0(x10)
lw x12,4(x10)
add x13,x11,x12
sw x13,8(x10)

