
# Python Expression Operators

## Mathematical Operators

These are used for arithmetic calculations:

- **`+` (Addition)**: Adds two numbers.Example: `5 + 3` → `8`
- **`-` (Subtraction)**: Subtracts one number from another.Example: `5 - 3` → `2`
- **`*` (Multiplication)**: Multiplies two numbers.Example: `5 * 3` → `15`
- **`/` (Division)**: Divides one number by another.Example: `5 / 2` → `2.5`
- **`%` (Modulus)**: Returns the remainder of division.Example: `5 % 2` → `1`
- **`//` (Floor Division)**: Divides and returns the integer part of the quotient.Example: `5 // 2` → `2`
- **`**` (Exponentiation)**: Raises a number to the power of another.
  Example: `5 ** 2` → `25`

---

## Bitwise Operators

Used to perform operations on bits:

- **`&` (AND)**: Performs bitwise AND.Example: `5 & 3` → `1` (Binary: `0101 & 0011 = 0001`)
- **`|` (OR)**: Performs bitwise OR.Example: `5 | 3` → `7` (Binary: `0101 | 0011 = 0111`)
- **`^` (XOR)**: Performs bitwise XOR.Example: `5 ^ 3` → `6` (Binary: `0101 ^ 0011 = 0110`)
- **`~` (NOT)**: Inverts the bits.Example: `~5` → `-6` (Binary: `~0101 = 1010`, considering 2's complement)
- **`<<` (Left Shift)**: Shifts bits to the left.Example: `5 << 1` → `10` (Binary: `0101 << 1 = 1010`)
- **`>>` (Right Shift)**: Shifts bits to the right.
  Example: `5 >> 1` → `2` (Binary: `0101 >> 1 = 0010`)

---

## Comparison Operators

Used to compare values:

- **`<` (Less Than)**: Checks if left is less than right.Example: `5 < 3` → `False`
- **`<=` (Less Than or Equal)**: Checks if left is less than or equal to right.Example: `5 <= 5` → `True`
- **`>` (Greater Than)**: Checks if left is greater than right.Example: `5 > 3` → `True`
- **`>=` (Greater Than or Equal)**: Checks if left is greater than or equal to right.Example: `5 >= 3` → `True`
- **`==` (Equal)**: Checks if values are equal.Example: `5 == 3` → `False`
- **`!=` (Not Equal)**: Checks if values are not equal.
  Example: `5 != 3` → `True`

---

## Logical Operators

Used for combining conditional statements:

- **`not`**: Reverses the result of a condition.Example: `not True` → `False`
- **`and`**: Returns True if both conditions are True.Example: `True and False` → `False`
- **`or`**: Returns True if any condition is True.
  Example: `True or False` → `True`

---

## Membership Operators

Checks if a value is in a sequence:

- **`in`**: Returns True if a value exists in a sequence.Example: `'a' in 'apple'` → `True`
- **`not in`**: Returns True if a value does not exist in a sequence.
  Example: `'b' not in 'apple'` → `True`

---

## Identity Operators

Used to compare the memory locations of two objects:

- **`is`**: Returns True if two variables point to the same object.Example: `a = [1, 2]; b = a; a is b` → `True`
- **`is not`**: Returns True if two variables point to different objects.
  Example: `a = [1, 2]; b = [1, 2]; a is not b` → `True`

---

## Indexing and Slicing

Access elements or subsequences in a collection:

- **Indexing**:Example: `x = [1, 2, 3]; x[0]` → `1`
- **Slicing**:
  Example: `x = [1, 2, 3, 4]; x[1:3]` → `[2, 3]`

---

## Function Call and Attribute Access

Used to call functions or access an object's attributes:

- **Function Call**:Example: `def greet(): return "Hello"; greet()` → `"Hello"`
- **Attribute Access**:
  Example: `class X: pass; x = X(); x.attr = 5; x.attr` → `5`

---

## Operator Precedence

Operators are evaluated in the following order:

1. Parentheses `()`
2. Exponentiation `**`
3. Multiplication/Division/Floor Division/Modulus `*`, `/`, `//`, `%`
4. Addition/Subtraction `+`, `-`
5. Logical and Comparison Operators (`not`, `and`, `or` have the lowest precedence).

---

## Example: Mixed Operators

```python
result = (3 + 2) * 2 ** 3 // 3 % 5
# Step-by-step evaluation:
# 1. Parentheses: (3 + 2) → 5
# 2. Exponentiation: 2 ** 3 → 8
# 3. Multiplication: 5 * 8 → 40
# 4. Floor Division: 40 // 3 → 13
# 5. Modulus: 13 % 5 → 3
# Final Result: 3
```


### More examples of **Indexing and Slicing** in Python, showcasing how can manipulate and extract data from sequences like strings, lists, or tuples:

```python
# Indexing Examples
text = "Python"
print(text[0])  # 'P' (First character)
print(text[-1]) # 'n' (Last character)

numbers = [10, 20, 30, 40]
print(numbers[2])  # 30 (3rd element)
print(numbers[-2]) # 30 (2nd-to-last element)

# Slicing Examples
text = "Python"
print(text[1:4])  # 'yth' (Characters from index 1 to 3)
print(text[:3])   # 'Pyt' (First three characters)
print(text[3:])   # 'hon' (From index 3 to the end)
print(text[::2])  # 'Pto' (Every second character)

numbers = [10, 20, 30, 40, 50]
print(numbers[1:4])   # [20, 30, 40] (Subset from index 1 to 3)
print(numbers[::2])   # [10, 30, 50] (Every second element)
print(numbers[::-1])  # [50, 40, 30, 20, 10] (Reverse the list)

# Nested Indexing
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
print(matrix[1][2])  # 6 (Element in the 2nd row and 3rd column)

# Slicing and Assignment
numbers = [1, 2, 3, 4, 5]
numbers[1:4] = [8, 9]  # Replace indices 1, 2, and 3
print(numbers)         # [1, 8, 9, 5]

# Strings are Immutable
greeting = "hello"
# greeting[0] = 'H'   # Error! Strings can't be modified directly.
modified_greeting = "H" + greeting[1:]
print(modified_greeting)  # 'Hello'

# Advanced Slicing with Steps
alphabet = "abcdefghijklmnopqrstuvwxyz"
print(alphabet[2:20:3])  # 'cfilor' (Every 3rd character between indices 2 and 19)
print(alphabet[::-1])    # 'zyxwvutsrqponmlkjihgfedcba' (Reverse the string)
```


**advanced examples of membership operators** combined with **for loops** and other techniques for more complex scenarios:

```python
# Example 1: Using "in" with a for loop to filter items
fruits = ["apple", "banana", "cherry", "date"]
allowed_fruits = ["apple", "cherry"]

# Only keep fruits that are in the allowed list
result = [fruit for fruit in fruits if fruit in allowed_fruits]
print(result)  # Output: ['apple', 'cherry']

# Example 2: Using "not in" to exclude items
excluded_items = ["spam", "ham"]
items = ["eggs", "spam", "bacon", "ham", "toast"]

# Remove unwanted items
cleaned_list = [item for item in items if item not in excluded_items]
print(cleaned_list)  # Output: ['eggs', 'bacon', 'toast']

# Example 3: Nested "in" checks in a matrix
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

# Check if a specific number exists in any row
target = 5
found = any(target in row for row in matrix)
print(found)  # Output: True

# Example 4: Membership with dictionaries in a loop
dictionary = {"name": "Alice", "age": 30, "city": "Wonderland"}
keys_to_check = ["age", "city", "job"]

# Check which keys exist in the dictionary
existing_keys = [key for key in keys_to_check if key in dictionary]
print(existing_keys)  # Output: ['age', 'city']

# Example 5: Multi-step membership with strings
sentences = ["The cat is on the mat.", "Python is fun.", "Hello world!"]
keywords = ["Python", "world"]

# Find sentences that contain any of the keywords
matching_sentences = [sentence for sentence in sentences if any(keyword in sentence for keyword in keywords)]
print(matching_sentences)  # Output: ['Python is fun.', 'Hello world!']

# Example 6: Combining membership and string slicing
text = "abcdef"
substrings = ["abc", "efg"]

# Extract substring slices that are found
found_substrings = [substring for substring in substrings if substring in text]
print(found_substrings)  # Output: ['abc']
```

These examples demonstrate how you can creatively use **membership operators (`in`, `not in`)** with **for loops**, **list comprehensions**, and other constructs to solve more sophisticated problems.


### More Examples:


```python
# Example 1: Basic formatting
num = 5.6789
print('{0:6.2f}'.format(num))  # Output: '  5.68'
# Width of 6 includes 2 spaces before the number.

# Example 2: Multiple placeholders
a, b = 12.3, 45.678
print('{0:5.1f} | {1:7.3f}'.format(a, b))  # Output: ' 12.3 |  45.678'

# Example 3: Variable number of decimals
fornum in[1.2345, 6.789]:
    print('{0:6.3f}'.format(num))
# Outputs:
# ' 1.235'
# ' 6.789'
```
