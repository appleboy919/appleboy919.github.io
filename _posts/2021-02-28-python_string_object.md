---
title: "[Python] #6 Python String Objects"
excerpt: "Overview string objects in python"

categories:
  - Python
tags:
  - [Python, String]

toc: true

date: 2021-02-28
last_modified_at: 2021-02-28
---

This is a self note while taking the online course from:
**LinkedIn Learning: Learning Python** by _Joe Marini_
**LinkedIn Learning: Python Essential Training** by _Bill Weinman_

---

## 1. String

- strings are object in python and **immutable**.
- \_\_\_str\_\_\_: built-in function for each class that is used for string representation
- common functions for string object: +(concatenate), upper(), lower(), replace(), index(), ...

```python
# subclass of string object
class MyString(str):
    def __str__(self):
        return self[::-1]

s = 'hello'
print(f'{s} -> {MyString(s)}')
```

```
(Result)

hello -> olleh
```

## 2. String Formatting

- format(a0, a1, ...) function can be used with order of indices
- {str:[< or > with numbers]}: line up with the given number of whitespaces
- {number:,}: add comma(,) on the given number
- {float:.(num)f}: print the given number of floating points
  -{:o / b}: hexadecimal/binary

```python
x = 42
y = 73

# string interpolation
print('the number is {} {}'.format(x, y))
print('numbers: {xx} {bb}'.format(xx=x, bb=y))
print('numbers: {0} {1} {0}'.format(x, y))

# order formatting ':' '+' ',' '._f'
print('numbers: {0:<5}. {1:>5}'.format(x, y))
print('numbers: {0:<5}. {1:>+05}'.format(x, y))
print('{:,}'.format(x*y*1298).replace(',', '.'))
print('number is {:.3f}'.format(x*y))
print('hexadecimal: {:o}\tbinary:{:b}'.format(x, x))

# F string formatting
print(f'the number is {x:.3f}')
```

```
(Result)

the number is 42 73
numbers: 42 73
numbers: 42 73 42
numbers: 42   .    73
numbers: 42   . 00+73
3.979.668
number is 3066.000
hexadecimal: 52	binary:101010
the number is 42.000
```

## 3. Split & Join

- _split()_: split words with spaces and new lines
- _join()_: concats list or tuples of strings with the given arg

```python
# split
s = 'this is a long string with a bunch of words in it.'
l = s.split()
print(l)
print(s.split('i'))

# join
s2 = ':'.join(l)
print(s2)
```

```
(Result)

['this', 'is', 'a', 'long', 'string', 'with', 'a', 'bunch', 'of', 'words', 'in', 'it.']
['th', 's ', 's a long str', 'ng w', 'th a bunch of words ', 'n ', 't.']
this:is:a:long:string:with:a:bunch:of:words:in:it.
```
