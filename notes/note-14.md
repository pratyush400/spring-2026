# Note 14

## Little endian, big endian

The byte order (or endianness) of a system defines how its hardware assigns the
bytes of a multibyte variable to consecutive memory addresses. Byte order is
[rarely an issue](https://commandcenter.blogspot.com/2012/04/byte-order-fallacy.html)
for programs.

## Processor state

Important components of processor state include:

* *Program counter (PC) or instruction pointer (IP)*. It points to an address in
  memory containing the next instruction to execute.

* *Integer register file*. A collection of 16 registers that can hold integer
   data or addresses (our C pointers).

* *Condition code*. A collection of bits reflecting the status of recent
  arithmetic or logical instructions.
