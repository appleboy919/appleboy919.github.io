---
title: "[Python] #2 Python Functions"
excerpt: "Defining functions in Python"

categories:
  - Python
tags:
  - [Python, Python Function]

toc: true

date: 2021-02-18
last_modified_at: 2021-02-18
---

This is a self note while taking the online course from:

**LinkedIn Learning: Learning Python** by _Joe Marini_

**LinkedIn Learning: Python Essential Training** by _Bill Weinman_

---

## 1. Argument with default values

- args with default values have to be at the end

```python
def power(num, a=1):
  result = 1
  for i in range(a):
    result = result * num
  return result
```

## 2. Variable number of args

```python
def multi_add(*args):
  result = 0
  for x in args:
    result = result + x
  return result
```

## 3. List of args

- passing list, dictionareis as arg => **\*list**, **\*\*dict**

```python
# variable args for list
def arg_list(*args):
    if len(args):
        for s in args:
            print(s)
    else:
        print("Empty list")
    print()

# key-word arguments for dictionary
def kwarg_func(**kwargs):
    if len(kwargs):
        for k in kwargs:
            print('{}, {}'.format(k, kwargs[k]))
    else:
        print('empty dictionary')
    print()

# pass variables directly
arg_list(1, 2, 3)

# pass list, tuple as argument
x = (1, 3, 5, 7)
y = []
arg_list(x)
arg_list(*y)  # this is the right way

# pass pairs of data directly
kwarg_func(one='1', two='2', three='3')

# pass dict as argument
a = {'4': 'four', '5': 'five', '6': 'six'}
kwarg_func(**a)

# These raise an TypeError:
"""
kwarg_func(a)
kwarg_func(*a)
"""
```

```
Result:
1
2
3

(1, 3, 5, 7)

Empty list

one, 1
two, 2
three, 3

4, four
5, five
6, six

empty dictionary
```

## 4. Generator

- Generator is a special class of function that serves as an iterator (returns stream of values)
- Use "yield" keword

```python
# A generator which works as an inclusive range function
def inclusive_range(*args):
    numargs = len(args)
    start = 0
    step = 1

    # initialize parameters
    if numargs < 1:
        raise TypeError(f'expected at least 1 argument, got {numargs}')
    elif numargs == 1:  # ex. range(1) = 0, 1
        stop = args[0]
    elif numargs == 2:  # ex. range(1, 3) = 1, 2, 3
        (start, stop) = args
    elif numargs == 3:  # ex. range(1, 5, 2) = 1, 3, 5
        (start, stop, step) = args
    else:
        raise TypeError(f'expected at most 3 arguments, got {numargs}')

    # generator
    i = start
    while i <= stop:
        yield i
        i += step
```
