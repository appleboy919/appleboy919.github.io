---
title: "[Python] #8 Python Buil-in Functions"
excerpt: "Built-in functions in Python"

categories:
  - Python
tags:
  - [Python, Built-in Function]

toc: true

date: 2021-02-28
last_modified_at: 2021-02-28
---

This is a self note while taking the online course from:
**LinkedIn Learning: Learning Python** by _Joe Marini_
**LinkedIn Learning: Python Essential Training** by _Bill Weinman_

---

## 1. Numeric Functions

- complex(float, comp) -> also use _x + yj_
- abs(): returns an absolute value
- divmod(x, y): returns a tuple of quotient, remainder

```python
x = '47'
y = int(x)
z = float('-32.2')
absZ = abs(z)
divMod = divmod(y, 3)
comp1 = y + 17j
comp2 = complex(y, 3)

print(f'x is {type(x)}')
print(f'x is {x}')
print(f'y is {type(y)}')
print(f'y is {y}')
print(f'z is {type(z)}')
print(f'z is {z}')
print(f'absZ is {type(absZ)} {absZ}')
print(f'divMod is {type(divMod)} {divMod}')
print(f'divMod is {type(comp1)} {comp1}')
print(f'divMod is {type(comp2)} {comp2}')
```

```
(Result)

x is <class 'str'>
x is 47
y is <class 'int'>
y is 47
z is <class 'float'>
z is -32.2
absZ is <class 'float'> 32.2
divMod is <class 'tuple'> (15, 2)
divMod is <class 'complex'> (47+17j)
divMod is <class 'complex'> (47+3j)
```
