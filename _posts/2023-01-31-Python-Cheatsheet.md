---
title: "Python-Cheatsheet"
date: 2023-01-31
layout: default
---

https://www.geeksforgeeks.org/differences-and-applications-of-list-tuple-set-and-dictionary-in-python/

# Python Data Structures

## List ```[1,2,3,4,5]```
* like an array
* allow duplicates

## Tuple `````(1,2,3,4,5)`````
* more like an array of constants
* allow duplicate elements

## Dictionary `````{1:"a", 2:"b"}`````
* ordered key-value pairs
* does not allow duplicate keys

## Set `````{1,2,3,4,5}`````
* will not allow duplicate elements



## ```if __name__=='__main__' ```
* this code only gets run if this file is executed directly and not used in an import
* 


## Keyword arguments 
```def add_suffix(suffix='.com'):```

## **kwargs - keyword arguments
```def convert_and_sum_list_kwargs(usd_list, **kwargs):```
* can be accessed as a dictionary
* commonly used when passing to another function


## using % in a string
```name = "Geek"```
# append a string within a string
```print("Hey, %s!" % name)```


## scope
* use the global keyword to use globals
```global score```
* * use the nonlocal to get it from the scope above
```nonlocal score```

## lambdas
```add_up = lambda x, y: x + y
print(add_up(2, 5))
```

### mapping with lambdas
* first argument is function to apply
* second is an iterable

```lengths = list(map(len, names)```
* (map returns a generator)

# generator
a function which uses yield to return a series of results which change each time it is called

## filter() is similar - takes a function and an iterable
```names = ['Josefina', 'Jim', 'Kim']
list(filter(lambda name: len(name) == 3, names))
```

## and sorted()
```
names = ['Ming', 'Jennifer', 'Andrew', 'Boris']
sorted(names, key=lambda x : len(x))
```

# Objects
## view properties and methods
```test.__dir__()```

## Classes
```
class Australian
    is_human = True
    enjoys_sport = True
    
john = Australian()
type(John)
john.is_human
```

### Constructors
```
def __init__(self, height):
    self.height = height
```

### To get attributes of object:
```usa.__dict__```

## Methods
### Instance
```
def area(self):
    
```
### Static
```
@staticmethod
def format_date(date):
#can only access what is passed
```
### Class - can be used to instantiate
can access class level variables
```
@classmethod
def is_sporty_human(cls):
```
### The str method - when you print(instance)
```
def __str__(self):
```

## The property decorator
```
@property
def fahrenheit(self):
    return self.celsius * 9 / 5 + 32
```
Can now use this as an attribute:
```
freezing.fahrenheit #do need for ()
```

## The setter method - update multiple attributes simultaneously
```
@full_name.setter
def full_name(self, name):
    first, last = name.split(' ')
    self.first_name = first
    self.last_name = las
```

*Can also be used for validation* (ValueError?)

## Inheritance

```
class Pet:
    def __init__(self, name, weight):
        self.name = name
        self.weight = weight

class Cat(Pet)
    is_feline = True

```

## Overridding



## Calling the parent method with super()
```
super().speak()
```

# The Standard Library
## Working with dates and times


## Dates and Times
```
    from datetime import date, time, datetime
    date(year=2020, month=1, day=31)
    # datetime.date(2020, 1, 31)
    
    time(hour=13, minute=14, second=31)
    #datetime.time(13, 14, 31)
    
    datetime(year=2020, month=1, day=31, hour=13, minute=14, second=31)
    # datetime.datetime(2020, 1, 31, 13, 14, 31)
```

```
date.today()
datetime.now()
datetime.combine()
date.fromisoformat("2020-01-31")
```


Can use  srtptime for different formats:
```
date_string = "01-31-2020 14:45:37"
format_string = "%m-%d-%Y %H:%M:%S"
datetime.strptime(date_string, format_string)
```

## Working with time zones

* datetime provides tzinfo 
* allows datetime.datetime and datetime.time to include timezones information
* also need python-dateutil

```
from dateutil import tz
from datetime import datetime

now = datetime.now(tz=tz.tzlocal())
now
datetime.datetime(2020, 1, 26, 0, 55, 3, 372824, tzinfo=tzlocal())
now.tzname()
'Eastern Standard Time'


```


## Using collections in Python

### The counter class
* counts hashable objects
* has keys and values

```
Counter('abracadabra').most_common(3)
```

### The defaultdict class
* defaultdict is a Python type that inherits from dict:

```python
def_dict = defaultdict(list)  # Pass list to .default_factory
def_dict['one'] = 1  # Add a key-value pair
```

### The ChainMap class

### functools