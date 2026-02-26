# Note 16

Adapted from *Computer Systems: A Programmer's Perspective, 3rd Edition* and
the *Intel® 64 and IA-32 Architectures Software Developer’s Manual*.

## Sizes of common C data types

C declaration | Intel data type | GCC assembly suffix | Size (bytes)
-|-|-|-
`char`        | Byte            | b                   | 1
`short`       | Word            | w                   | 2
`int`         | Doubleword      | l                   | 4
`long`        | Quadword        | q                   | 8
`void *`      | Quadword        | q                   | 8

## Simple move instructions

Instruction            | Effect           | Name
-|-|-
`movb` *src*, *dst*    | *dst* `<-` *src* | move byte
`movw` *src*, *dst*    | *dst* `<-` *src* | move word
`movl` *src*, *dst*    | *dst* `<-` *src* | move doubleword
`movq` *src*, *dst*    | *dst* `<-` *src* | move quadword
`movabsq` *imm*, *reg* | *reg* `<-` *imm* | move absolute quad word

Notes:
* Operands *src* and *dst* cannot be both memory
* Only the specific bytes are updated
  * Exception: `movl` with a register as a destination: high-order bits are set
    to 0
* `movq`: Immediate operand only up to 32 bits
* `movabsq`: source is always a 64-bit immediate and destination is always a
             register

## Common C patterns

C | Assemly
-|-
`i = 42`  | `movl  $42, %ebp`
`*p = 42` | `movl $42, (%rax)`
`i = j`   | `movl %esp, %ebp`
`*p = i`  | `movl %ebp, (%rax)`
`j = *p`  | `movl (%rax), %esp`
`q = 0xfdecba9876543210` | `movabsq $0xfdecba9876543210, %rbx`
