# Homework #7

## Alignment and padding

Consider the following C definition:

```c
struct s {
    short type;
    int range;
    char key;
    double value;
};
```

Using the template below (allowing a maximum of 28 bytes), indicate the
allocation of data for `struct s`. Mark off and label the areas for each
individual element. I have already marked the bytes allocated for field
`type` (using capital letter `T`). Cross hatch the parts that are allocated,
but not used (to satisfy alignment).

Assume the Linux alignment rules discussed in class. Clearly indicate the right
hand boundary of the data structure with a vertical line (to satisfy alignment
of arrays of these `struct`s).

```
                     1 1 1 1 1 1 1 1 1 1 2 2 2 2 2 2 2 2
 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|T|T| | | | | | | | | | | | | | | | | | | | | | | | | | |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
```

Reorder the fields in `struct s` to minimize its allocation size. Give the new
`struct` definition in the space below and indicate the new allocation size.

```






```

## Nand gate

In class, we have developed a circuit for the nor gate. On the back of this
page, draw a circuit for the nand gate (negated and). Like the nor gate, the
nand gate has two inputs, one output, and can be built with four transistors
(two P-Channel FETs and two N-Channel FETs).
