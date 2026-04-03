# Lab #5: Fun with Logic Design

In class, we have seen how to implement circuits for some of the C bitwise
operators. This assignment helps answer what is the same and what is different
about implementing operators such as addition.

## Tool

We will continue using Helmut Neeman's [simple digital circuit
simulator](https://github.com/hneemann/digital).

## Hierarchical construction

Review the wikipedia article about
[Adders](https://en.wikipedia.org/wiki/Adder_(electronics)).

First, construct a half adder and save it as HA.dig. For this step, you are only
to use items in Components > Logic, Components > Wire, and Components > IO. If
you feel like building your own logic gates, from transistors, you may use items
in Components > Switches.

Second, construct a full adder using as many instances of the half adder as
necessary. Save this circuit in the file FA.dig.

Third, build a 4-bit adder using instances of the full adder you just
constructed. Save the result in a file called ADDER.dig.

## Notes

* You may need to open a circuit multiple times before it becomes available as a
  building block under Components > Custom.'
* For verification, you can generate the truth table of your designs with the
  command Analysis > Analysis.
* Claude Shannon demonstrated binary addition in his graduate thesis.

## What to hand in

Upload `HA.dig`, `FA.dig`, and `ADDER.dig`. Don’t forget to add your name
somewhere as text decorations (Components > Misc. > Decoration > Text).
