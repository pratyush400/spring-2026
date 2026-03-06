# Note 20

Adapted from *Computer Systems: A Programmer's Perspective, 3rd Edition* and
the *Intel® 64 and IA-32 Architectures Software Developer’s Manual*.

## Condition code

I mentioned, in [Note 14](./note-14.md), that processor state includes
*condition code* flags. These flags are held in a register called RFLAG. The
important flags are as follows:

Name        | Description
-|-
CF (bit 0)  | Set if result produced a carry out of the most-significant bit
PF (bit 2)  | Set if least-significant byte contains an even number of bits
ZF (bit 6)  | Set if result is zero
SF (bit 7)  | Equal to the most-significant bit of the result
OF (bit 11) | Set to indicate overflow condition in signed-integer arithmetic

## Setting condition code

### Implicit setting

Condition code flags are implicitly set by *most* arithmetic operations. Note
that the *leaq* instruction does *not* change the condition code flags.
