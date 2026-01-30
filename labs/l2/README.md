# Doubly Linked Lists

In this assignment, you will learn how to create (and to destroy) doubly linked
lists in C. This work entails learning about how C supports dynamic memory
allocation. In this regard, there are several differences between Python and C:

- In C, you are completely in charge; no garbage collection! You allocate memory
  with a call to `malloc()` and release that memory, when are you are done with
  it, with a call to `free()`. See `man malloc` for more details.

- In C, `malloc()` returns a pointer to untyped memory (`void *`), it is
  customary but not required to cast that pointer to the correct type for use in
  your program. Note that `malloc()` may return `NULL` if out of memory. Your
  program must check for that condition as well.

- `malloc()` takes a size as an argument. You can get help from the pseudo
  function `sizeof()` to figure out the size of a data structure (e.g.,
  `sizeof(struct list)`).

## Building your code

This assignment comes with a `makefile`. To build your code, type `make list.o`.
To receive full credits, the compilation must not issue any warnings.

## Unit tests

This assignment comes with unit tests. To get full credit, all the tests must
pass. To run the unit tests, type `make test`.

## Memory leaks

One difficult tasks facing C programmers is to free dynamically allocated memory
properly: not too soon; not too late; just in time. The utility `valgrind` helps
us find memory leaks and other errors when using dynamic memory allocation
(e.g., freeing twice the same memory). The `makefile` runs valgrind for you.
Therefore the utility must be installed on the platform on which you run your
tests. `valgrind` should be installed on all the machines in Olin 309. Please
find me, if you want to install this tool in your system. To receive full
credits, valgrind must issue a clean bill of health (no leaks, etc.). To check
for leaks, type `make leak`. Typing `make` by itself, runs both the unit tests
and the checks for leaks.

A successful leak check should include the phrase `All heap blocks were freed --
no leaks are possible`.

## Check the values returned By `malloc`

To receive full credits, you must check that malloc does not return `NULL` (an
indication that the program ran out of memory).

## What to hand in

Hand in your one filled-in file `list.c`.

## Extra credits

This assignment implements a doubly linked list of longs. What are possible
alternatives, if you want to support a list of an arbitrary data type? For
instance, suppose you want to give a user the ability to create a list of
doubles as well as a list of character arrays with a single `list.h`/`list.c`
pair. What are your options? I'm not saying, it's going to be pretty.
