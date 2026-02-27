# Note 17

Adapted from *Computer Systems: A Programmer's Perspective, 3rd Edition* and
the *Intel® 64 and IA-32 Architectures Software Developer’s Manual*.

## Other move instructions

Instruction           | Effect               | Name
-|-|-
`movzbw` *src*, *reg* | *reg* `<-` ZE(*src*) | Move zero-extended byte to word
`movzbl` *src*, *reg* | *reg* `<-` ZE(*src*) | Move zero-extended byte to doubleword
`movzbq` *src*, *reg* | *reg* `<-` ZE(*src*) | Move zero-extended byte to quadword
`movzwl` *src*, *reg* | *reg* `<-` ZE(*src*) | Move zero-extended word to doubleword
`movzwq` *src*, *reg* | *reg* `<-` ZE(*src*) | Move zero-extended word to quadword
`movsbw` *src*, *reg* | *reg* `<-` SE(*src*) | Move sign-extended byte to word
`movsbl` *src*, *reg* | *reg* `<-` SE(*src*) | Move sign-extended byte to doubleword
`movsbq` *src*, *reg* | *reg* `<-` SE(*src*) | Move sign-extended byte to quadword
`movswl` *src*, *reg* | *reg* `<-` SE(*src*) | Move sign-extended word to doubleword
`movswq` *src*, *reg* | *reg* `<-` SE(*src*) | Move sign-extended word to quadword
`movslq` *src*, *reg* | *reg* `<-` SE(*src*) | Move sign-extended doubleword to quadword

Notes:
* Source: either register or memory
* Destination: only register
* `movzlq` is missing, subsumed by `movl`

## Access the stack

Instruction   | Effect                | Name
-|-|-
`pushq` *src* | $M[R[--\%rsp]] = src$ | Push quadword
`popq` *dst*  | $dst = M[R[\%rsp++]]$ | Pop quadword

Note:
* Be careful in reading the effect of these instructions; I've packed a lot of
  information
