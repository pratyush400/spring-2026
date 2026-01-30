# Note 05

## Phases of C compilation

The compilation a C program typically goes through the following phases:

1. Preprocessing
2. Compilation
3. Assembly
4. Linkage

Let us study these phases with the help of the files generated when we invoke
the compiler with the flag `--save-temps`. Not all C compilers support this
flag, but GNU gcc and clang do.

## Regions of memory

Now that we know how to print the value of a pointer, write a program that
prints the address of (1) a small global variable (e.g., a scalar), (2) a large
global variable (e.g., a large array), (3) a local (i.e., declared inside a
function) variable, (4) a small dynamic allocation (e.g., 8 bytes), (5) a large
dynamic allocation (e.g., 100,000 bytes), (6) a function you defined, and (5) a
function available in a library (e.g., `malloc` or `printf`).

Relevant regions of memory include:

* text
* stack
* heap

Can you assign each of the addresses you printed to a specific region?
