---
title: "[Python] #1 Python Basics"
excerpt: "Basic tutorials using Python (Variables, functions, loop, class, modules)"

categories:
  - Python
tags:
  - [Python, Python Basics]

toc: true

date: 2021-01-16
last_modified_at: 2021-01-16
---

This is a self note while taking the online course from **LinkedIn Learning: Learning Python** by _Joe Marini_

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

result:

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
