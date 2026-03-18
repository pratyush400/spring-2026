# Note 25

## Structs

In the 64-bit x86 assembly, the compiler is likely using the *base* plus
*displacement* memory specifier (`Imm(reg)`) for translating accesses to members
of a struct.

### Alignment

The 64-bit x86 assembly strongly suggests that certain data types reside at an
address that is a multiple of their size. Values properly aligned in memory can
then be read or written with greater efficiency.
