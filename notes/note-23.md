# Note 23

## Functions

The action of calling a function involves three mechanisms:

* Passing control (calling and returning from a function)
* Passing data (passing arguments and returning values)
* Memory management (allocating and deallocating memory for local variables)

### Passing data

The 64-bit x86 assembly passes up to six integral (i.e., integers or pointers)
arguments through registers.

Register | Role
-|-
%rax     | Return value
%rbx     | Callee saved
%rcx     | 4th argument
%rdx     | 3rd argument
%rsi     | 2nd argument
%rdi     | 1st argument
%rbp     | Callee saved
%rsp     | Stack pointer
%r8      | 5th argument
%r9      | 6th argument
%r10     | Caller saved
%r11     | Caller saved
%r12     | Callee saved
%r13     | Callee saved
%r14     | Callee saved
%r15     | Callee saved

### Stack

Assuming function `f` calls function `g`:

```
(top of the stack, lower addresses)
+---------+----------------+ <-- %rsp
| Frame   | Argument build |
| for g   | area           |
|         +----------------+
|         | Local          |
|         | variables      |
|         +----------------+
|         | Saved          |
|         | registers      |
+---------+----------------+
| Frame   | Return address |
| for f   +----------------+
|         | 7th argument   |
|         +----------------+
|         | 8th argument   |
|         +----------------+
|         | ...            |
+---------+----------------+
| Earlier | ...            |
| frame   |                |
(bottom of the stack, higher addresses)
```
