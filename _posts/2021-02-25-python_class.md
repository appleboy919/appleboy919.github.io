---
title: "[Python] #4 Python Class"
excerpt: "Defining class in python"

categories:
  - Python
tags:
  - [Python, Class]

toc: true

date: 2021-02-25
last_modified_at: 2021-02-25
---

This is a self note while taking the online course from:
**LinkedIn Learning: Learning Python** by _Joe Marini_
**LinkedIn Learning: Python Essential Training** by _Bill Weinman_

---

## 1. Class and class function

- _\_\_init\_\_(self, args...)_: constructor
- self keyword -> 'this' keyword in C/Java
- _\_\_str\_\_(self)_: provides string representation, allowing simply using print() method
- object variables: bounded to the object(**NOT CLASS**) ==> **ENCAPSULATION**

```python
class Animal:
    # class variables
    x = [1, 2, 3]

    # constructor
    def __init__(self, **kwargs):
        self._type = kwargs['type'] if 'type' in kwargs else 'Living thing'
        self._name = kwargs['name'] if 'name' in kwargs else 'No Name'
        self._sound = kwargs['sound'] if 'sound' in kwargs else '(Mute)'

    # provides string representation --> allows to simply use print() function
    def __str__(self):
        return f'Type: {self.type()}\tName: {self.name()}\tSound: {self.sound()}'

    # setter and getter
    def type(self, t=None):
        if t:
            self._type = t
        return self._type

    def name(self, n=None):
        if n:
            self._name = n
        return self._name

    def sound(self, s=None):
        if s:
            self._sound = s
        return self._sound


def print_animal(o):
    if not isinstance(o, Animal):
        raise TypeError('print_animal(): requires an Animal')
    print(f'Type: {o.type()}\tName: {o.name()}\tSound: {o.sound()}')


def main():
    a1 = Animal(type='Human', name='David', sound='Hu---man')
    print_animal(a1)
    print(a1.sound('Hello!'))
    print_animal(a1)
    a2 = Animal(type='Dog', name='Moly', sound='Woof-woof')
    print_animal(a2)
    a3 = Animal()
    print_animal(a3)
    print('using print function', a1)


if __name__ == '__main__':
    main()
```

```
(Result)

Type: Human Name: David Sound: Hu---man
Hello!
Type: Human	Name: David	Sound: Hello!
Type: Dog	Name: Moly	Sound: Woof-woof
Type: Living thing	Name: No Name	Sound: (Mute)
using print function Type: Human	Name: David	Sound: Hello!
```

## 2. Inheritance

- "class childClass(ParentClass)" => inherits parent class
- _super().\_\_init\_\_(args...)_: calls the parent's class constructor
- can extend built-in classes (ex. \_\_str\_\_)

```python
class Animal:
    # no default value for child classes
    def __init__(self, **kwargs):
        if 'type' in kwargs:
            self._type = kwargs['type']
        if 'name' in kwargs:
            self._name = kwargs['name']
        if 'sound' in kwargs:
            self._sound = kwargs['sound']

    def type(self, t=None):
        if t:
            self._type = t
        try:
            return self._type
        except AttributeError:
            return None

    def name(self, n=None):
        if n:
            self._name = n
        try:
            return self._name
        except AttributeError:
            return None

    def sound(self, s=None):
        if s:
            self._sound = s
        try:
            return self._sound
        except AttributeError:
            return None


class Duck(Animal):     # Duck inherits Animal class
    def __init__(self, **kwargs):
        self._type = 'duck'
        if 'type' in kwargs:
            del kwargs['type']
        super().__init__(**kwargs)

    def swim(self, s):  # Own function
        print(f'{self.name()} is swimming in {s}')


class Dog(Animal):      # Dog inherits Animal class
    def __init__(self, **kwargs):
        self._type = 'dog'
        if 'type' in kwargs:
            del kwargs['type']
        super().__init__(**kwargs)


def print_animal(o):
    if not isinstance(o, Animal):
        raise TypeError('print_animal(): requires an Animal')
    print(f'Type: {o.type()}\tName: {o.name()}\tSound: {o.sound()}')


def main():
    a0 = Duck(name='Donald', sound='Kwawk-kwawk')
    a1 = Dog(name='Moly', sound='Woof-woof')
    print_animal(a0)
    print_animal(a1)
    a0.swim('lake')


if __name__ == '__main__':
    main()
```

```
(Result)

Type: duck	Name: Donald	Sound: Kwawk-kwawk
Type: dog	Name: Moly	Sound: Woof-woof
Donald is swimming in lake
```

## 3. Iterator

- Iterator is a class that provides a sequence of items used in a loop (ex. range)
- \_\_\_iter\_\_\_ : identifies this object as an iterator object
- Loop uses \_\_next\_\_ for iteration
- _yield_ (generator) is a simpler way than iterators but iterators are still common

```python
# inclusinve range iterator
class inclusive_range:
    def __init__(self, *args):
        numargs = len(args)
        self._start = 0
        self._step = 1

        if numargs < 1:
            raise TypeError(f'expected at least 1 argument, got {numargs}')
        elif numargs == 1:
            self._stop = args[0]
        elif numargs == 2:
            (self._start, self._stop) = args
        elif numargs == 3:
            (self._start, self._stop, self._step) = args
        else:
            raise TypeError(f'expected at most 3 arguments, got {numargs}')

        self._next = self._start

    def __iter__(self):
        return self

    def __next__(self):
        if self._next > self._stop:
            raise StopIteration
        else:
            _r = self._next
            self._next += self._step
            return _r


def main():
    for n in inclusive_range(25):
        print(n, end=' ')
    print()

    for n in inclusive_range(2, 10, 2):
        print(n, end=' ')
    print()


if __name__ == '__main__':
    main()
```

```
(Result)

0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25
2 4 6 8 10
```
