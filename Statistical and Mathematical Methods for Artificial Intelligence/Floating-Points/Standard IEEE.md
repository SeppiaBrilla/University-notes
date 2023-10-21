The [IEEE](https://www.ieee.org/) standards for [[Floating-Point number]] are:
- **Single precision** : 32 bit.

 | 1 (sign)      | 23 (mantissa) | 8 (exponent) |
 | ----------- | ----------- | ------------ |
 - **Double precision** : 64 bit.
 
 | 1 (sign)      | 52 (mantissa) | 11 (exponent) |
 | ----------- | ----------- | ------------ |

Due to the [[Normalized Floating-Point number|normaization]] the first bit is always 1 and, therefore, is hidden

Special values in the IEEE standards are: 
- *Inf* that occurs when dividing a finite number by 0 (like: $\frac{1}{0}$)
- *NaN* for undefined or undetermined operations such as $\frac{0}{0}$ or 0 \* *Inf* or $\frac{Inf}{Inf}$
-