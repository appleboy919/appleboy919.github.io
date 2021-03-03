---
title: "[Python] #9 Python Modules"
excerpt: "Commonly used modules and creating modules in Python"

categories:
  - Python
tags:
  - [Python, Module]

toc: true

date: 2021-03-03
last_modified_at: 2021-03-03
---

This is a self note while taking the online course from:
**LinkedIn Learning: Learning Python** by _Joe Marini_
**LinkedIn Learning: Python Essential Training** by _Bill Weinman_

---

## 1. datetime - date, datetime class

- date.today(): returns today's date as Date object
- .day, .month, .year, .weekday()
- datetime.now(): returns today's datetime object(class)

```python
from datetime import date
from datetime import time
from datetime import datetime

# DATE OBJECTS
# Get today's date
today = date.today()
print("Today's date is", today)

# print out the date's individual components
print("Date components:", today.day, today.month, today.year)

# retrieve today's weekday (0=Monday, 6=Sunday)
print("Today's weekday # is:", today.weekday())
days = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"]
print("Which is a:", days[today.weekday()])

# DATETIME OBJECTS
# Get today's date from the datetime class
today = datetime.now()
print("The current date and time is", today)

# Get the current time
t = datetime.time(today)
print(t)
```

```
(Result)

Today's date is 2021-03-03
Date components: 3 3 2021
Today's weekday # is: 2
Which is a: Wed
The current date and time is 2021-03-03 07:41:25.286398
07:41:25.286398
```

## 2. Time Formatting

- strftime(_date_): returns a string representation of a date
- Date formatting:
  - %y/%Y: year (abrv/full)
  - %a/%A: weekday (abrv/full)
  - %b/%B: month (abrv/full)
  - %d: day of month
  - %c: locale's date and time
  - %x: locale's date
  - %X: locale's time
- Time formatting:
  - %I/%H: 12/24 Hour
  - %M: minute
  - %S: second
  - %p: locale's AM/PM

```python
from datetime import datetime

# Times and dates can be formatted using a set of predefined string
# control codes
now = datetime.now()

#### Date Formatting ####

# %y/%Y - year, %a/%A - weekday, %b/%B - month, %d - day of month
print(now.strftime("The current year is: %Y"))
print(now.strftime("%a, %d %B, %y"))

# %c - locale's date and time, %x - locale's date, %X - locale's time
print(now.strftime("Locale date and time: %c"))
print(now.strftime("Locale date: %x"))
print(now.strftime("Locale time: %X"))

#### Time Formatting ####

# %I/%H - 12/24 Hour, %M - minute, %S - second, %p - locale's AM/PM
print(now.strftime("Current time: %I:%M:%S %p"))
print(now.strftime("24-hour time: %H:%M"))
```

```
(Result)

The current year is: 2021
Wed, 03 March, 21
Locale date and time: Wed Mar  3 07:57:27 2021
Locale date: 03/03/21
Locale time: 07:57:27
Current time: 07:57:27 AM
24-hour time: 07:57
```

## 3. datetime - timedelta class

- timedelta class allows to compute time easily
- timedelta(days=,hours=,minutes=,...)
-

```python
from datetime import date
from datetime import time
from datetime import datetime
from datetime import timedelta

# construct a basic timedelta and print it
print(timedelta(days=365, hours=5, minutes=1))

# print today's date
now = datetime.now()
print("today is : "+str(now))

# print today's date one year from now
print("one year from now is: " + str(now+timedelta(days=365)))

# create a timedelta that uses more than one argument
print("In 2 days and 3 week is: " + str(now + timedelta(days=2, weeks=3)))

# calculate the date 1 week ago, formatted as a string
t = datetime.now() - timedelta(weeks=1)
s = t.strftime("%A %B %d, %Y")
print("One week ago, it was: "+s)

### How many days until New Year's Day? ###
print("\nHow many days until New Year's Day?")
today = date.today()
afd = date(today.year, 1, 1)

# use date comparison to see if New Year's has already gone for this year
# if it has, use the replace() function to get the date for next year
if afd < today:
    print("New Year's day already went by %d days ago" %
            ((today-afd).days))
    afd = afd.replace(year=today.year + 1)

# Now calculate the amout of time until New Year's Day
time_to_afd = afd-today
print("It's just", time_to_afd.days, "days until New Year's Day")
```
