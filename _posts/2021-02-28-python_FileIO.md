---
title: "[Python] #7 Python File I/O"
excerpt: "File I/O in Python"

categories:
  - Python
tags:
  - [Python, File I/O]

toc: true

date: 2021-02-28
last_modified_at: 2021-02-28
---

## 1. Open files

- open function returns a file object which is an **iterator**
- write mode(w) empties the file and **write over**
- 'b' - open as binary file (default is _text file_)

```python
f = open('line.txt', 'r')
    for line in f:
        print(line.rstrip())
```

```
(Result, line.txt)

1st line
2nd line
3rd line
4th line
5th line
```

## 2. Write text file

- can use print(_str_, file=_fileName_) fucntion to write into files
- **flush** output buffer for accuracy

```python
infile = open('line.txt', 'rt')

# new file object for output file (write-text mode)
outfile = open('line-copy.txt', 'wt')

# read and write each line in input file to output file
for line in infile:
    print(line.rstrip(), file=outfile) # strip from the end of string
    print('.', end='', flush=True)  # flush=True flushes the output buffer
outfile.close()     # buffering -> prevent data loss
print('\ndone.')
```

```
(Result)

.....
done.

```

```
(line-copy.txt)

1st line
2nd line
3rd line
4th line
5th line
```

## 3. Write(Copy) binary file

- code below copies a jpg file with write-binary mode:

```python
# open jpg file in binary file
infile = open('uw_madison.jpeg', 'rb')
outfile = open('uw-copy.jpeg', 'wb')
while True:
    buf = infile.read(10240)    # use 10KB = 10240 as the buffer
    if buf:
        outfile.write(buf)
        print('.', end='', flush=True)
    else:
        break
outfile.close()
print('\nDone.')
```
