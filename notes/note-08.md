# Note 08

## Unsigned numbers

Bit vector interpreted as a number.

Bit vector: bn−1 bn−2 … b3 b2 b1 b0

"b0" is the least significant digit, "b1" the next one, and so on, until "bn−1",
the most significant digit.

Value encoded:

* bn−1×2^(n−1) + bn−2×2^(n−2) + … + b3×2^3 + b2×2^2 + b1×2^1 + b0×2^0

## Signed numbers

Few alternatives.

### Signed magnitude

* One bit to encode the sign
* The other bits to encode the magnitude (i.e., an unsigned number)

Sign: bn−1
Magnitude: bn−2 … b3 b2 b1 b0

Value encoded:

* If bn−1 is clear: bn−2×2^(n−2) + … + b3×2^3 + b2×2^2 + b1×2^1 + b0×2^0
* If bn−1 is set: −(bn−2×2^(n−2) + … + b3×2^3 + b2×2^2 + b1×2^1 + b0×2^0)

Discussion:

* Fewer encoding dedicated to positive numbers
* Two encodings for zero (+0 and −0)
* Adding two numbers together requires special care

### Biased

A signed number is represented by the bit pattern corresponding to the unsigned
number plus a bias. With this encoding, 0 is represented by the unsigned
encoding of the bias.

Consider numbers encoded with eight bits and a bias of 128. Then encodings
`00000000` represents value −128, `00000001` value −127, …, `01111111` value −1,
`10000000` value 0, `10000001` value +1, …, and `11111111` value +127.

Discussion:

* Only one encoding for zero
* Adding two numbers together requires special care (e.g., regular addition of
  −128 + (−128) yields −128)


### One’s complement

Use the bitwise complement of the unsigned number to represent negative numbers.
Considering an 8-bit encoding, then the representation of −1 is the bitwise
complement of `00000001` (i.e., the unsigned encoding for 1) which yields
`11111110`, −2 is `11111101` (the bitwise complement of `00000010`), and so on.

Discussion:

* We’re back to two encodings for zero
* Adding two numbers together requires special care

### Two’s complement

Use the complement of the unsigned number plus one to represent negative
numbers. The increment of the complement shifts all the negative numbers by one
position to avoid two representations of zero.

Again consider an 8-bit representation. To obtain the two’s complement encoding
of −1, start with the unsigned encoding of +1 (`00000001`), compute its bitwise
complement (`11111110`), and finally add one (`11111110 + 1 = 11111111`). The
encoding of −2 is `11111110` (encoding of +2 is `00000010`, its bitwise
complement is `11111101`, add one: `11111110`).

Discussion:

* Single encoding for zero
* Regular addition works in (almost) all cases (try 1 + (−1) or −1 + (−1))
