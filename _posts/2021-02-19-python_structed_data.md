---
title: "[Python] #3 Python Structed Data"
excerpt: "Structed data structure in Python(list, tuple, dictionary, sets)"

categories:
  - Python
tags:
  - [Python, List, Tuple, Dictionary]

toc: true

date: 2021-02-19
last_modified_at: 2021-02-19
---

This is a self note while taking the online course from:
**LinkedIn Learning: Learning Python** by _Joe Marini_
**LinkedIn Learning: Python Essential Training** by _Bill Weinman_

---

## 1. List, Tuple

- Lists are mutable, but tuples are **immutable**.

- using join function when printing elements:

```python
list_a = ['a', 'b', 'c']
print(', '.join(list_a))
```

```
(Result)

a, b, c
```

## 2. Dictionary

- Initializing dictionaries:

```python
# match each data in pairs in brackets {}
numbers = {'1': 'one', '2': 'two', '3': 'three'}

# use dict() function
nums = dict(one='1', two='2', three='3')
```

- Accessing keys and values, or both:

```python
nums = dict(one='1', two='2', three='3')

# key and value pairs
for k, v in nums.items():
    print(f'({k}, {v})')
print()

# only keys
for k in nums.keys():
    print(k)
print()

# only values
for v in nums.values():
    print(v)
print()

# access to a value
print(nums['one'])
nums['one'] = '1one1'
print(nums['one'])
```

```
(Result)

(one, 1)
(two, 2)
(three, 3)

one
two
three

1
2
3

1
1one1
```

## 3. Set

- Set does not allow duplicate, but **mutable**
- Strings can be stored as sets:

```python
a = set("My name is David Oh")
print(a)
print('\n\nsorted:')
print(sorted(a))
```

```
(Result)

{' ', 'v', 'y', 'd', 'e', 'D', 'n', 'O', 'm', 'h', 'M', 'a', 's', 'i'}

sorted:
[' ', 'D', 'M', 'O', 'a', 'd', 'e', 'h', 'i', 'm', 'n', 's', 'v', 'y']
```

- Set operators: -, &, |, ^(xor)

## 4. List Comprehension

```python
seq = range(11)
print(list(seq))
print()

# list comprehension
seq2 = [x*2 for x in seq]
print(seq2)

seq3 = [x for x in seq if x % 3 != 0]
print(seq3)
print()

# list of tuples
seq4 = [(x, x**2) for x in seq]
print(seq4)
print()

# dictionaries
seq5 = {x: x**2 for x in seq}
print(seq5)
print()

# sets
seq6 = {x for x in 'South Korea' if x in 'North Korea'}
print(seq6)
```

```
(Result)

[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

[0, 2, 4, 6, 8, 10, 12, 14, 16, 18, 20]
[1, 2, 4, 5, 7, 8, 10]

[(0, 0), (1, 1), (2, 4), (3, 9), (4, 16), (5, 25), (6, 36), (7, 49), (8, 64), (9, 81), (10, 100)]

{0: 0, 1: 1, 2: 4, 3: 9, 4: 16, 5: 25, 6: 36, 7: 49, 8: 64, 9: 81, 10: 100}

{'t', 'K', ' ', 'a', 'e', 'h', 'r', 'o'}
```
