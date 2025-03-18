
### Other Numeric Types in Python

Python provides additional numeric types beyond integers, floats, and complex numbers, including **Decimal** and **Fraction** types, which help improve numerical accuracy.

#### **Decimal Type**

* Introduced in Python 2.4, Decimals are fixed-precision floating-point numbers.
* Created using `Decimal` from the `decimal` module, typically initialized with strings for accuracy.
* Example:
  ```python
  from decimal import Decimal
  Decimal('0.1') + Decimal('0.1') + Decimal('0.1') - Decimal('0.3')  # Output: Decimal('0.0')
  ```
* Avoids floating-point precision errors (e.g., `0.1 + 0.1 + 0.1 - 0.3` results in `5.55e-17` with floats).
* Global precision can be set using `decimal.getcontext().prec = n`.
* The `with` statement allows temporary precision changes using `decimal.localcontext()`.

#### **Fraction Type**

* Introduced in Python 2.6 and 3.0, `Fraction` represents rational numbers using a numerator and denominator.
* Automatically simplifies fractions using the greatest common divisor (GCD).
* Example:
  ```python
  from fractions import Fraction
  x = Fraction(1, 3)  
  y = Fraction(4, 6)  # Simplified to Fraction(2, 3)
  ```
* Fractions avoid floating-point inaccuracies, providing exact arithmetic operations.
* Can be initialized from strings or floats (`Fraction.from_float(1.75)`).
* Mixed-type arithmetic is supported but may require explicit conversions.

#### **Key Differences**

| Feature   | Float          | Decimal                | Fraction                  |
| --------- | -------------- | ---------------------- | ------------------------- |
| Precision | Limited        | Configurable           | Exact                     |
| Storage   | Hardware-based | Arbitrary precision    | Numerator/denominator     |
| Speed     | Fastest        | Slower                 | Slowest                   |
| Use Case  | General math   | Financial calculations | Exact rational arithmetic |

Both Decimal and Fraction improve numerical accuracy at the cost of performance.

### **"Numeric Extensions"**

Python has powerful built-in numeric types, but third-party libraries extend its capabilities for specialized needs. **NumPy (Numeric Python)** is a widely used extension that provides advanced numerical tools such as matrices, vector processing, and high-performance computations. It is popular in scientific fields, including NASA and Los Alamos, as an alternative to languages like C++, FORTRAN, and Matlab. NumPy, combined with Python, offers flexibility and performance comparable to Matlab. Other numerical tools, such as SciPy, statistics libraries, and plotting tools, are available through Python’s package ecosystem. However,  **NumPy is not included with Python by default and must be installed separately** .
