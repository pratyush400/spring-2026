# Note 21

Adapted from *Dive Into Systems*, *Computer Systems: A Programmer's Perspective,
3rd Edition*, and the *Intel® 64 and IA-32 Architectures Software Developer’s
Manual*.

## Setting condition code

### Explicit setting

Instruction     | Computation
-|-
`cmpq` S1, S2   | S2 − S1
`testq1` S1, S2 | S2 & S1

The instructions `cmpq s, d` and `testq s, d` perform all the same actions as
`subq s, d` and `andq s, d`, respectively, exception for updating the
destination.

## Using condition code

### Jumping

Signed comparison | Unsigned comparison | Description
-|-|-
`je` (`jz`)       |                     | jump if equal (jump if zero)
`jne` (`jnz`)     |                     | jump if not equal (jump if not zero)
`js`              |                     | jump if negative
`jns`             |                     | jump if non-negative
`jg` (`jnle`)     | `ja` (`jnbe`)       | jump if greater
`jge` (`jnl`)     | `jae` (`jnb`)       | jump if greater or equal
`jl` (`jnge`)     | `jb` (`jnae`)       | jump if less
`jle` (`jng`)     | `jbe` (`jna`)       | jump if less or equal
