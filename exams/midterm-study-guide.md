# Midterm Study Guide

## C programming language

* Phases of compilation
  * Preprocessing (`cpp`, `.c -> .i`)
  * Compilation (`cc1`, `.i -> .s`)
  * Assembly (`as`, `.s -> .o`)
  * Linkage (`ld`, `.o -> exe`)
* Regions of memory
  * Text (the instructions)
  * Stack (manage function calls and returns)
  * Heap (`malloc`, `free`)
* Data types
  * Integers
    * Signed (`char`, `short`, `int`, `long`)
      * Unsigned (add prefix `unsigned`)
      * Sizes on our machines: 1, 2, 4, and 8 bytes (respectively)
    * Operators
      * Addition, subtraction, multiplication, division, remainder
      * Shift left (`<<`, multiply by a power of 2)
      * Shift right (`>>`, divide by a power of 2)
      * Bitwise operators
        * Not (`~`)
        * And (`&`)
        * Or (`|`)
        * Exclusive or (`^`)
  * No boolean types
    * Instead use `int`
    * Generous in accepting a true value (any value other than 0)
    * Specific in generating a true value (only 1)
    * Operators (`!`, `&&`, `!!`)
      * `&&` and `!!` use short-cicuit evaluation
  * Approximation of numbers on the real line
    * `float`, `double`
    * Sizes: 4 bytes, 8 bytes
  * Arrays
    * `<base type> <var>[]`
    * E.g., `int v[10]`, `int a[10][10]`
  * Pointers
    * Declaration (`<base type> *<ptr>`, e.g., `int *p`)
    * Generate an address (`&<name>`)
    * Dereference (`*<ptr>`)
  * Compound
    * `struct <name> { <type> <fname>; <type> <fname>; ... };`
    * Access through a variable: `<var>.<fname>`
    * Access through a pointer: `<ptr>-><fname>`
* Memory management
  * Allocation: typically `malloc`
  * Deallocation: typically `free`
  * Problems
    * Leaks (not calling `free` soon enough)
    * Stray memory writes with invalid pointer (e.g., calling `free` too soon)
    * Double `free`

## Data representation

* Byte order
  * Big endian
  * Little endian
* Characters
  * ASCII code (7 bits stored in a `char`)
  * Unicode (1 to 4 bytes encoding)
* Integers
  * Binary encodings
    * Precise but limited range
    * Least value (`0`)
    * Greatest value ($2^n - 1$ where $n$ is the width of the word)
    * Conversions
      * Decimal to binary
      * Binary to decimal
      * Decimal to hexadecimal
      * Hexadecimal to binary
  * Negative numbers
    * Precise but limited range
    * Strategies
      * Sign & magnitude
      * Bias (used to store the exponent part of a floating point number)
      * One's complement (`~`)
      * Two's complement (used for integer types on most machines)
    * Number of representations of 0
      * Bias, two's complement: 1
      * Sign & magnitude, one's complement: 2
    * Smallest and largest values
* Numbers on the real line
  * Approximation, but large range (including positive and negative infinity)
  * IEEE 754 standard
    * Central idea: store number in normalized scientific notation using base 2
    * `float`: 32-bit IEEE format
    * `double`: 64-bit IEEE format
    * 3 fields (sign bit (n), exponent bits (e), significand bits (s))
    * Interpretation (for 32-bit)
      * Normalized: −1^n * 2^(e-127) * 1.s
      * Denormalized (e = 0): −1^n * 2^−126 * 0.s
      * Special values (e = 255)
        * Infinities (s = 0)
        * Not a Number (s ≠ 0)
    * Conversion to and from integers
      * Changes the encoding!
      * Not always precise
    * Extremes
      * Smallest positive normalized number
      * Largest positive normalized number
      * Smallest non-zero positive denormalized number
      * Largest positive denormalized number

## 64-bit x86 assembly

* Processor state
  * Instruction pointer (`%rip`)
  * Register file
  * Memory
* Register file
  * 16 64-bit registers
  * Can be accessed as
    * 64-bit values (`%rax`, `%rbx`, ...)
    * 32-bit values (`%eax`, `%ebx`, ...)
    * 16-bit values (`%ax`, `%bx`, ...)
    * 8-bit values (`%al`, `%bl`, ...)
* Operand specifiers
  * Immediate (value encoded in the instruction)
    * `$Imm`
  * Register (value stored in a register)
    * `%reg`
  * Memory (value stored in memory)
    * `Imm(%r1, %r2, s)`
    * Operand stored at address `Imm + R[%r1] + R[%r2]*s`
      * `s` can only be 1, 2, 4, or 8
      * If `s` is omitted then its value is assumed to 1
      * If `Imm` is omitted then its value is assumed to 0
      * If `%r1` is omitted then `R[%r1]` evaluates to 0
      * If `%r2` is omitted then `R[%r2]` evaluates to 0
* Simple move instructions
  * `movb`, `movw`, `movl`, `movq`
    * Operands cannot be both memory
    * Only specific bytes are updated
      * Exception: `movl` with register as destination (higher bits zeroed out)
    * `movq` immediate operands only up to 32 bits
  * `movabsq`
    * Initialize all bits of 64-bit register under control of source operand
* Move to a wider width
  * Unsigned integer: zero extension (e.g., `movzbw`, ...)
  * Signed integer: sign extension (e.g., `movsbw`, ...)
  * Destination always a register
* Stack access
  * Push a value on the stack
    * `push %reg`
      * `R[%rsp] = R[%rsp] - 8`
      * `M[R[%rsp]] = R[%reg]`
  * Pop a value from the stack
    * `pop %reg`
      * `R[%reg] = M[R[%rsp]]`
      * `R[%rsp] = R[%rsp] + 8`
  * Operand can be a memory location
