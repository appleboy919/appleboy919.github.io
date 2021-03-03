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
nyd = date(today.year, 1, 1)

# use date comparison to see if New Year's has already gone for this year
# if it has, use the replace() function to get the date for next year
if nyd < today:
    print("New Year's day already went by %d days ago" %
            ((today-nyd).days))
    nyd = nyd.replace(year=today.year + 1)

# Now calculate the amout of time until New Year's Day
time_to_nyd = nyd-today
print("It's just", time_to_nyd.days, "days until New Year's Day")
```

```
(Result)

365 days, 5:01:00
today is : 2021-03-03 08:01:08.003646
one year from now is: 2022-03-03 08:01:08.003646
In 2 days and 3 week is: 2021-03-26 08:01:08.003646
One week ago, it was: Wednesday February 24, 2021

How many days until New Year's Day?
New Year's day already went by 61 days ago
It's just 304 days until New Year's Day
```

## 4. calendar module

- calendar module allows to output calendars with useful functions
- calendar.TextCalendar(calendar.\_\_\DAY): creates a text calendar each week starting with \_\_\_DAY
- can also create HTML calendar using _HTMLCalendar()_
- formatmonth(_year_,_month_,_w_,_l_): returns a month’s calendar in a multi-line string
- itermonthdays(_year_,_month_): iterate on days in a month (0 - overlapping days)
- month_name, day_name: returns names of days and months for the given locale

```python
# import the calendar module
import calendar

# create a plain text calendar
# c = calendar.TextCalendar(calendar.MONDAY)
c = calendar.TextCalendar(calendar.SUNDAY)
st = c.formatmonth(2021, 1, 0, 0)
print(st)

# create an HTML formatted calendar
hc = calendar.HTMLCalendar(calendar.SUNDAY)
st = hc.formatmonth(2021, 1)
print(st)

# loop over the days of a month
print('days in Jan 2021:')
for i in c.itermonthdays(2021, 1):
    print(i, end=' ')
print()

# months and days
for name in calendar.month_name:
    print(name, end=' ')
print()

for name in calendar.day_name:
    print(name, end=' ')
print()

# Calculate days based on a rule: For example, consider
# a team meeting on the first Friday of every month.
# To figure out what days that would be for each month,
# we can use this script:
print("Team meeting will be on: ")
for m in range(1, 13):
    cal = calendar.monthcalendar(2021, m)
    weekone = cal[0]
    weektwo = cal[1]

    if weekone[calendar.FRIDAY] != 0:
        meetday = weekone[calendar.FRIDAY]
    else:
        meetday = weektwo[calendar.FRIDAY]

    print("%10s %2d" % (calendar.month_name[m], meetday))
```

```
(Result)

    January 2021
Su Mo Tu We Th Fr Sa
                1  2
 3  4  5  6  7  8  9
10 11 12 13 14 15 16
17 18 19 20 21 22 23
24 25 26 27 28 29 30
31

<table border="0" cellpadding="0" cellspacing="0" class="month">
<tr><th colspan="7" class="month">January 2021</th></tr>
<tr><th class="sun">Sun</th><th class="mon">Mon</th><th class="tue">Tue</th><th class="wed">Wed</th><th class="thu">Thu</th><th class="fri">Fri</th><th class="sat">Sat</th></tr>
<tr><td class="noday">&nbsp;</td><td class="noday">&nbsp;</td><td class="noday">&nbsp;</td><td class="noday">&nbsp;</td><td class="noday">&nbsp;</td><td class="fri">1</td><td class="sat">2</td></tr>
<tr><td class="sun">3</td><td class="mon">4</td><td class="tue">5</td><td class="wed">6</td><td class="thu">7</td><td class="fri">8</td><td class="sat">9</td></tr>
<tr><td class="sun">10</td><td class="mon">11</td><td class="tue">12</td><td class="wed">13</td><td class="thu">14</td><td class="fri">15</td><td class="sat">16</td></tr>
<tr><td class="sun">17</td><td class="mon">18</td><td class="tue">19</td><td class="wed">20</td><td class="thu">21</td><td class="fri">22</td><td class="sat">23</td></tr>
<tr><td class="sun">24</td><td class="mon">25</td><td class="tue">26</td><td class="wed">27</td><td class="thu">28</td><td class="fri">29</td><td class="sat">30</td></tr>
<tr><td class="sun">31</td><td class="noday">&nbsp;</td><td class="noday">&nbsp;</td><td class="noday">&nbsp;</td><td class="noday">&nbsp;</td><td class="noday">&nbsp;</td><td class="noday">&nbsp;</td></tr>
</table>

days in Jan 2021:
0 0 0 0 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 0 0 0 0 0 0
 January February March April May June July August September October November December
Monday Tuesday Wednesday Thursday Friday Saturday Sunday
Team meeting will be on:
   January  1
  February  5
     March  5
     April  2
       May  7
      June  4
      July  2
    August  6
 September  3
   October  1
  November  5
  December  3
```

## 5. os module

- os module provides functions for interacting with the operating system
- commonly used functions:
  - os.name
  - path.exists/isfile/isdir/realpath/split
  - path.getmtime

```python
import os
from os import path
import datetime
from datetime import date, time, timedelta
import time

# print the name of the OS
print(os.name)

# check for item existence and type
print("Item exists: " + str(path.exists("textfile.txt")))
print("Itme is a file: " + str(path.isfile("textfile.txt")))
print("Item is a directory: " + str(path.isdir("textfile.txt")))

# work with file paths
print("Item path: " + str(path.realpath("textfile.txt")))
print("Item path and name: " + str(path.split(path.realpath("textfile.txt"))))

# get the modification time
# using time class to convert modification time
t = time.ctime(path.getmtime("textfile.txt"))
print(t)
# construct datetime object using fromtimestamp function
print(datetime.datetime.fromtimestamp(path.getmtime("textfile.txt")))

# calculate how long ago the tiem was modified
td = datetime.datetime.now(
) - datetime.datetime.fromtimestamp(path.getmtime("textfile.txt"))
print("It has been " + str(td)+" since the file was modified")
print("Or, " + str(td.total_seconds()) + " seconds")
```

```
(Result)

posix
Item exists: True
Itme is a file: True
Item is a directory: False
Item path: /PATH.../textfile.txt
Item path and name: ('/PATH...', 'textfile.txt')
Wed Mar  3 17:27:30 2021
2021-03-03 17:27:30.740000
It has been 0:00:25.315583 since the file was modified
Or, 25.315583 seconds
```

- Zip a file using shutil, zipfile module:

```python
import os
from os import path
import shutil
import datetime
from datetime import date, time, timedelta
import time
from shutil import make_archive
from zipfile import ZipFile


def main():
    # make a duplicate of an existing file
    if path.exists("textfile.txt"):
        # get the path to the file in the current directory
        src = path.realpath("textfile.txt")

        # let's make a backup copy by appending "bak" to the name
        dst = src + ".bak"

        # copy over the permissions, modification times, and other info
        shutil.copy(src, dst)  # copy the contents of a file
        shutil.copystat(src, dst)  # copy metadata from a file
        print(datetime.datetime.fromtimestamp(path.getmtime("textfile.txt")))
        print(datetime.datetime.fromtimestamp(
            path.getmtime("textfile.txt.bak")))

        # rename the original file
        # os.rename("textfile.txt", "newfile.txt")

        # now put things into a ZIP archive
        root_dir, tail = path.split(src)
        shutil.make_archive("archive", "zip", root_dir)

        # more fine-grained control over ZIP files
        with ZipFile("testzip.zip", "w") as newzip:
            newzip.write("textfile.txt")
            # testzip file will have only these two files
            newzip.write("textfile.txt.bak")


if __name__ == "__main__":
    main()
```

## 6. Creating Modules

```python
# 1. import other modules
# 2. create a class
'''
    doc string for description
'''

# 3. main, test function...
```
