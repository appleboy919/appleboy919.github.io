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

result

```
def
1234
```

---

# 2. Functions
