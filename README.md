nah [![PyPI version](https://badge.fury.io/py/nah.svg)](https://badge.fury.io/py/nah)
=====================
[![Build Status](https://travis-ci.com/onchie/nah.svg?branch=master)](https://travis-ci.com/onchie/nah)

A tiny collection of simple error handling decorators.

Usage
-----

Ignoring exception

```python
import nah

@nah.meh
def check_age(age):
    if age < 18:
        raise UnderAgeException

check_age(17)  # returns None
```
Returning a value
```python
import nah

@nah.gimme(0)
def divide_by(n):
    return 100 / n

divide_by(0) # returns 0 instead of raising ZeroDivisionError
```
Retry
```python
@nah.again(3)
def connect_db(config):
    return DbConnection.connect(config)
```
Alternative function
```python
def alternative_func(a, b):
    return safe_divide(a, b)

@nah.maybe(alternative_func)
def my_func(a, b):
    return a / b

@nah.maybe(alternative_func, when=ZeroDivisionError)
def my_func(a, b):
    return a / b

```

Copyright
---------

`nah` is an open source project by `Onchie Cantillo`_. See the license_ file
for more information.
