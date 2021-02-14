---
title: "[Python] #1 Python Basics"
excerpt: "Basic tutorials using Python (Variables, functions, loop, class, modules)"

categories:
  - Python
tags:
  - [Python, Python Basics]

toc: true

date: 2021-01-16
last_modified_at: 2021-02-14
---

This is a self note while taking the online course from:

**LinkedIn Learning: Learning Python** by _Joe Marini_

**LinkedIn Learning: Python Essential Training** by _Bill Weinman_

---

# 1. Variables

```python
f = 1234 # global variable
def someFunction():
    f="def" # local variable
    print(f)

someFunction()
print(f)
```

Result:

```
def
1234
```

---

# 2. Functions

- Basic function

```python
def basic_func():
    print("This is basic function")
```

- Function with arguments

```python
def argument_func(arg1, arg2):
    print("This function takes", arg1, "and", arg2)
```

- Function that returns a value

```python
def cube(x):
    return x*x*x
```

- Function with default values for an argument

```python
def power(num, a=1): # a has a default value 1
    result = 1
    for i in range(a):
        result = result * num
    return result
```

- Function with variable number of arguments

```python
def multi_add(*args):
    result = 0
    for x in args:
        result = result + x
    return result
```

---

# 3. Conditional

- can assign values with conditional statements

```python
x = 10
y = 11
st = "x is less than y" if (x < y) else "x is greater than or the same as y"
print(st)
```

Result:

```
x is less than y
```

- is, in kewords

```python
# A is B
a = 1
b = 1
if a is b:
    print('a is b')
else:
    print('a is not b')

# a is in A
A = [1,2,3,4]
if 1 in A:
    print('1 is in A')
else:
    print('1 is not in A')
```

Result:

```
a is b
1 is in A
```

---

# 4. Loop

- enumerate() function for each index and value in a collection

```python
days = ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
for i, d in enumerate(days):
    print(i, d)
```

Result:

```
0 Mon
1 Tue
2 Wed
3 Thu
4 Fri
5 Sat
6 Sun
```

---

# 5. Numeric

1. float type --> sacrificing accuracty for precision
2. DO NOT USE FLOAT FOR ACCURACY ex) Money

- Problem with calculating float numbers

```python
x = .1 + .1 + .1 - .3  # in a real world, this should be zero
print('x is {}'.format(x))  # not actually zero (almost zero)
print(type(x))
```

```
x is 5.551115123125783e-17
<class 'float'>
```

- Use Decimal module for accurate calculation

```python
from decimal import *

# use modules for accuracy
a = Decimal('.10')
b = Decimal('.30')
y = a + a + a - b
print('y is {}'.format(y))
print(type(y))
```

```
y is 0.00
<class 'decimal.Decimal'>
```
