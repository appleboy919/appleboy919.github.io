---
title: "[Python] #8 Python Buil-in Functions"
excerpt: "Built-in functions in Python"

categories:
  - Python
tags:
  - [Python, Built-in Function]

toc: true

date: 2021-02-28
last_modified_at: 2021-03-03
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

## 2. String Functions

- \_\_repr()\_\_: returns the best representation of an object
- print() calls \_\_str\_\_ first and if DNE, \_\_repr()\_\_
- ord(): returns the unicode code point representation

```python
class bunny:
    def __init__(self, n):
        self._n = n

    def __repr__(self):
        return f'repr: the number of bunnies is {self._n} 😷'

    def __str__(self) -> str:
        return f'str: the number of bunnies is {self._n}'


s = 'Hello world.'
print(repr(s))

# repr, str of a class object
x = bunny(47)
print(x)        # default: str
print(repr(x))  # repr: prints out the emoji
# ascii also calls repr, but escape values(Unicodes) are printed out
print('ascii=>', ascii(x))

# ascii vs chr
print(ord('😷'))
print(chr(128567))
```

```
(Result)

'Hello world.'
str: the number of bunnies is 47
repr: the number of bunnies is 47 😷
ascii=> repr: the number of bunnies is 47 \U0001f637
128567
😷
```

## 3. Container Functions

- common functions: len(), max(), sum(), reversed(), ...
- any(): returns True if any item are true
- all(): returns True when all items are true
- zip(): returns each items
- enumerate(): returns an index and a value

```python
x = (1, 2, 3, 4, 5)
print(x, len(x))
y = list(reversed(x))
for i in y:
    print(i)
sum = sum(x, 10)  # sum of x + 10

# any, all
print(any((0, 0, 0, 0)))
print(all((1, 1, 0)))

# zip returns each items
z = zip(x, y)
for a, b in z:
    print(f'{a} - {b}')

# enumerate returns an index and a value
x = ('cat', 'dog', 'rabbit', 'velociraptor')
for i, v in enumerate(x):
    print(f'{i}: {v}')
```

```
(Result)

(1, 2, 3, 4, 5) 5
5
4
3
2
1
False
False
1 - 5
2 - 4
3 - 3
4 - 2
5 - 1
0: cat
1: dog
2: rabbit
3: velociraptor
```
