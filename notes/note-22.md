# Note 22

Parts of this note are adapted from *Computer Systems: A Programmer's
Perspective, 3rd Edition*.

## If statements

Consider:

```c
void cond(short a, short *p) {
    if (a && *p < a)
        *p = a;
}
```

1. Implement `cond` in assembly.
2. Compare your implementation with the output produced by `godbolt.org` with
   the `-O` compiler option.
3. Explain why the assembly contains two condition jump instructions.

## Loops

Today, we will look at different ways that loops are compiled into assembly
code.

## Jump instruction encodings

There are several strategies for encoding the target of jump instructions. One
common strategy encodes the target *relative* to the address in memory of the
jump instruction.

### Activity

Below you will find snippets of output of a disassembler. A disassembler reads
a binary and decodes it back to assembly instructions, typically one per line.
The first column represents the address of the instruction, followed by its
encoding, and ending with assembly instruction. All the numbers are produced in
hexadecimal format.

I have replaced the address of most jump instructions with `XXXXXX`. Replace all
instances of `XXXXXX` with the addresses of the jump target (you do not need to
know what the `call`, `hlt`, and `xchg` instructions do to solve these
problems).

```
40100f:       48 85 c0                test   %rax,%rax
401012:       74 02                   je     XXXXXX
401014:       ff d0                   call   *%rax
401016:       48 83 c4 08             add    $0x8,%rsp
40101a:       c3                      ret
```

```
401365:       e8 76 55 04 00          call   4468e0
40136a:       f4                      hlt
40136b:       eb fd                   jmp    XXXXXX
```

```
40169b:       74 13                   je     XXXXXX
40169d:       b8 00 00 00 00          mov    $0x0,%eax
4016a2:       48 85 c0                test   %rax,%rax
4016a5:       74 09                   je     XXXXXX
4016a7:       bf c8 6a 4c 00          mov    $0x4c6ac8,%edi
4016ac:       ff e0                   jmp    *%rax
4016ae:       66 90                   xchg   %ax,%ax
4016b0:       c3                      ret
```
