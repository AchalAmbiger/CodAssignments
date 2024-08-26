# Program 1: 
### Statement: to write assembly code for the following c code

### Observation - Single Cycle
-created a array of 11 halfwords whose address are loaded into x10 register
-their values are loaded into register x10 then each element of the array is added to h which gets updated after every iteration
-the final value of h is stored into a[11] which is the register x12
 
### Register Mapping:
-x2:0x00000000
-x3:0x00001234
-x4:0x00005678
-x5:0x00001111
-x6:0x00002222
-x7:0x00003333
-x8:0x00004444
-x9:0x00005050
-x10:0x00000101
-x11:0x00007089
-x12:0001f651
- x10: 0x10000000

### Data Mapping
-0x00000038 : 0x003686b3
0x00000034:0x000106b3
0x00000030 :0x01451603
0x0000002c :0x01251583
0x00000028 :0x01051703
0x00000024  :0x00e51483
0x00000020  :0x00e51483
0x0000001c  :0x00a51383
0x00000018  :0x00851303
0x00000014  :0x00651283
0x00000010  :0x00451203
0x0000000c  :0x00251183
0x00000008  :0x00051103
0x00000004  :0x00051103
0x00000000  :0x10000517

...

# Program 2:
### Statement:2. Write an Assembly Program for addition of 2 64-bit numbers on RV32I  


### Observation - Single Cycle
-the 64 bit number is split into 32 bits, the LSB split is stored in a while the MSB split is present in b
-the LSB split of the numbers are loaded in register x10 while the MSB split is present in x11
-the LSB of the numbers is added and stored into x2, while the carry is present in x6
-similarly, the MSB of the numbers is added and present in x4 with the carry in x7
- the final sum is present in x8 = sum of MSB's + carry of the LSB's
 
### Register Mapping
- x2:0xfffffffe
-x3:0xFFFFFFFF
-x4:0xFFFFFFFE
-x5:0xFFFFFFFF
-x6:0x00000001
-x7:0x00000001
-x8:0xffffffff
- x10:0x10000000
-x11:0x10000000

### Data Mapping
-0x00000034 : 0x00000000
-0x00000030 : 0x00620433
-0x0000002c : 0x005233b3
-0x00000028 : 0x00520233
-0x00000024 : 0x00313333
-0x00000020 : 0x00310133
-0x0000001c : 0x0045a283
-0x00000018 : 0x0005a203
-0x00000014 : 0x00452183
-0x00000010 : 0x00052103
-0x0000000c : 0x00058593
-0x00000008:  0x10000597
-0x00000004 : 0x00050513
-0x00000000 : 0x10000517




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
