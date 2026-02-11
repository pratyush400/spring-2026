# 10 Shift Operations

Assume 8-bit unsigned numbers.

Consider the 8-bit unsigned binary number `00010100`.

* Convert it to decimal and hexadecimal.
* Shift it by one position to the right. What decimal value do you end up with?
* Shift it by two positions to the right. Same question.
* Shift it by one position to the left. Same question.
* Shift it by two positions to the left. Same question.

Consider the 8-bit unsigned binary number `11111100`.

* Convert it to decimal and hexadecimal.
* Shift it by one position to the right. What decimal value do you end up with?
* Shift it by two positions to the right. Same question.

Can you describe, in prose, what is happening to a binary number when you shift
it by *n* positions? Ignore overflows.

Now assume 8-bit signed numbers using the two's complement encoding and consider
the same pattern as in the last example (`11111100`) but interpret it as a
signed number.

* What happens when you shift that pattern by one position to the left? What
  value do you end up with?
* What about when you shift that pattern by two positions to the left?
* Ideally, what would you like the result to be when you shift that pattern by
  one position to the right?
* Two positions to the right?
* Can you draw a conclusion?
