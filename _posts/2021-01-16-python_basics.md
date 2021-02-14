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

---

# 6. Sequence Type

- List

```python
x = [1, 2, 3, 4]  # list is created with [] brackets
x[0] = 0  # list is mutable
for i in x:
    print("i is {}".format(i))
print("list x is {}".format(x))
```

- Tuple

```python
y = (1, 2, 3, 4)  # tuple is created with () parentheses
for j in y:
    print("j is {}".format(j))
print("tuple y is {}".format(y))

y[0] = 0  # this line is an error -> tuple is immutable
```

- range()

```python
z = range(5)  # range function creates a sequence from 0 to n-1

for k in z:
    print("k is {}".format(k))

print("range(5, 30, 5) is {}".format(range(5, 30, 5)))

z[0] = 0 # this line is also an error -> range sequence is immutable
```

- Accessing specific range of sequence

```python
SSN = "12121515"

print("first four digit: " + SSN[:4])
print("last four digit: " + SSN[-4:])
print("except last two digit: " + SSN[:-2])
```

```
(Result)

first four digit: 1212
last four digit: 1515
except last two digit: 121215
```

- Dictionary

```python
# dictionary: searchable sequence with key value pairs
w = {'one': 1, 'two': 2, 'three': 3, 'four': 4}

# prints only keys
for l in w:
    print('l is {}'.format(l))

# prints out tuple of key and value
for k, v in w.items():
    print('k: {}, v: {}'.format(k, v))

# dictionary is mutable
w['one'] = 101
print('dictionary is mutable:')
print('k: one, v: {}'.format(w['one']))
```

```
(Result)

l is one
l is two
l is three
l is four
k: one, v: 1
k: two, v: 2
k: three, v: 3
k: four, v: 4
dictionary is mutable:
k: one, v: 101
```

---

# 7. Object

```python
class Dog:
    sound = "Woof-Woof"
    walking = "Walks like a dog"

    # self = reference keyword for object
    def bark(self):
        print(self.sound)

    def walk(self):
        print(self.walking)


def main():
    moly = Dog()
    moly.bark()
    moly.walk()


if __name__ == "__main__":
    main()
```
