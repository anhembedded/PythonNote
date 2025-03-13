# Dictionaries in Python

## Introduction

Python dictionaries are mappings that store objects by key rather than relative position. Unlike sequences, they do not maintain a reliable left-to-right order but map keys to associated values. Dictionaries are mutable, meaning they can be modified in place, growing and shrinking dynamically.

## Mapping Operations

Dictionaries are written as `{key: value}` pairs within curly braces (`{}`). They are useful for associating values with keys, such as describing an object’s properties.

```python
D = {'food': 'Spam', 'quantity': 4, 'color': 'pink'}
print(D['food'])  # Output: Spam
D['quantity'] += 1
print(D)  # Output: {'food': 'Spam', 'quantity': 5, 'color': 'pink'}
```

Dictionaries can also be created dynamically:

```python
D = {}
D['name'] = 'Bob'
D['job'] = 'dev'
D['age'] = 40
print(D)  # Output: {'name': 'Bob', 'job': 'dev', 'age': 40}
```

## Nesting in Dictionaries

Dictionaries can store complex data structures, including nested dictionaries and lists.

```python
rec = {'name': {'first': 'Bob', 'last': 'Smith'},
       'job': ['dev', 'mgr'],
       'age': 40.5}

print(rec['name']['last'])  # Output: Smith
print(rec['job'][-1])  # Output: mgr
rec['job'].append('janitor')
print(rec['job'])  # Output: ['dev', 'mgr', 'janitor']
```

## Sorting Dictionary Keys

Dictionaries do not maintain order, but we can sort keys:

```python
D = {'a': 1, 'b': 2, 'c': 3}
for key in sorted(D):
    print(key, '=>', D[key])
```

## Iteration in Dictionaries

Using `for` loops to iterate over dictionary keys:

```python
for c in 'spam':
    print(c.upper())
```

Using `while` loops:

```python
x = 4
while x > 0:
    print('spam!' * x)
    x -= 1
```

## Handling Missing Keys

Fetching a nonexistent key raises a `KeyError`. We can prevent errors by checking key existence:

```python
D = {'a': 1, 'b': 2, 'c': 3}
if 'f' not in D:
    print('missing')  # Output: missing
```

Using the `get` method to provide default values:

```python
value = D.get('x', 0)  # Returns 0 if 'x' is not in D
```

Dictionaries are powerful tools for efficient data storage and retrieval in Python, enabling structured and dynamic data management.
