---
title: "[Python] #5 Python Exception Handling"
excerpt: "Handling exceptions and reporting errors"

categories:
  - Python
tags:
  - [Python, Exception]

toc: true

date: 2021-02-28
last_modified_at: 2021-02-28
---

This is a self note while taking the online course from:
**LinkedIn Learning: Learning Python** by _Joe Marini_
**LinkedIn Learning: Python Essential Training** by _Bill Weinman_

---

## Exception

- try -> except \_\_\_Error -> except -> else (NO Errors)
- use sys.exc_info()[1] for details about an error
- to raise error(exception): use 'raise' keyword

```python
import sys

try:
    # codes that might raise exceptions

    # Code below raise exception
    """
    raise TypeError('raised TypeError intenionally')
    """
except Error_Name (as e):
    print(f'caught {e}')
except:
    # other exceptions
    print(f'unkonwn error: {sys.exc_info()[1]}')
else:
    # No error raised!
```
