# Note 06

## `make`

`make` is a standard Unix utility used to build C applications. `make` reads
a file named `makefile` to figure out how to build the application.

A `makefile` consists of

* definitions
  ```
  VAR = WORDS...
  ```
* rules
  ```
  TARGET: DEPENDENCES...
         COMMAND
         ...
  ```

Definitions and rules can refer to previous definitions by enclosing the desired
variable with `$(` and `)` (e.g., `$(VAR)`).

If you type `make TARGET`, `make` will build `TARGET`. If you omit `TARGET`,
`make` builds the `TARGET` of the first rule that appears in `makefile`.

This note is just a short summary of the capabilities of the `make` utility. For
more information refer to the manual (`man make`).
