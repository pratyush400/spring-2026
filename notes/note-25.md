# Note 25

Adapted from *Dive Into Systems*.

## Arrays

Operation        | Type    | Assembly
-|-|-
`x = arr`        | `int *` | `mov %rdx, %rax`
`x = arr[0]`     | `int`   | `mov (%rdx), %eax`
`x = arr[i]`     | `int`   | `mov (%rdx, %rcx, 4), %eax`
`x = &arr[3]`    | `int *` | `lea 0xc(%rdx), %rax`
`x = arr + 3`    | `int *` | `lea 0xc(%rdx), %rax`
`x = *(arr + 5)` | `int`   | `mov 0x14(%rdx), %eax`

## Structs

In the 64-bit x86 assembly, the compiler is likely using the *base* plus
*displacement* memory specifier (`Imm(reg)`) for translating accesses to members
of a struct.

### Alignment

The 64-bit x86 assembly strongly suggests that certain data types reside at an
address that is a multiple of their size. Values properly aligned in memory can
then be read or written with greater efficiency.
