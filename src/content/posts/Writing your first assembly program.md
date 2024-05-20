---
title: Writing your first assembly program
published: 2022-01-03
description: 'Learn how about assembly language and how to write a basic program in assembly'
image: ''
tags: ['assembly', 'reversing']
category: 'reverse-engineering'
draft: false 
---
Assembly is a low level programming language and is used to communicate directly with a computer hardware. Unlike machine language which consists of binary and hex characters, assembly language is readable by humans. 

Every computer has a microprocessor (like intel and amd) that manages all the arithemtical, logical and control activities. Each family of processor has its own set of instructions for managing different operations. These set of instructions are called 'machine language instructions'.

A processor understands only machine language instructions, which are strings of 1's and 0's. However, machine language is too complex for general development and other programming tasks. So, assembly language is designed for a specific family of processors that represents various instructions in symbolic code and a more understandable form.

In this blog we will talk about assembly language from a security researcher's perspective.

# WHY LEARN ASSEMBLY ?

- Unlike some skills in cybersecurity like network-security and web-app pentesting, assembly language knowledge is relatively rare. And hence if a company needs someone with knowledge of assembly the value will automatically get high (rarity = valuable).

- Essential for learning reverse engineering

- Essential for writing memory corruption and other low level exploits.

- Knowledge of assembly language is required for understanding the concept of computer architecture in detail.

- To become a good hacker you should know how systems work in detail and assembly language is essential for that.

There are various syntax assembly is written in which the instructions are same, the way the instructions are represented differ. For this blog we will be writing our program in intel x86 syntax.

# REGISTERS

Registers are the small storage areas in the processor. They are used to store memory address, values or anything that can be represented with 4 bytes *(4 Bytes = 32 Bits. A byte is 8 bits. It can store up to 28 (256) different values, or one character of ASCII text. A bit is the basic unit of information.)* or less.

In x86 Architecture there are 6 general purpose registers.

1. eax
2. ebx
3. ecx
4. edx
5. esi
6. edi

These registers are generally use as they are needed. There are 3 purpose that are reserved for specific purposes

1. ebp
2. esp
3. eip

# STACK
The stack is a data structure comprised of elements that are added or removed with operations- **push** or **pop** and **ret** .

push adds an element to the top of the stack & pop removes an element from the top of the stack.
The ret instruction transfers control to the return address located on the stack

Each element on a stack is assigned a stack address. Elements that are higher on the stack have lower address than those on the bottom of the stack. In other words stack grows towards lower memory address.

Whenever a function is called its setup with what we call a stack frame. All of the local variables of the function will be stored in that stack frame (which means each function has its own stack).

Lets talk about the two special purpose registers we mentioned earlier (esp, ebp). 

**ebp** (base pointer) → contains the address of the base of current stack frame.

**esp** (stack pointer) → contains the address of the top of current stack frame.

All the addresses outside of the current stack frame are called JUNK by the compiler.

The return address is outside of the stack frame. All th space b/w esp & ebp is considered the stack frame.

# HELLO WORLD IN ASSEMBLY
Although its not really necessary to learn how to write in assembly just understanding how to read it will be enough. But hey it won't hurt to do a little hello world program will it ?

```
BITS 32

extern printf

section .rodata
    hello_world: db "hello, world!", 10, 0

section .text
    global main

    main:
        push ebp
        mov ebp, esp

        push hello_world
        call printf
        add esp, 4

        mov eax, 0
        mov esp, ebp
        pop ebp
        ret
```
save this file as whatever file name you want but add .asm in last.
Now we will compile this file and run it. Before compiling there are some packages you need to install (i am using ubuntu, if you are using other operating system then you might have to look up these packages for your os.)

- nasm
- gcc
- gcc-multilib

```sh
sudo apt-get install nasm gcc gcc-multilib
```

Once the packages are installed, let's compile our program and run it.
```sh
nasm -f elf hello.asm
```
This will create an object file named `hello.o`. Now we will use gcc to create a .out file which is our final file that we will run.
```sh
gcc -m32 hello.o -o hello.out
```
Now execute the file and you'll get the output "hello, world!".
```sh
./hello.out
hello, world!
```

EOF