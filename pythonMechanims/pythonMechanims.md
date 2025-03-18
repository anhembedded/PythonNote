
# Dynamic Typing in Python

Python's **dynamic typing** is a fundamental feature that contributes to its flexibility and conciseness. Unlike statically typed languages (e.g., C, C++, Java), Python does not require variable declarations or type definitions. Instead, types are determined automatically at runtime. This allows Python code to be more versatile and adaptable. Below is a detailed explanation of how dynamic typing works in Python.

---

## Key Concepts

### 1. **Variables, Objects, and References**

- **Variables**: Names used to reference objects (e.g., `a = 3`).
- **Objects**: Pieces of memory that store data and their types (e.g., the integer `3`).
- **References**: Links between variables and objects (implemented as pointers).

   When you assign a value to a variable:

```python
   a = 3
```

   Python performs the following steps:

1. Creates an object to represent the value `3`.
2. Creates the variable `a` (if it doesn’t already exist).
3. Links `a` to the object `3`.

---

### 2. **Dynamic Typing**

- **No Type Declarations**: Variables are not bound to a specific type. They can reference any type of object.
- **Types Live with Objects**: The type of a variable is determined by the object it references, not the variable itself.
- Example:
  ```python
  a = 3        # a references an integer
  a = 'spam'   # a now references a string
  a = 1.23     # a now references a float
  ```

  Here, `a` changes the type of object it references, but `a` itself has no type.

---

### 3. **Object Header Fields**

- Every object has two standard header fields:
  1. **Type Designator**: Identifies the object’s type (e.g., `int`, `str`).
  2. **Reference Counter**: Tracks the number of references to the object.

---

### 4. **Garbage Collection**

- Python automatically reclaims memory for objects that are no longer referenced.
- **Reference Counting**: Each object has a counter that tracks how many variables reference it. When the counter drops to zero, the object is garbage collected.
- Example:
  ```python
  x = 42        # Object 42 is created, referenced by x
  x = 'shrubbery'  # Object 42 is reclaimed (if no other references exist)
  ```
- **Cyclic References**: Python’s garbage collector can detect and clean up objects involved in reference cycles (e.g., a list that references itself).

---

## Benefits of Dynamic Typing

### 1. **Flexibility**

- Variables can reference any type of object, making code more adaptable.
- Example:
  ```python
  x = 42        # x references an integer
  x = "hello"   # x now references a string
  ```

### 2. **Polymorphism**

- Code can work with multiple types as long as they support the required operations.
- Example:
  ```python
  def double(x):
      return x * 2

  print(double(3))      # Works with integers
  print(double("spam")) # Works with strings
  ```

### 3. **Simplified Code**

- No need for type declarations or memory management (e.g., `malloc`/`free` in C).

---

## Key Takeaways

- **Variables are generic**: They can reference any type of object.
- **Types are associated with objects, not variables**: The type of a variable is determined by the object it references.
- **Garbage collection**: Python automatically reclaims memory for unused objects.
- **Dynamic typing enables polymorphism**: Code can work with multiple types without explicit type checking.

Dynamic typing is a core feature of Python that makes it concise, flexible, and powerful. By understanding how variables, objects, and references work, you can write more efficient and adaptable Python code.


Here's a breakdown of the provided text, summarized with key details and formatted with Markdown:

### **Shared References in Python: A Deep Dive**

This document explores how Python handles object references, a key concept for understanding variable behavior, especially with mutable objects.

#### **1. Basic Shared References**

* **Concept:** When one variable is assigned to another, they both reference the *same* object in memory.

  **Python**

  ```python
  a = 3  # 'a' references the integer object 3
  b = a  # 'b' now also references the *same* integer object 3
  ```
* **Key Detail:** `b = a` doesn't create a copy of the object `a` references. It makes `b` a *pointer* to the *same* object.  The variable `a` is replaced with the object it references.  This is called a "shared reference."
* **Visual Representation:**  The text refers to Figures 6-2 and 6-3, which illustrate this with diagrams of names (variables) pointing to objects.
* **Immutability and reassignment** :

  **Python**

```
  a = 3
  b = a
  a = 'spam' # a now points to a *new* string object 'spam'
              # b *still* points to the integer object 3
```

  **Python**

```
  a = 3
  b = a
  a = a + 2 # a now points to a *new* integer object 5, the result of 3+2
            # b *still* points to the original integer object 3
```

* **Key Detail:** Assigning a *new* value to `a` doesn't change `b`.  `a` simply points to a different object.  Integers are  *immutable* ; they cannot be changed in place.  This is fundamental to understanding why `b` isn't affected.
* **Pointers, Not Labels:** Python variables are  *pointers to objects* , not labels on memory locations that can be changed.

#### **2. Shared References and Mutable Objects (Lists)**

* **Mutability:** Lists, unlike integers and strings, are  *mutable* .  Their contents can be changed  *in place* .
* **In-Place Modification:**

  **Python**

  ```
  L1 = [2, 3, 4]
  L2 = L1       # Shared reference: L1 and L2 point to the *same* list
  L1[0] = 24   # Modify the list *in place*
  print(L1)    # Output: [24, 3, 4]
  print(L2)    # Output: [24, 3, 4]  <-- L2 is also changed!
  ```

  * **Key Detail:** Because `L1` and `L2` point to the *same* list object, modifying the list through `L1` *also* affects `L2`.  This is a direct consequence of shared references and mutability.
* **Avoiding Unintended Side Effects: Copying**

  * **Problem:**  Sometimes you *don't* want to modify the original list.
  * **Solution:** Create a *copy* of the list:

    **Python**

    ```
    L1 = [2, 3, 4]
    L2 = L1[:]  # Create a *copy* using slicing.  L2 is a *new* list.
    L1[0] = 24
    print(L1)    # Output: [24, 3, 4]
    print(L2)    # Output: [2, 3, 4]  <-- L2 is unchanged!
    ```

    Other Copying methods:

    **Python**

    ```
    import copy
    X = copy.copy(Y) #shallow copy
    X = copy.deepcopy(Y) # deep copy, copies nested objects.
    ```

    If the type is a dictionary or set use the `.copy()` method.
  * **Key Detail:** Slicing (`[:]`) creates a new list object.  `copy.copy()` creates a shallow copy (top-level only), and `copy.deepcopy()` creates a full, recursive copy of nested objects. Dictionaries and sets require the `.copy()` method because they aren't sequences.

#### **3. Shared References and Equality**

* **Two Types of Equality Checks:**

  * `==`:  Value equality.  Checks if two objects have the same  *content* .  This is the most common comparison.
  * `is`:  Object identity.  Checks if two variables point to the *exact same object* in memory.  This is a much stricter test.

  **Python**

  ```
  L = [1, 2, 3]
  M = L       # Shared reference
  print(L == M)  # Output: True (same values)
  print(L is M)  # Output: True (same object)

  L = [1, 2, 3]
  M = [1, 2, 3]  # Two *different* list objects with the same content
  print(L == M)  # Output: True (same values)
  print(L is M)  # Output: False (different objects)
  ```
* **Object Caching (Optimization):**

  ```
  X = 42
  Y = 42
  print(X == Y)  # Output: True
  print(X is Y)  # Output: True (likely due to caching)
  ```

  * **Key Detail:** Python caches small integers and strings for performance.  Even though `X` and `Y` are assigned separately, they might point to the *same* cached object.  This is an implementation detail and  *doesn't change the fact that integers are immutable* .
* **Reference Counting (sys.getrefcount)**

  **Python**

  ```
  import sys
  print(sys.getrefcount(1))
  ```

  * The `sys.getrefcount()` function reveals the number of references to an object and how python manages memory.

#### **4. Dynamic Typing and Polymorphism**

* **Dynamic Typing:** The core principle that variables can hold objects of any type, and the type can change over time. This entire discussion of references is a direct consequence of dynamic typing.
* **Polymorphism:** Because Python uses dynamic typing, code can be written without knowing the exact types of objects it will operate on. This leads to flexible and adaptable code (polymorphism).

#### **Key Takeaways:**

* Shared references are created when you assign one variable to another.
* Mutable objects (lists, dictionaries, sets) can be modified in place, affecting all variables that share a reference to them.
* Use copies (slicing, `copy.copy()`, `copy.deepcopy()`, `.copy()`) to avoid unintended modifications of shared mutable objects.
* `==` checks for value equality; `is` checks for object identity.
* Python's object caching is an optimization that usually doesn't affect your code's logic, but it can be visible with the `is` operator.
* Dynamic Typing is the foundation of the whole system.

```python
  a = 3  # 'a' references the integer object 3
  b = a  # 'b' now also references the *same* integer object 3
```

- **Key Detail:** `b = a` doesn't create a copy of the object `a` references. It makes `b` a *pointer* to the *same* object. The variable `a` is replaced with the object it references. This is called a "shared reference."
- **Immutability and Reassignment:**

  ```python
  a = 3
  b = a
  a = 'spam'  # 'a' now points to a *new* string object 'spam'
              # 'b' still points to the integer object 3

  a = a + 2   # 'a' now points to a *new* integer object (5)
              # 'b' still points to the original integer (3)
  ```

  - **Key Detail:** Assigning a *new* value to `a` doesn't change `b`. Integers are **immutable**, meaning they cannot be changed in place.
- **Pointers, Not Labels:** Python variables are *pointers* to objects, not labels attached to memory locations.

---

## **2. Shared References and Mutable Objects (Lists)**

- **Mutability:** Lists, unlike integers and strings, are **mutable**. Their contents can be changed in place.
- **In-Place Modification:**

  ```python
  L1 = [2, 3, 4]
  L2 = L1       # Shared reference: L1 and L2 point to the *same* list
  L1[0] = 24    # Modify the list *in place*
  print(L1)     # Output: [24, 3, 4]
  print(L2)     # Output: [24, 3, 4]  <-- L2 is also changed!
  ```

  - **Key Detail:** Both `L1` and `L2` point to the same list object, so modifying the list affects all references to it.
- **Avoiding Unintended Side Effects: Copying**

  ```python
  L1 = [2, 3, 4]
  L2 = L1[:]     # Creates a *copy* using slicing
  L1[0] = 24
  print(L1)      # Output: [24, 3, 4]
  print(L2)      # Output: [2, 3, 4]  <-- L2 is unaffected!
  ```

  **Other Copying Methods:**

  ```python
  import copy
  X = copy.copy(Y)       # Creates a "shallow" copy
  X = copy.deepcopy(Y)   # Creates a "deep" copy for nested objects
  ```

---

## **3. Shared References and Equality**

- **Types of Equality Checks:**

  - **`==`:** Checks *value equality*—whether two objects have the same content.
  - **`is`:** Checks *object identity*—whether two variables point to the same object.

  ```python
  L = [1, 2, 3]
  M = L
  print(L == M)  # True: same values
  print(L is M)  # True: same object

  N = [1, 2, 3]
  print(L == N)  # True: same values
  print(L is N)  # False: different objects
  ```
- **Object Caching (Optimization):**

  ```python
  X = 42
  Y = 42
  print(X is Y)  # True (caching for small integers)
  ```

---

## **4. Dynamic Typing and Polymorphism**

- **Dynamic Typing:** Variables can reference objects of any type, and the type can change over time.
- **Polymorphism:** Python's dynamic typing enables writing flexible and adaptable code.

---

## **Key Takeaways**

1. Shared references are created when one variable is assigned to another.
2. Mutable objects (e.g., lists) can be modified in place, affecting all variables referencing them.
3. Use `copy.copy()`, `copy.deepcopy()`, or slicing (`[:]`) to avoid unintended modifications.
4. Understand the difference between `==` (value equality) and `is` (identity).
5. Python's dynamic typing simplifies code and supports polymorphism.

```

```
