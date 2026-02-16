# Note 12

## IEEE floating-point

### Representation

$V = (-1)^s \times M \times 2^E$

where

* The sign $s$ determines if the number is negative or positive
* The significand $M$ is a fractional binary number
* The exponent $E$ weights the value a power of 2

### Encoding

The 32-bit format is encoded as follows:

```
  31  30        23  22          0
+---+----- ... ---+------ ... ---+
| s | exp         | frac         |
+---+----- ... ---+------ ... ---+
```

where

* The single sign bit `s` directly encodes the sign $s$
* The 8-bit exponent field `exp` = $e_7...e_1e_0$ encodes the exponent $E$
* The 23-bit fraction field `frac` = $f_{22}..f_1f_0$ encodes the
  significand $M$

#### Normalized values

When `exp` $\neq$ 0 and `exp` $\neq$ 255

> $E$ = `exp` $-Bias$ where $Bias = 2^7-1 = 127$  
> $M$ = $1 + f$ where $f$ = 0.$frac_{22}...frac_1frac_0$

#### Denormalized values

When `exp` = 0

> $E = 1 - Bias$  
> $M = f$ where $f = 0.frac_{22}...frac_1frac_0$

#### Special values

When `exp` = 255

> If `frac` = 0, then infinity  
> If `frac` $\neq$ 0, then NaN
