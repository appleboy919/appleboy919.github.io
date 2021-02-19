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
