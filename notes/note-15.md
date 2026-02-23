# Note 15

Adapted from *Computer Systems: A Programmer's Perspective, 3rd Edition* and
the *Intel® 64 and IA-32 Architectures Software Developer’s Manual*

## Integer register file

The integer register file consists of 16 general-purpose registers (see below).
These registers can operate on data of different sizes. The name of the register
varies depending on the size of the data they hold.

```
   6          5         4         3         2         1  
 3210987654321098765432109876543210987654321098765432109876543210
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
| %rax                          | %eax          | %ax   | %al   |
| %rbx                          | %ebx          | %bx   | %bl   | 
| %rcx                          | %ecx          | %cx   | %cl   |
| %rdx                          | %edx          | %dx   | %dl   |
| %rdi                          | %edi          | %di   | %dil  |
| %rsi                          | %esi          | %si   | %sil  |
| %rsp                          | %esp          | %sp   | %spl  |
| %rbp                          | %ebp          | %bp   | %bpl  |
| %r8                           | %r8d          | %r8w  | %r8b  |
| %r9                           | %r9d          | %r9w  | %r9b  |
| %r10                          | %r10d         | %r10w | %r10b |
| %r11                          | %r11d         | %r11w | %r11b |
| %r12                          | %r12d         | %r12w | %r12b |
| %r13                          | %r13d         | %r13w | %r13b |
| %r14                          | %r14d         | %r14w | %r14b |
| %r15                          | %r15d         | %r15w | %r15b |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
```

## Operand specifiers

The source of an operand can be:

* The instruction itself (immediate)
* A register
* Memory

The destination for the result of a computation can be:

* A register
* Memory

The table below summarizes all operand forms supported by the x86-64 instruction 
set architecture.

Type      | Form               | Operand value
-|-|-
Immediate | $\$Imm$            | *Imm*
Register  | $r_b$              | $R[r_b]$
Memory    | $Imm$              | $M[Imm]$
Memory    | $(r_b)$            | $M[R[r_b]]$
Memory    | $Imm(r_b)$         | $M[Imm + R[r_b]]$
Memory    | $(r_b, r_i)$       | $M[R[r_b] + R[r_i]]$
Memory    | $Imm(r_b, r_i)$    | $M[Imm + R[r_b] + R[r_i]]$
Memory    | $(, r_i, s)$       | $M[R[r_i] \times s]$
Memory    | $Imm(, r_i, s)$    | $M[Imm + R[r_i] \times s]$
Memory    | $(r_b, r_i, s)$    | $M[R[r_b] + R[r_i] \times s]$
Memory    | $Imm(r_b, r_i, s)$ | $M[Imm + R[r_b] + R[r_i] \times s]$

where

* $r$ is a register identifier (e.g., `%rax`)
* $R[r]$ is the content of register $r$
* $M[a]$ is the content of memory at address $a$
