# Note 18

Some of this content is adapted from *Computer Systems: A Programmer's
Perspective, 3rd Edition*.

## Arithmetic and other operations

Open your browser to address https://godbolt.org, uncheck Output > Intel asm
syntax, and set compiler options to `-O`.

### Unary and binary C operators

Using

```c
long op(long x, long y) {
    return x - y;
}
```

as a template, try all C operators we have studied, replacing the subtraction
appropriately. In each case, note the name of the assembly instruction(s) used
to implement the operator. Also verify your understanding of passing parameters
through registers.

### Array accesses

Note the difference between

```c
long f1(long a[], long i) {
    return a[i];
}
```

and

```c
long *f1(long a[], long i) {
    return &a[i];
}
```

Do these examples help understand the purpose of the `lea` instruction? Do
they help understand how the C compiler implemented addition in the previous
section?

### Put it all together

Study the code generated for

```c
long arith(long x, long y, long z) {
    long t1 = x + y;
    long t2 = z + t1;
    long t3 = x + 4;
    long t4 = y*48;
    long t5 = t3 + t4;
    long rval = t2*t5;
    return rval;
}
```
