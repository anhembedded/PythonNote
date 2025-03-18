# Other Core Types in Python

Python includes several additional core types beyond the basics (like numbers, strings, lists, and dictionaries). These include **sets**, **decimal numbers**, **fractions**, **Booleans**, and **None**. Additionally, Python supports **user-defined classes** for creating custom object types. Below is a detailed explanation of these types and their uses.

---

## 1. **Sets**

- **Description**: Unordered collections of unique and immutable objects.
- **Creation**: Use the `set()` function or set literals `{}` (Python 3.0+).
- **Operations**: Supports mathematical set operations like union, intersection, and difference.
- **Example**:
  ```python
  X = set('spam')  # {'a', 'p', 's', 'm'}
  Y = {'h', 'a', 'm'}  # {'a', 'h', 'm'}
  print(X & Y)  # Intersection: {'a', 'm'}
  print(X | Y)  # Union: {'a', 'p', 's', 'h', 'm'}
  print(X - Y)  # Difference: {'p', 's'}
  ```

---

## 2. **Decimal and Fraction Numbers**

- **Decimal**: Fixed-precision floating-point numbers for accurate calculations.
  ```python
  import decimal
  d = decimal.Decimal('3.141')
  print(d + 1)  # Decimal('4.141')
  decimal.getcontext().prec = 2
  print(decimal.Decimal('1.00') / decimal.Decimal('3.00'))  # Decimal('0.33')
  ```
- **Fraction**: Represents rational numbers with a numerator and denominator.
  ```python
  from fractions import Fraction
  f = Fraction(2, 3)
  print(f + 1)  # Fraction(5, 3)
  print(f + Fraction(1, 2))  # Fraction(7, 6)
  ```

---

## 3. **Booleans**

- **Description**: Represents truth values (`True` or `False`). These are essentially integers (`1` for `True`, `0` for `False`) with custom display logic.
- **Example**:
  ```python
  print(1 > 2)  # False
  print(bool('spam'))  # True
  ```

---

## 4. **None**

- **Description**: A special placeholder object used to represent the absence of a value.
- **Example**:
  ```python
  X = None
  print(X)  # None
  L = [None] * 100  # A list of 100 None values
  ```

---

## 5. **Type Checking**

- **Description**: Python allows type checking using `type()` or `isinstance()`, but it is generally discouraged to maintain code flexibility.
- **Example**:
  ```python
  L = [1, 2, 3]
  if type(L) == list:  # Not recommended
      print("yes")
  if isinstance(L, list):  # Preferred
      print("yes")
  ```

---

## 6. **User-Defined Classes**

- **Description**: Classes allow you to define custom object types with attributes (state) and methods (behavior).
- **Example**:
  ```python
  class Worker:
      def __init__(self, name, pay):  # Constructor
          self.name = name
          self.pay = pay
      def lastName(self):
          return self.name.split()[-1]  # Get last name
      def giveRaise(self, percent):
          self.pay *= (1.0 + percent)  # Increase pay

  bob = Worker('Bob Smith', 50000)
  sue = Worker('Sue Jones', 60000)
  print(bob.lastName())  # Smith
  sue.giveRaise(0.10)
  print(sue.pay)  # 66000.0
  ```

---

## 7. **Polymorphism and Flexibility**

- **Description**: Python encourages coding to object interfaces (operations supported) rather than specific types. This promotes polymorphism, where code works on a wide range of types.
- **Example**:
  ```python
  def process(data):
      if hasattr(data, 'append'):  # Check for required operation
          data.append(1)
      return data

  print(process([1, 2, 3]))  # Works with lists
  print(process(set([1, 2, 3])))  # Fails with sets (no append method)
  ```

---

## 8. **Other Types**

- **Program Execution Types**: Functions, modules, classes, and compiled code are also objects in Python.
- **Application-Specific Types**: Imported modules provide types for text patterns, database interfaces, network connections, etc.

---

## Key Takeaways

- **Sets**: Unordered collections of unique elements, supporting mathematical operations.
- **Decimal and Fraction**: For precise numeric calculations.
- **Booleans**: Represent truth values (`True` or `False`).
- **None**: A placeholder for the absence of a value.
- **User-Defined Classes**: Allow creating custom object types with attributes and methods.
- **Polymorphism**: Python encourages flexible, type-agnostic coding.

These core types and concepts form the foundation of Python programming, enabling both simplicity and powerful customization.
