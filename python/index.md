[[Return to Index]](../README.md)

# Python Quick Start Guide
This guide will walk you through the basics of Python 3.x.

## Table of Contents
- [Console Input/Output](#console-inputoutput)
- [Data Types](#data-types)
  - [Variable Declaration and Instantiation](#variable-declaration-and-instantiation)
  - [Destructuring](#destructuring)
  - [Type Checking](#type-checking)
  - [Type Conversion](#type-conversion)
  - [Deleting Variables](#deleting-variables)
- [Operators](#operators)
  - [Arithmetic Operators](#arithmetic-operators)
  - [Comparison Operators](#comparison-operators)
  - [Logical Operators](#logical-operators)
- [Control Structures](#control-structures)
  - [`if...else`](#ifelse)
  - [`if...else` ternary operator](#ifelse-ternary-operator)
  - [`match` block](#match-block)
  - [`for...in`](#forin)
    - [`range()`](#range)
  - [`while`](#while)
  - [`break`](#break)
  - [`continue`](#continue)
- [Strings](#strings)
- [Data Structures](#data-structures)
- [Lists](#lists)
  - [Check if a value exists in a list](#check-if-a-value-exists-in-a-list)
  - [Iterate through a list](#iterate-through-a-list)
  - [Comparing Lists](#comparing-lists)
  - [Merging Lists](#merging-lists)
  - [List Unpacking](#list-unpacking)
  - [List Methods](#list-methods)
  - [Slicing](#slicing)
  - [Deleting Lists](#deleting-lists)
  - [List Comprehension](#list-comprehension)
- [Dictionaries](#dictionaries)
  - [Check if a key exists in a dictionary](#check-if-a-key-exists-in-a-dictionary)
  - [Iterate through a dictionary](#iterate-through-a-dictionary)
  - [Unpacking Dictionary](#unpacking-dictionary)
  - [Dictionary Methods](#dictionary-methods)
  - [Deleting Dictionaries](#deleting-dictionaries)
  - [Dictionary Comprehension](#dictionary-comprehension)
- [Tuples](#tuples)
  - [Check if a value exists in a tuple](#check-if-a-value-exists-in-a-tuple)
  - [Iterate through a tuple](#iterate-through-a-tuple)
  - [Comparing Tuples](#comparing-tuples)
  - [Merging Tuples](#merging-tuples)
  - [Tuple Unpacking](#tuple-unpacking)
  - [Tuple Methods](#tuple-methods)
- [Sets](#sets)
  - [Iterate through a set](#iterate-through-a-set)
  - [Set Methods](#set-methods)
  - [Set Operations](#set-operations)
  - [Set Comprehension](#set-comprehension)
- [Functions](#functions)
  - [Default Parameters](#default-parameters)
  - [Keyword Arguments](#keyword-arguments)
  - [Positional-Only Arguments](#positional-only-arguments)
  - [Keyword-Only Arguments](#keyword-only-arguments)
  - [Scope](#scope)
  - [`global` keyword](#global-keyword)
  - [`nonlocal` keyword](#nonlocal-keyword)
  - [`*args` operator](#args-operator)
  - [`**kwargs` operator](#kwargs-operator)
  - [Parameter ordering](#parameter-ordering)
  - [Tuple and List Unpacking](#tuple-and-list-unpacking)
  - [Dictionary Unpacking](#dictionary-unpacking)
  - [Higher-order functions](#higher-order-functions)
  - [Docstrings](#docstrings)
- [Lambda](#lambda)
- [Built-in Functions](#built-in-functions)
  - [`map()`](#map)
  - [`filter()`](#filter)
  - [`all()`](#all)
  - [`any()`](#any)
  - [`sorted()`](#sorted)
  - [`min()` and `max()`](#min-and-max)
  - [`reversed()`](#reversed)
  - [`abs()`](#abs)
  - [`sum()`](#sum)
  - [`round()`](#round)
  - [`zip()`](#zip)
- [Debugging and Error Handling](#debugging-and-error-handling)
  - [Common Exceptions](#common-exceptions)
  - [`raise`](#raise)
  - [`try...except`](#tryexcept)
  - [`try...except...else`](#tryexceptelse)
  - [`finally` block](#finally-block)
  - [Trace Debugging with `pdb`](#trace-debugging-with-pdb)
- [Modules](#modules)
  - [Importing Modules](#importing-modules)
  - [Custom Modules](#custom-modules)
  - [Nested Modules](#nested-modules)
  - [Module Resolution](#module-resolution)
  - [`__name__` variable](#__name__-variable)
  - [Runnable Python](#runnable-python)
  - [Installing Third-Party Modules with `pip`](#installing-third-party-modules-with-pip)
  - [Packages](#packages)
- [Classes and Objects](#classes-and-objects)
  - [Define a class](#define-a-class)
  - [Class Attributes](#class-attributes)
  - [Class Methods](#class-methods)
  - [`__repr__()` magic method](#__repr__-magic-method)
  - [Class Getter and Setter](#class-getter-and-setter)
  - [Inheritance](#inheritance)
  - [Invoking parent constructor](#invoking-parent-constructor)
  - [Multiple Inheritance](#multiple-inheritance)
  - [Method Resolution Order (MRO)](#method-resolution-order-mro)
  - [Magic Methods](#magic-methods)
  - [Abstract Classes](#abstract-classes)
- [Enums](#enums)
    - [Auto-generated enum values](#auto-generated-enum-values)    
- [Iterators and Iterables](#iterators-and-iterables)
- [Generators](#generators)
  - [Generator Functions](#generator-functions)
  - [Generator Expressions](#generator-expressions)
- [Decorators](#decorators)
  - [Decorators with Variable Argument Support](#decorators-with-variable-argument-support)
  - [Preserving Metadata in Decorators](#preserving-metadata-in-decorators)
  - [Decorators with Arguments](#decorators-with-arguments)
- [Type Hinting and Annotations](#type-hinting-and-annotations)
  - [Install `mypy`](#install-mypy)
  - [Enable VSCode Support for `mypy`](#enable-vscode-support-for-mypy)
  - [Basic Type Annotation](#basic-type-annotation)
  - [List Annotation](#list-annotation)
  - [Tuple Annotation](#tuple-annotation)
  - [Dictionary Annotation](#dictionary-annotation)
  - [Set Annotation](#set-annotation)
  - [Function Annotation](#function-annotation)
  - [Optional Argument Annotation](#optional-argument-annotation)
  - [`Any` type Annotation](#any-type-annotation)
  - [Union Type Annotation](#union-type-annotation)
  - [Custom Type Annotation](#custom-type-annotation)
  - [Sequence Type Annotation](#sequence-type-annotation)
  - [Callable Type Annotation](#callable-type-annotation)
  - [Generics Annotations](#generics-annotations)
- [Dataclasses](#dataclasses)
  - [Converting Dataclasses to `dict` and `tuple`](#converting-dataclasses-to-dict-and-tuple)
  - [Immutable Dataclasses](#immutable-dataclasses)
  - [Ordered Dataclasses](#ordered-dataclasses)
  - [Default Values for Mutable Fields](#default-values-for-mutable-fields)
- [Testing](#testing)
  - [Assertions](#assertions)
  - [Doctest](#doctest)
  - [Unit Testing](#unit-testing)
  - [`setUp()` and `tearDown()`](#setup-and-teardown)
- [File Operations](#file-operations)
  - [Reading](#reading)
  - [Moving Cursor](#moving-cursor)
  - [Read Line](#read-line)
  - [Read All Lines](#read-all-lines)
  - [Check File Handler State](#check-file-handler-state)
  - [Closing Files using `with`](#closing-files-using-with)
  - [Writing](#writing)
  - [Truncating](#truncating)
- [CSV File Processing](#csv-file-processing)
  - [Reading with `reader`](#reading-with-reader)
  - [Writing with `writer`](#writing-with-writer)
  - [Reading with `DictReader`](#reading-with-dictreader)
  - [Writing with `DictWriter`](#writing-with-dictwriter)
- [Serialization with `pickle`](#serialization-with-pickle)
- [Serialization with JSON](#serialization-with-json)
  - [Encoding JSON](#encoding-json)
  - [Decoding JSON](#decoding-json)
- [Asynchronous Programming](#asynchronous-programming)
  - [Coroutines](#coroutines)
  - [Event Loop](#event-loop)
  - [`await` keyword](#await-keyword)
  - [Futures](#futures)
  - [Creating tasks](#creating-tasks)
  - [Threading with async](#threading-with-async)
- [`pip` Package Manager](#pip-package-manager)
  - [`pip list`](#pip-list)
  - [`pip freeze`](#pip-freeze)
  - [`pip show`](#pip-show)
  - [`pip install`](#pip-install)
  - [`pip uninstall`](#pip-uninstall)
  - [Get `pip` version](#get-pip-version)
  - [Upgrade `pip` version](#upgrade-pip-version)
- [Virtual Environment with `venv`](#virtual-environment-with-venv)
  - [Create environment](#create-environment)
  - [Activate environment](#activate-environment)
- [Dependency Management with `pipenv`](#dependency-management-with-pipenv)
  - [Install `pipenv`](#install-pipenv)
  - [Install dependency](#install-dependency)
  - [Synchronize virtual environment](#synchronize-virtual-environment)
  - [Update dependency](#update-dependency)
  - [Uninstall dependency](#uninstall-dependency)
  - [Activate virtual environment](#activate-environment)
  - [Import from `requirements.txt`](#import-from-requirementstxt)
  - [Show dependency graph](#show-dependency-graph)
  - [Check security vulnerabilities](#check-security-vulnerabilities)

## Console Input/Output
- Output
  ```python
  print('Hello World')
  print('Hello', 'World')   # print() also supports multiple arguments
  ```
- Input
  ```python
  age = input('How old are you? ')
  ```
[[Go back]](#table-of-contents)

## Data Types
Here are some of the most commonly used data types in Python.

| Data Type      | Example                                     | 
| -------------- | ------------------------------------------- | 
| `int`          | `32`                                        | 
| `float`        | `4.86`                                      | 
| `bool`         | `True`                                      | 
| `str`          | `'Hello'`                                   | 
| `list`         | `['apples', 'oranges', 'grapes']`           | 
| `dict`         | `{'name': 'John Doe', 'age': 21}`           | 
| `tuple`        | `('male', 'female')`                        | 
| `set`          | `{'Davao', 'Cebu', 'Manila', 'Baguio'}`     | 
| `function`     | `def hello(): pass`                         | 
| `NoneType`     | `None`                                      | 

Data types as displayed by `type()`
```python
print(type(32))                                       # <class 'int'>
print(type(4.86))                                     # <class 'float'>
print(type(True))                                     # <class 'bool'> 
print(type('Hello'))                                  # <class 'str'> 
print(type(['apples', 'oranges', 'grapes']))          # <class 'list'> 
print(type({'name': 'John Doe', 'age': 21}))          # <class 'dict'> 
print(type(('male', 'female')))                       # <class 'tuple'>
print(type({'Davao', 'Cebu', 'Manila', 'Baguio'}))    # <class 'set'>
print(type(None))                                     # <class 'NoneType'>
```

[Functions](#functions) and [Lambdas](#lambda) are grouped under the `function` data type and they can be [passed around](#higher-order-functions) just like any other data types.
```python
def foo(): pass         # Function
bar = lambda: True      # Lambda

print(type(foo))        # <class 'function'>
print(type(bar))        # <class 'function'>

# test for function/lambda
print(callable(foo))    # True
print(callable(bar))    # True
```
[[Go back]](#table-of-contents)

### Variable Declaration and Instantiation
In Python, variables are created the moment they are assigned a value. No need to declare or specify the data type.
```python
# This creates 'age' variable with an 'int' data type.
age = 21

# Multiple assignment with tuple destructuring
first_name, last_name = 'John', 'Doe'
```
[[Go back]](#table-of-contents)

### Destructuring
You can also create variables through destructuring. This is useful if you want to extract values from [tuples](#tuples) and [lists](#lists).

Destructuring with lists
```python
user_info = ['John Doe', 21, 'male']
full_name, age, gender = user_info

print(type(user_info))  # <class 'list'>
print(f'{full_name}, {age}, {gender}')
# John Doe, 21, male
```

Destructuring with tuples
```python
user_info = ('John Doe', 21, 'male')
full_name, age, gender = user_info

print(type(user_info))  # <class 'tuple'>
print(f'{full_name}, {age}, {gender}')
# John Doe, 21, male
```

### Type Checking
Use `type()` to check the data type of a variable
```python
message = 'Hello World'
print(type(message))      # Output: <class 'str'>
```
To compare types, use `is` and `is not` identity operators
```python
some_value = 'hello'
if type(some_value) is str:
    print('The value is a string')

if type(some_value) is not list:
    print('The value is not a list')
```
[[Go back]](#table-of-contents)

### Type Conversion
Python allows you to convert values from one data type to another.
```python
some_int = '24'
print(int(some_int))      # convert to int

some_float = '19.22'
print(float(some_float))  # convert to float

to_text = 88
print(str(to_text))       # convert to str
```
[[Go back]](#table-of-contents)

### Deleting Variables
To remove a variable from the current scope, use the `del` statement.
```python
greeting = 'Hello World'
print(greeting)     # Hello World

del greeting
print(greeting)
# NameError: name 'greeting' is not defined
```
[[Go back]](#table-of-contents)

## Operators
### Arithmetic Operators
| Operator | Name                         |
|----------|------------------------------|
| `+`      | addition                     | 
| `-`      | subtraction                  |
| `*`      | multiplication               |
| `/`      | division                     |
| `//`     | integer division             |
| `**`     | exponentation                |
| `%`      | modulo                       |

[[Go back]](#table-of-contents)


### Comparison Operators
| Operator | Name                         |
|----------|------------------------------|
| `==`     | equal                        | 
| `!=`     | not equal                    |
| `>`      | greater than                 |
| `<`      | less than                    |
| `>=`     | greater than or equal to     |
| `<=`     | less than or equal to        |
| `is`     | points to same object        |
| `is not` | points to diff object        |

[[Go back]](#table-of-contents)

### Logical Operators
| Operator | Name                         |
|----------|------------------------------|
| `and`    | AND operator                 | 
| `or`     | OR operator                  |
| `not`    | NOT operator                 |

[[Go back]](#table-of-contents)

## Control Structures
### `if...else`
Execute statements based on a conditional expression. You can use `and`, `or`, and `not` to group multiple conditions. Use indentation to group statements inside the block.
```python
age = 31
if age < 18:
    print('Child fare')
elif age >= 19 and age <= 60:
    print('Regular fare')
else:
    print('Senior fare')

# Use `pass` to indicate empty block
if True:
    pass
```
[[Go back]](#table-of-contents)

### `if...else` ternary operator
Assign values based on a condition. This is analogous to `?:` ternary operators in other programming languages.
```python
age = 17
status = 'minor' if age < 18 else 'adult'
print(status)   # minor
```
[[Go back]](#table-of-contents)

### `match` block
To do multiple comparisons with the same variable, you may use the `match` block. They are analogous to switch statements in other programming languages. Use `|` to perform `or` comparison and `_` for the default case.
```python
fruit = input('Select fruit: ')

match fruit:
    case 'apple':
        print('The fruit is red')

    case 'mandarin' | 'orange':
        print('The fruit is orange')

    case 'banana':
        print('The fruit is yellow.')

    case _:
        print('Unknown input')
```
[[Go back]](#table-of-contents)

### `for...in`
Loops through an iterable value
```python
# Print each letter in a string
some_text = 'hello'
for letter in some_text:
    print(letter)

# Print numbers from 1-9
for number in range(1, 10):
    print(number)

# Print each item in a list
davao_places = ['Ecoland', 'Toril', 'Panabo', 'Buhangin', 'Calinan']
for route in davao_places:
    print(route)
```
[[Go back]](#table-of-contents)

#### `range()`
Generate an iterable sequence of numbers. Typically used on `for...in` loops.
```python
# Syntax
range(initial_value, stop, increment)

# Examples
range(10)         # range of numbers from 0 to 9
range(5, 31)      # range of numbers from 5 to 30
range(2, 51, 2)   # range of even numbers from 2 to 50
```
[[Go back]](#table-of-contents)

### `while`
Repeatedly execute a block for as long as the condition is `True`
```python
# Print num from 0-9
num = 0
while num < 10:
    print(num)
    num += 1
```
[[Go back]](#table-of-contents)

### `break`
Exit out of the loop
```python
# Print num from 0 to 4
for num in range(9):
    if num == 5:
        break
    print(num)

# Same code but with the `while` loop
num = 0
while True:
    if num == 5:
      break
    print(num)
    num += 1
```
[[Go back]](#table-of-contents)

### `continue`
Skip over a loop and proceed to the next iteration. Also works with `while` loops
```python
# Print num from 0 to 8, skipping 5
for num in range(9):
    if num == 5:
      continue
    print(num)
```

[[Go back]](#table-of-contents)

## Strings
String is a data type used for representing text.
```python
# Single or double quotes
print('Single quotes')
print("Double quotes")

# String concatenation
first_name = 'John'
last_name = 'Doe'
print('My name is ' + first_name + ' ' + last_name)   # My name is John Doe

# String interpolation with F-Strings
name = 'John Doe'
print(f'Hi my name is {name}')    # Hi my name is John Doe

# String interpolation with .format()
name = 'John Doe'
print('Hi my name is {}'.format(name))  # Hi my name is John Doe

# Multiline strings (3 single-quotes)
text = '''First line
Second line
Third line
'''
# Multiline strings (3 double-quotes)
text = """First line
Second line
Third line
"""
print(text)
```
[[Go back]](#table-of-contents)

## Data Structures
Python supports the following data structures:
- [`list`](#lists)
- [`tuple`](#tuples)
- [`dict`](#dictionaries)
- [`set`](#sets)

Here's a table to illustrate their differences:

| Data Structure | Ordered | Immutable | Unique |
| -------------- | ------- | --------- | ------ |
| `list`         | yes     | no        | no     |
| `tuple`        | yes     | yes       | no     |
| `dict`         | no      | no        | no*    |
| `set`          | no      | no        | yes    |

*`dict` have unique keys but can have non-unique values

[[Go back]](#table-of-contents)

## Lists
Lists are an ordered collection of items. They are analogous to arrays in other programming languages.
```python
# Create the list
cities = ['Davao', 'Cebu', 'Cagayan de Oro', 'Mati']

print(type(cities))   # <class 'list'>
print(len(cities))    # 4

# Accessing index
print(cities[0])      # Davao
print(cities[-1])     # Mati

# Changing values
cities[1] = 'Bohol'
print(cities) # ['Davao', 'Bohol', 'Cagayan de Oro', 'Mati']

```
[[Go back]](#table-of-contents)

### Check if a value exists in a list
To check if a value already exists inside the list, use `in` operator.
```python
cities = ['Davao', 'Cebu', 'Cagayan de Oro', 'Mati']

print('Cebu' in cities)       # returns True
```
[[Go back]](#table-of-contents)

### Iterate through a list
Use a `for...in` loop to enumerate the contents of a list. List indexes are available with `enumerate()`.
```python
cities = ['Davao', 'Cebu', 'Cagayan de Oro', 'Mati']

# Iterate through the list
for city in cities:
    print(city)

# Use enumerate() if you need access to indexes.
for index, city in enumerate(cities):
    print(index, city)
```
[[Go back]](#table-of-contents)

### Comparing Lists
Python also allows item by item comparison with lists.
```python
numbers = [1, 3, 5, 7]
odds = [1, 3, 5, 7]
evens = [2, 4, 6, 8]

print(numbers == odds)  # True
print(numbers == evens)  # False
print(odds != evens)  # True
```
[[Go back]](#table-of-contents)

### Merging Lists
It is possible to concatenate two or more lists together with the `+` operator.
```python
fruits = ['apple', 'pear', 'banana']
vegetables = ['cabbage', 'pumpkin', 'potato']

food = fruits + vegetables
print(food)
# ['apple', 'pear', 'banana', 'cabbage', 'pumpkin', 'potato']
```
[[Go back]](#table-of-contents)

### List Unpacking
Take a list and use its items as new values in another list. Unlike merging, you can specify where to place the values.
```python
old_order = ['socks', 'basket', 'chair']
new_order = ['soap', 'chocolate', *old_order]

print(new_order)
# ['soap', 'chocolate', 'socks', 'basket', 'chair']
```
[[Go back]](#table-of-contents)

### List Methods
- `.append()` - add new item to the end of the list
  ```python
  items = [1, 2, 3]
  items.append(4)
  print(items)         # [1, 2, 3, 4]
  ```
- `.extend()` - add multiple items to the end of the list
  ```python
  items = [1, 2, 3]
  items.extend([4, 5, 6])
  print(items)        # [1, 2, 3, 4, 5, 6]
  ```
- `.insert()` - add new item in a specific index of a list
  ```python
  items = [1, 2, 3]
  items.insert(1, 'me')
  print(items)        # [1, 'me', 2, 3]
  ```
- `.clear()` - removes all items in the list
  ```python
  items = [1, 2, 3]
  items.clear()
  print(items)        # []
  ```
- `.pop()` - removes an item from a list and returns it as a value
  ```python
  items = [1, 2, 3, 4, 5, 6, 7, 8]

  old_item = items.pop()      # remove last item
  print(items)                # [1, 2, 3, 4, 5, 6, 7]
  print(old_item)             # 8

  old_item = items.pop(2)     # remove item at index 2
  print(items)                # [1, 2, 4, 5, 6, 7]
  print(old_item)             # 3
  ```
- `.remove()` - removes a value from the list
  ```python
  items = ['apple', 'banana', 'citrus', 'mango', 'orange']
  items.remove('citrus')
  print(items)                # ['apple', 'banana', 'mango', 'orange']
  ```
- `.index()` - search for an item in a list and returns the index if found
  ```python
  items = ['apple', 'banana', 'citrus', 'mango', 'orange']
  print(items.index('citrus'))        # 2

  # search from start (inclusive) index to end index (exclusive)
  print(items.index('orange', 0, 5))  # 4
  ```
- `.count()` - counts the number of times an item appears in a list
  ```python
  domains = ['com', 'ph', 'uk', 'org', 'ph', 'kr', 'au', 'eu']
  print(domains.count('ph'))    # 2
  ```
- `.reverse()` - flips the order of items in a list
  ```python
  items = [1, 2, 3, 4, 5]
  items.reverse()
  print(items)      # [5, 4, 3, 2, 1]
  ```
- `.sort()` - sorts all items in a list
  ```python
  items = [4, 6, 1, 3, 7, 5, 2]
  items.sort()
  print(items)      # [1, 2, 3, 4, 5, 6, 7]
  ```
- `.join()` - converts a list into a string separated with delimiters
  ```python
  items = ['apple', 'banana', 'citrus', 'mango', 'orange']
  joined_items = '/'.join(items)
  print(joined_items)     # apple/banana/citrus/mango/orange
  ```
[[Go back]](#table-of-contents)

### Slicing
Python allows you to work with a subset of items in a list. The syntax goes like this
```python
some_list[start:end:step]
```

Examples
```python
items = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

# start at index 3
print(items[3::])       # [3, 4, 5, 6, 7, 8, 9]
# end before index 7
print(items[:7:])       # [0, 1, 2, 3, 4, 5, 6]
# skip by 2 increments
print(items[::2])       # [0, 2, 4, 6, 8]

# Negative values are also supported

# start at 3rd from the last
print(items[-3::])      # [7, 8, 9]
# stop before the 3rd from the last
print(items[:-3:])      # [0, 1, 2, 3, 4, 5, 6]
# negative step means incrementing backwards
print(items[::-1])      # [9, 8, 7, 6, 5, 4, 3, 2, 1, 0]

# Override items from index 3 to 5 with new values
items[3:6:] = ['three', 'four', 'five']
print(items)            # [0, 1, 2, 'three', 'four', 'five', 6, 7, 8, 9]
```
[[Go back]](#table-of-contents)

### Deleting Lists
Aside from `pop()` and `remove()`, you can also remove items in a list using the `del` statement.
```python
numbers = [0, 1, 2, 3, 4, 5, 6]

# Delete first item
del numbers[0]
print(numbers)  # [1, 2, 3, 4, 5, 6]

# Delete last item
del numbers[-1]
print(numbers)  # [1, 2, 3, 4, 5]

# Delete with slices
del numbers[0::2]
print(numbers)  # [2, 4]

# Delete all items
del numbers[::]
print(numbers)  # []
```
[[Go back]](#table-of-contents)

### List Comprehension
Comprehension allows you to transform and filter items in a list. The syntax goes like this
```python
# Basic syntax
[expression for each_item in some_list]

# Only for some items where the condition is True
[expression for each_item in some_list if condition_expression]

# Transform each item depending on the conditional expression
[true_expression if condition else false_expression for each_item in some_list]
```

Examples
```python
items = [0, 1, 2, 3, 4, 5, 6]

# Return all items as is
print([item for item in items])                           # [0, 1, 2, 3, 4, 5, 6]
# Multiply each item by two
print([item * 2 for item in items])                       # [0, 2, 4, 6, 8, 10, 12]

# Only return items that are even
print([item for item in items if item % 2 == 0])          # [0, 2, 4, 6]

# Transform each item to 'odd' or 'even'
print(['odd' if item % 2 else 'even' for item in items])  # ['even', 'odd', 'even', 'odd', 'even', 'odd', 'even']
```
[[Go back]](#table-of-contents)

## Dictionaries
A dictionary is a data structure consisting of key-value pairs.
```python
# Create a dictionary
employee = {
    'name': 'John Doe',
    'age': 21,
    'active': True,
}
print(employee)     # {'name': 'John Doe', 'age': 21, 'active': True}

print(type(employee))  # <class 'dict'>
print(len(employee))   # 3

# Access a key
print(employee['name'])    # John Doe

# Add new key
employee['gender'] = 'male'
print(len(employee))   # 4
print(employee)
# {'name': 'John Doe', 'age': 21, 'active': True, 'gender': 'male'}

# Change value
employee['age'] = 30
print(employee)
# {'name': 'John Doe', 'age': 30, 'active': True, 'gender': 'male'}
```
[[Go back]](#table-of-contents)

### Check if a key exists in a dictionary
To check if a key already exists inside the dictionary, use `in` operator.
```python
employee = { 'name': 'John Doe','age': 21, 'active': True }

# Check if keys exists
print('name' in employee)       # True
print('address' in employee)    # False
```
[[Go back]](#table-of-contents)

### Iterate through a dictionary
Use a `for...in` loop to enumerate the contents of a dictionary.
```python
# Iterate over values
for value in employee.values():
    print(value)

# Iterate over keys
for value in employee.keys():
    print(value)

# Iterate over keys and values
for key, value in employee.items():
    print(f'Key: {key} - Value: {value}')
```
[[Go back]](#table-of-contents)

### Unpacking Dictionary
Take a dictionary and use its items as new values in another dictionary. You can specify where to place the values.
```python
detail = {
    'gender': 'male',
    'city': 'Davao',
}
user = {
    'first_name': 'John',
    'last_name': 'Doe',
    **detail,
}

print(user)
# {'first_name': 'John', 'last_name': 'Doe', 'gender': 'male', 'city': 'Davao'}
```
[[Go back]](#table-of-contents)

### Dictionary Methods
- `.clear()` - removes all items in a dictionary
  ```python
  employee = { 'name': 'John Doe', 'age': 21, 'active': True }

  employee.clear()
  print(employee)     # {}
  ```
- `.copy()` - makes a copy of an existing dictionary
  ```python
  employee = {'name': 'John Doe', 'age': 21, 'active': True}

  another_employee = employee.copy()
  print(another_employee)      # {'name': 'John Doe', 'age': 21, 'active': True}
  print(another_employee is employee)    # False
  ```
- `.fromkeys()` - generates a dictionary from a list with a default value
  ```python
  # Create a new dictionary with None as default value
  new_dict = {}.fromkeys(['name', 'age'], None)
  print(new_dict)   # {'name': None, 'age': None}
  ```
- `.get()` - retrieves an item from the dictionary and return None if it doesn't exists
  ```python
  employee = {'name': 'John Doe', 'age': 21}
  print(employee['active'])       # KeyError
  print(employee.get('active'))   # None
  ```
- `.pop()` - removes an item from a dictionary and returns it as a value
  ```python
  employee = {'name': 'John Doe', 'age': 21, 'active': True}
  old_item = employee.pop('age')
  print(employee)     # {'name': 'John Doe', 'active': True}
  print(old_item)     # 21
  ```
- `.popitem()` - removes the last item from a dictionary
  ```python
  employee = {'name': 'John Doe', 'age': 21, 'active': True}
  old_item = employee.popitem()
  print(employee)     # {'name': 'John Doe', 'age': 21}
  print(old_item)     # ('active', True)
  ```
- `.update()` - merge a dictionary into another, existing fields will be overwritten while the new ones will be added as is
  ```python
  employee = {'name': 'John Doe', 'age': 21}
  new_fields = {'age': 34, 'active': True}

  employee.update(new_fields)
  print(employee)     # {'name': 'John Doe', 'age': 34, 'active': True}
                      # age gets overwritten while active gets added
  ```
[[Go back]](#table-of-contents)

### Deleting Dictionaries
Aside from `pop()` and `popitem()`, you can also remove items from a dictionary using the `del` statement.
```python
employee = {
    'name': 'John Doe',
    'age': 21,
    'active': True,
}
print(employee) # {'name': 'John Doe', 'age': 21, 'active': True}

del employee['age']
print(employee)  # {'name': 'John Doe', 'active': True}
```
[[Go back]](#table-of-contents)

### Dictionary Comprehension
Comprehension allows you to transform and filter items in a dictionary. The syntax goes like this
```python
# Basic syntax
{key_expr: val_expr for key, value in dict_items}

# Filter out items based on a condition
{key_expr: val_expr for key, value in dict_items if condition}

# Transform each key depending on the conditional expression
{(true_key if condition else false_key): value for key, value in dict_items}

# Transform each value depending on the conditional expression
{key: (true_val if condition else false_val) for key, value in dict_items}
```

Examples
```python
employee = {'name': 'John Doe', 'age': 21, 'active': True}

# Return all items as is
print({key: value for key, value in employee.items()})
# {'name': 'John Doe', 'age': 21, 'active': True}

# Only include non-int values
print({key: value for key, value in employee.items() if type(value) is not int})
# {'name': 'John Doe', 'active': True}

# Capitalize the key and value for all items
print({key.upper(): str(value).upper() for key, value in employee.items()})
# {'NAME': 'JOHN DOE', 'AGE': '21', 'ACTIVE': 'TRUE'}

# Capitalize key if value is odd
numbers = {'one': 1, 'two': 2, 'three': 3, 'four': 4, 'five': 5}
print({(key.upper() if value % 2 else key): value for key, value in numbers.items()})
# {'ONE': 1, 'two': 2, 'THREE': 3, 'four': 4, 'FIVE': 5}
```
[[Go back]](#table-of-contents)

## Tuples
Tuples are immutable collection of items. They are ordered like lists but are read-only.
```python
fruits = ('apple', 'banana', 'peach', 'mango', 'orange')

print(type(fruits))         # <class 'tuple'>
print(len(fruits))          # 5

# Accessing index
print(fruits[2])            # peach
print(fruits[-1])           # orange

# Changing values (NOT ALLOWED!)
fruits[1] = 'avocado' 
# TypeError: 'tuple' object does not support item assignment
```
While tuples are commonly written with parenthesis, they are optional and Python will treat any comma-separated bare expressions as tuples.
```python
# Parenthesis are optional too
marital_status = 'single', 'married', 'divorced', 'widowed'
print(type(marital_status))     # <class 'tuple'>
```
[[Go back]](#table-of-contents)

### Check if a value exists in a tuple
To check if a value already exists inside the tuple, use `in` operator.
```python
fruits = ('apple', 'banana', 'peach', 'mango', 'orange')

print('mango' in fruits)    # True
print('avocado' in fruits)  # False
```
[[Go back]](#table-of-contents)

### Iterate through a tuple
Use a `for...in` loop to enumerate the contents of a tuple.
```python
fruits = ('apple', 'banana', 'peach', 'mango', 'orange')

for fruit in fruits:
    print(fruit)
```
[[Go back]](#table-of-contents)

### Comparing Tuples
Python also allows item by item comparison with tuples.
```python
numbers = (1, 3, 5, 7)
odds = (1, 3, 5, 7)
evens = (2, 4, 6, 8)

print(numbers == odds)  # True
print(numbers == evens)  # False
print(odds != evens)  # True
```
[[Go back]](#table-of-contents)

### Merging Tuples
It is possible to concatenate two or more tuples together with the `+` operator.
```python
fruits = ('apple', 'pear', 'banana')
vegetables = ('cabbage', 'pumpkin', 'potato')

food = fruits + vegetables
print(food)
# ('apple', 'pear', 'banana', 'cabbage', 'pumpkin', 'potato')
```
[[Go back]](#table-of-contents)

### Tuple Unpacking
Take a tuple and use its items as new values in another tuple. Unlike merging, you can specify where to place the values.
```python
old_order = ('socks', 'basket', 'chair')
new_order = ('soap', 'chocolate', *old_order)

print(new_order)
# ('soap', 'chocolate', 'socks', 'basket', 'chair')
```
[[Go back]](#table-of-contents)

### Tuple Methods
- `.count()` - counts the number of times an item appears in a tuple
  ```python
  domains = ('com', 'ph', 'uk', 'org', 'ph', 'kr', 'au', 'eu')
  print(domains.count('ph'))    # 2
  ```
- `.index()` - search for an item in a tuple and returns the index if found
  ```python
  items = ('apple', 'banana', 'citrus', 'mango', 'orange')
  print(items.index('citrus'))        # 2

  # search from start (inclusive) index to end index (exclusive)
  print(items.index('orange', 0, 5))  # 4
  ```
[[Go back]](#table-of-contents)

## Sets
Sets are a collection of unordered items. All items in a set are unique and there can be no duplicates.
```python
fruits = {'apple', 'banana', 'peach', 'mango', 'orange'}

print(fruits)                 # {'orange', 'peach', 'apple', 'banana', 'mango'}
print(type(fruits))           # <class 'set'>
print(len(fruits))            # 5

# Check if item exists in a set
print('peach' in fruits)      # True
print('avocado' in fruits)    # False
```
[[Go back]](#table-of-contents)

### Iterate through a set
Use a `for...in` loop to enumerate the contents of a set.
```python
fruits = {'apple', 'banana', 'peach', 'mango', 'orange'}

for fruit in fruits:
    print(fruit)
```
[[Go back]](#table-of-contents)

### Set Methods
- `.add()` - adds a new item on a set
  ```python
  cities = {'Davao', 'Bacolod', 'Cebu', 'Manila'}

  cities.add('Tagaytay')
  print(cities)     # {'Bacolod', 'Cebu', 'Tagaytay', 'Manila', 'Davao'}
  ```
- `.remove()` - removes an item from a set, throws `KeyError` if not found
  ```python
  cities = {'Davao', 'Bacolod', 'Cebu', 'Manila'}

  cities.remove('Bacolod')
  print(cities)     # {'Manila', 'Cebu', 'Davao'}
  ```
- `.discard()` - removes an item from a set, doesn't throw `KeyError` unlike `.remove()`
  ```python
  cities = {'Davao', 'Bacolod', 'Cebu', 'Manila'}

  cities.discard('Bacolod')
  print(cities)     # {'Manila', 'Cebu', 'Davao'}

  # Remove non-existent item from a set
  cities.discard('Makati')  # No exception raised
  print(cities)     # {'Manila', 'Cebu', 'Davao'}
  ```
- `.copy()` - makes a copy of an existing set
  ```python
  cities = {'Davao', 'Bacolod', 'Cebu', 'Manila'}
  another_cities = cities.copy()

  print(another_cities)             # {'Davao', 'Manila', 'Bacolod', 'Cebu'}
  print(another_cities is cities)   # False
  ```
- `.clear()` - removes all items in a set
  ```python
  cities = {'Davao', 'Bacolod', 'Cebu', 'Manila'}
  print(cities)       # {'Manila', 'Bacolod', 'Cebu', 'Davao'}

  cities.clear()
  print(cities)       # set()
  print(len(cities))  # 0
  ```
[[Go back]](#table-of-contents)

### Set Operations
```python
set_a = {1, 2, 3}
set_b = {3, 4, 5}

# Union
set_union = set_a | set_b
print(set_union)          # {1, 2, 3, 4, 5}

# Intersection
set_intersection = set_a & set_b
print(set_intersection)   # {3}
```
[[Go back]](#table-of-contents)

### Set Comprehension
Comprehension allows you to transform and filter items in a set. The syntax goes like this
```python
# Basic syntax
{expression for each_item in some_set}

# Only for some items where the condition is True
{expression for each_item in some_set if condition_expression}

# Transform each item depending on the conditional expression
{true_expression if condition else false_expression for each_item in some_set}
```

Examples
```python
items = {0, 1, 2, 3, 4, 5, 6}

# Return all items as is
print({item for item in items})     # {0, 1, 2, 3, 4, 5, 6}
# Multiply each item by two
print({item * 2 for item in items}) # {0, 2, 4, 6, 8, 10, 12}

# Only return items that are even
print({item for item in items if item % 2 == 0})  # {0, 2, 4, 6}

# Transform each item to 'odd' or 'even'
print({'odd' if item % 2 else 'even' for item in items}) # {'even', 'odd'}
```
[[Go back]](#table-of-contents)

## Functions
Functions are reusable set of code that can be called or invoked later.
```python
def make_user(username, password):
    return {
        'username': username,
        'password': password,
    }

print(make_user('john', 'abcdef'))  # {'username': 'john', 'password': 'abcdef'}
```
Functions will override other functions with existing name
```python
def speak():
    return 'Hello'

def speak():
    return 'Hi again'

print(speak())    # Hi again
```
If the function doesn't use `return`, it will return `None` by default.
```python
def speak():
    pass

print(speak())    # None
```
[[Go back]](#table-of-contents)

### Default Parameters
Assign default values in the parameters to make them optional
```python
def exponentation(base, power=2):   # power will be 2 by default
    return base ** power

print(exponentation(4)) # 16
```
[[Go back]](#table-of-contents)

### Keyword Arguments
Keyword arguments allow passing of arguments out-of-order and makes the code readable by adding labels to the arguments.
```python
def exponentation(base, power):
    return base ** power

# Positional arguments
print(exponentation(2, 4))              # 16

# Keyword arguments
print(exponentation(power=4, base=2))   # 16
```
[[Go back]](#table-of-contents)

### Positional-Only Arguments
You can designate arguments as positional-only arguments with the  `/` forward-slash character. All arguments before the forward-slash can only be passed as positional arguments.
```python
# designate first_name and last_name as positional-only arguments
def add_user(first_name, last_name, /, age, gender):
    print(f'User added: {first_name} {last_name}')

add_user('John', 'Doe', 21, 'male')
# User added: John Doe

add_user('John', 'Doe', age=21, gender='male')
# User added: John Doe

add_user('John', last_name='Doe', age=21, gender='male')
# TypeError: add_user() got some positional-only arguments passed as keyword arguments: 'last_name'

add_user(first_name='John', last_name='Doe', age=21, gender='male')
# TypeError: add_user() got some positional-only arguments passed as keyword arguments: 'first_name, last_name'
```
[[Go back]](#table-of-contents)

### Keyword-Only Arguments
You can designate arguments as keyword-only arguments by preceeding it with the `*` asterisk character. All arguments after the asterisk will only be accessible as keyword arguments.
```python
# designate age and gender as keyword-only arguments
def add_user(first_name, last_name, *, age, gender):
    print(f'User added: {first_name} {last_name}')

add_user('John', 'Doe', age=21, gender='male')
# User added: John Doe

add_user('John', 'Doe', 21, 'male')
# TypeError: add_user() takes 2 positional arguments but 4 were given

add_user('John', 'Doe')
# TypeError: add_user() missing 2 required keyword-only arguments: 'age' and 'gender'
```
[[Go back]](#table-of-contents)

### Scope
Global variables can be read from inside a function
```python
name = 'John'

def greeting():
    print(f'Hello {name}')

greeting()  # Hello John
```
However, global variables cannot be changed from within a function. Doing so will create a local variable and any changes to it are only local to that function.
```python
name = 'John'

def greeting():
    name = 'Mike'
    print(f'Hello {name}')  # Hello Mike

greeting()
print(name) # John
```
[[Go back]](#table-of-contents)

### `global` keyword
To change the value of a global variable, you need to use `global` keyword
```python
name = 'John'

def greeting():
    global name   # specify `name` as global

    name = 'Mike'
    print(f'Hello {name}')  # Hello Mike

greeting()
print(name)  # Mike

```
[[Go back]](#table-of-contents)

### `nonlocal` keyword
Functions in Python can be nested and sometimes you might want to access the variables in the parent function scope. To do so, you must use the `nonlocal` keyword.
```python
def start_counter():
    counter = 0

    def tick():
        nonlocal counter  # access counter in parent scope
        counter += 1
        return counter

    return tick


my_counter = start_counter()
print(my_counter()) # 1
print(my_counter()) # 2
print(my_counter()) # 3
```
[[Go back]](#table-of-contents)

### `*args` operator
Allows for variable-length positional arguments in functions. The arguments will be passed to a function as a tuple.
```python
def sum(*nums):
    print(type(nums))   # <class 'tuple'>

    result = 0
    for num in nums:
        result += num
    return result


print(sum(1, 2, 3, 4, 5))   # 15
```
[[Go back]](#table-of-contents)

### `**kwargs` operator
Allows for variable-length keyword arguments in functions. The arguments will be passed to a function as a dictionary.
```python
def show_age(**persons):
    print(type(persons))    # <class 'dict'>

    for key, value in persons.items():
        print(f'{key} is {value} years old')


show_age(john=21, mike=18, paul=24, tim=20)
# john is 21 years old
# mike is 18 years old
# paul is 24 years old
# tim is 20 years old
```
[[Go back]](#table-of-contents)

### Parameter ordering
Python resolves arguments by the following order:
- Positional arguments
- [Variable-length positional arguments (`*args`)](#args-operator)
- [Default parameters](#default-parameters)
- [Variable-length keyword arguments (`**kwargs`)](#kwargs-operator)

Example
```python
def foo(first, second, *args, default_param='bar', **kwargs):
    print(type(first), first)
    print(type(second), second)
    print(type(args), args)
    print(type(default_param), default_param)
    print(type(kwargs), kwargs)


foo('uno', 'dos', 'tres', 'kwatro', one=1, two=2, three=3)
# <class 'str'> uno
# <class 'str'> dos
# <class 'tuple'> ('tres', 'kwatro')
# <class 'str'> bar
# <class 'dict'> {'one': 1, 'two': 2, 'three': 3}
```
[[Go back]](#table-of-contents)

### Tuple and List Unpacking
A single asterisk `*` operator can be used to pass each items in a list or tuple as positional arguments to a function. This is analogous to spread operator in other programming languages.
```python
def sum(num1, num2, num3):
    return num1 + num2 + num3


# Tuple unpacking
nums_tuple = (1, 2, 3)
print(sum(*nums_tuple)) # 6


# List unpacking
nums_list = [4, 5, 6]
print(sum(*nums_list)) # 15
```
[[Go back]](#table-of-contents)

### Dictionary Unpacking
A double asterisk `**` operator can be used to pass dictionaries as a collection of keyword arguments to a function.
```python
def add_customer(first_name, last_name, age):
    print(f'Added customer {first_name} {last_name}, {age} y/o')


new_customer = {
    'first_name': 'John',
    'last_name': 'Doe',
    'age': 21,
}

# Dictionary unpacking
add_customer(**new_customer) # Added customer John Doe, 21 y/o
```
[[Go back]](#table-of-contents)

### Higher-order functions
Functions can take other functions as arguments as well as return them as values

Function as argument
```python
def print_message(message):
    print(message)


def invoker(fn):
    fn('Hello')

# Pass functions as arguments
invoker(print_message)      # Hello
```
Function as return value
```python
def init_logger():
    def log_message(message):
        print(message)
    return log_message  # Function as return value

logger = init_logger()  
logger('Hello')     # Hello
```
[[Go back]](#table-of-contents)

### Docstrings
Docstrings allows you to add documentation to your function. They can be used by code editors as popups when writing function calls.
```python
def greet():
    """Prints hello world to the standard output"""
    print('Hello World')


greet()
print(greet.__doc__)    # Prints hello world to the standard output
```
[[Go back]](#table-of-contents)

## Lambda
Defines an expression that can be executed at a later point. They are analogous to anonymous functions in other programming languages.
```python
add_num = lambda a, b: a + b

print(add_num(4, 5)) # 9
```
[[Go back]](#table-of-contents)

## Built-in Functions
### `map()`
Transform each item in an iterable.
```python
nums = [1, 2, 3, 4, 5]

doubled = map(lambda num: num * 2, nums)
print(list(doubled))    # [2, 4, 6, 8, 10]
```
[[Go back]](#table-of-contents)

### `filter()`
Filter each item in an iterable based on a boolean expression.
```python
nums = [1, 2, 3, 4, 5, 6]

even_nums = list(filter(lambda num: not num % 2, nums))
print(even_nums)   # [2, 4, 6]
```
[[Go back]](#table-of-contents)

### `all()`
Returns `True` if all the items in the iterable evaluates to `True`
```python
nums = [2, 4, 6, 8, 10]

is_even = all([not num % 2 for num in nums])
print(is_even)  # True
# All items are even
```
[[Go back]](#table-of-contents)

### `any()`
Returns `True` if at least one of the items in the iterable evaluates to `True`
```python
nums = [2, 4, 6, 8, 10]

some_odd = any([num % 2 for num in nums])
print(some_odd)   # False
# Not a single one is od
```
[[Go back]](#table-of-contents)

### `sorted()`
Returns a copy of a sorted list or tuple
```python
nums = [4, 3, 7, 9, 5, 2]
print(sorted(nums))                   # [2, 3, 4, 5, 7, 9]
print(sorted(nums, reverse=True))     # [9, 7, 5, 4, 3, 2]


# Sorting dict by specifying keys
leaderboard = [
    {'name': 'John', 'score': 21},
    {'name': 'Anna', 'score': 18},
    {'name': 'Mike', 'score': 24},
    {'name': 'Kate', 'score': 30},
]
high_scores = sorted(leaderboard,
                     key=lambda item: item['score'],
                     reverse=True)
print(high_scores)
# [{'name': 'Kate', 'score': 30},
#   {'name': 'Mike', 'score': 24},
#   {'name': 'John', 'score': 21},
#   {'name': 'Anna', 'score': 18}]
```
[[Go back]](#table-of-contents)

### `min()` and `max()`
Returns the highest and lowest value in an iterable
```python
nums = (4, 3, 7, 9, 5, 2)
print(max(nums))    # 9
print(min(nums))    # 2

# Using keys with dictionaries
leaderboard = [
    {'name': 'John', 'score': 21},
    {'name': 'Anna', 'score': 18},
    {'name': 'Mike', 'score': 24},
    {'name': 'Kate', 'score': 30},
]

get_score = lambda item: item['score']

highest = max(leaderboard, key=get_score)
lowest = min(leaderboard, key=get_score)

print(highest)  # {'name': 'Kate', 'score': 30}
print(lowest)   # {'name': 'Anna', 'score': 18}
```
[[Go back]](#table-of-contents)

### `reversed()`
Returns a reversed version of an iterable
```python
nums = [1, 2, 3, 4, 5]
print(list(reversed(nums))) # [5, 4, 3, 2, 1]

greet = 'hello world'
print(''.join(list(reversed(greet)))) # dlrow olleh
```
[[Go back]](#table-of-contents)

### `abs()`
Returns the absolute value of a number
```python
print(abs(-32))     # 32
print(abs(21))      # 21
```
[[Go back]](#table-of-contents)

### `sum()`
Returns the sum of all the values inside the iterable
```python
print(sum((1, 2, 3, 4, 5)))     # 15
print(sum([6, 7, 8, 9, 10]))    # 40
```
[[Go back]](#table-of-contents)

### `round()`
Rounds the number
```python
print(round(3.12))  # 3
print(round(4.62))  # 5

# Round by number of digits
print(round(21.3412, 2))  # 21.34
```
[[Go back]](#table-of-contents)

### `zip()`
Takes two or more iterables and joins all items in each index into one tuple
```python
col_a = ['a', 'b', 'c', 'd']
col_b = [1, 2, 3 , 4]

print(list(zip(col_a, col_b)))
# [('a', 1), ('b', 2), ('c', 3), ('d', 4)]
```
[[Go back]](#table-of-contents)

## Debugging and Error Handling
### Common Exceptions
- `Exception` - generic exception
- `SyntaxError` - code doesn't follow Python syntax rules
- `NameError` - variable, function, or class doesn't exists or is not defined
- `TypeError` - the type doesn't support the following operation
- `IndexError` - using invalid index on list or tuple
- `ValueError` - the value has a right type but invalid value
- `KeyError` - accessing non-existent keys in a dictionary
- `AttributeError` - accessing non-existent attributes in an object

[[Go back]](#table-of-contents)

### `raise`
Use `raise` to throw exceptions
```python
def greet(name):
    if type(name) is not str:
        raise TypeError('name must be type of str')
    
    print(f'Hello, {name}')


greet('John')   # Hello, John
greet(22)       # TypeError: name must be type of str
```
[[Go back]](#table-of-contents)

### `try...except`
Catch and handle exceptions
```python
try:
    foo
except NameError as err:
    print('An exception has occured')
    print(err)
```
Output
```
An exception has occured
name 'foo' is not defined
```

### `try...except...else`
Executes when there is no exception raised
```python
try:
    pass
except:
    print('Some exception occured')
else:
    print('No exceptions raised')
```
Output
```
No exceptions raised
```

### `finally` block
Execute code regardless of whether an exception occured or not
```python
try:
    raise ValueError
except:
    print('Some exception occured')
else:
    print('No exceptions raised')
finally:
    print('end of try block')
```
Output
```
Some exception occured
end of try block
```
[[Go back]](#table-of-contents)

### Trace Debugging with `pdb`
Code
```python
import pdb; pdb.set_trace()
```
Commands
- `l` - print current code
- `n` - proceed to next line
- `p` - inspect variable value
- `c` - exit pdb and continue execution

[[Go back]](#table-of-contents)

## Modules
Modules are self-contained Python code that contains stuff like functions or classes that can be used in other scripts.

### Importing Modules
```python
# Basic syntax
import random

# Using alias
import random as rd
print(rd.randint(1, 10))

# Only import a subset of a module
from random import randint
print(randint(1, 5))

# Use comma to import more than one
from random import randint, choice
print(randint(1, 5))
print(choice(['foo', 'bar']))

# Import a subset of a module and give it an alias
from random import randint as ri
print(ri(1, 5))

# Import everything from a module (NOT RECOMMENDED)
from random import *
print(randint(1, 5))
```
[[Go back]](#table-of-contents)

### Custom Modules
Custom modules are modules that are written by the user, as opposed to built-in or third-party modules.

`fruits.py`
```python
def apples():
    return 'This is apples'

def grapes():
    return 'This is grapes'

def bananas():
    return 'This is bananas'
```
`demo.py`
```python
import fruits

print(fruits.apples())      # This is apples
print(fruits.grapes())      # This is grapes
print(fruits.bananas())     # This is bananas
```
[[Go back]](#table-of-contents)

### Nested Modules
Use dot-notation to access modules inside a subdirectory

`fruits/apple.py`
```python
def get_apple():
    return 'This is apple.py'
```

`main.py`
```python
import fruits.apple

print(fruits.apple.get_apple())   # This is apple.py
```

[[Go back]](#table-of-contents)

### Module Resolution
When breaking down a complex Python application into separate files (modules), it is important to note that the path for module resolution always starts from where you launch your application.

Consider the following project structure:
```
.
└── hello-world/
    ├── fruits/
    │   └── apple.py
    ├── vegetables/
    │   └── cabbage.py
    └── main.py
```
`main.py`
```python
from fruits import apple
apple.greet()
```

`fruits/apple.py`
```python
from vegetables import cabbage

def greet():
    print('Hello from apple.py')
    cabbage.greet()
```

`vegetables/cabbage.py`
```python
def greet():
    print('Hello from cabbage.py')
```

Output:
```bash
$ python main.py 
Hello from apple.py
Hello from cabbage.py
```
Since we started our program from `main.py`, all module resolution will start from the directory where `main.py` is located. Hence if we want to import `cabbage` module from `fruits/apples.py`, we simply use either of these import statements:
```python
# Either this
import vegetables.cabbage

# Or this
from vegetables import cabbage
```
[[Go back]](#table-of-contents)


### `__name__` variable
When a Python file is included as a module from another file, it will return the name of the module. If the Python file is ran from the terminal, it will return `__main__` instead.

`foo.py`
```python
print('In foo: ', __name__)
```
`bar.py`
```python
import foo
print('In bar: ', __name__)
```
Terminal
```bash
$ python bar.py

In foo:  foo
In bar:  __main__
```
[[Go back]](#table-of-contents)

### Runnable Python
If the Python script is meant to be executed from the shell, it is recommended to check if it's run as a main script. Some IDEs can detect this code block and use it as a hint to indicate that the script is runnable.
```python
def main():
    # Insert code here
    pass

if __name__ == '__main__':
    main()
```
[[Go back]](#table-of-contents)

### Installing Third-Party Modules with `pip`
Install a package from [PyPi](https://pypi.org/) with `pip`
```bash
$ pip install termcolor
```
Using the third-party package
```python
import termcolor

print(termcolor.colored('Hello World', 'green'))
# Prints a green "Hello World" text onto the screen
```
[[Go back]](#table-of-contents)

### Packages
You can group multiple Python modules into a single package by using `__init__.py`.

`vegetables/eggplant.py`
```python
# sample function
def get_eggplant():
    return 'This is eggplant.py'
```

`vegetables/__init__.py`
```python
# add eggplant module to scope
__all__ = ('eggplant',)
```

`main.py`
```python
from vegetables import *

# eggplant module is now in scope
print(dir())
# ['__annotations__', '__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__spec__', 'eggplant']

print(eggplant.get_eggplant())
# This is eggplant.py
```

[[Go back]](#table-of-contents)


## Classes and Objects
### Define a class
Classes are defined with the `class` keyword. Each class may define a constructor method `__init__()` where the attributes of the object are initialized. All methods of the class should have `self` as the first parameter and it serves as a reference to the current instance of the class.
```python
# Create 'User' class
class User:
    # Constructor
    def __init__(self, first_name, last_name):
        # Initialize attributes
        self.first_name = first_name
        self.last_name = last_name

    # Instance method
    def print_fullname(self):
        print(self.first_name, self.last_name)

# Instantiate new object
john = User('John', 'Doe')

# Accessing attributes
print(john.first_name)  # John
print(john.last_name)   # Doe

# Accessing methods
john.print_fullname()   # John Doe
```
[[Go back]](#table-of-contents)

### Class Attributes
Class attributes are variables that are shared across all objects.
```python
class Foo:
    # Define class attribute named 'count'
    count = 0

    def __init__(self):
        # Access class properties from within class
        Foo.count += 1


# Access class properties outside class
print(Foo.count)  # 0

foo1 = Foo()
print(Foo.count)  # 1

foo2 = Foo()
print(Foo.count)  # 2
```
[[Go back]](#table-of-contents)

### Class Methods
Class methods belong to the class and are shared across all objects. They are defined using the `@classmethod` decorator.
```python
class Foo:
    name = None

    @classmethod
    def get_name(cls):
        return cls.name

    @classmethod
    def set_name(cls, new_name):
        cls.name = new_name

# Create 2 sample Foo objects
foo1 = Foo()
foo2 = Foo()

# Call a class method
Foo.set_name('barr')

# Name is shared across instances
print(Foo.get_name())   # barr
print(foo1.get_name())  # barr
print(foo2.get_name())  # barr

```
[[Go back]](#table-of-contents)

### `__repr__()` magic method
Allows you to define the string representation of an object.
```python
class User:
    def __init__(self, first_name, last_name):
        self.first_name = first_name
        self.last_name = last_name

    def __repr__(self):
        return f'Hi my name is {self.first_name} {self.last_name}'


john = User('John', 'Doe')
print(john)  # Hi my name is John Doe


# __repr__() is also called when doing string casting
str_john = str(john)
print(str_john) # # Hi my name is John Doe
```
[[Go back]](#table-of-contents)

### Class Getter and Setter
These are special methods that are executed when a class attribute gets accessed or changed from outside the class. Getters are designated using `@property` decorator while the setter is designated using `@propname.setter` decorator.
```python
class Foo:
    def __init__(self, message):
        self._message = message

    # define getter
    @property
    def message(self):
        print('Getter invoked!')
        return self._message

    # define setter
    @message.setter
    def message(self, value):
        print('Setter invoked!')
        self._message = value


foo = Foo('hello')
print(foo.message)      # Getter invoked! (hello)

foo.message = 'barr'    # Setter invoked!
print(foo.message)      # Getter invoked! (barr)
```
[[Go back]](#table-of-contents)

### Inheritance
Take a base class and use it to build a subclass with added functionality. The subclass inherits all class attributes and methods as well as the instance attributes and methods.
```python
# Base class
class Foo:
    # Class attribute
    enable = False

    # Instance method
    def hello(self):
        print('Hello World')

# Subclass
class Bar(Foo):   # Inherit from Foo class
    pass

# Inherited class attribute
print(Bar.enable)   # False

# Inherited instance method
bar = Bar()
bar.hello()     # Hello World

# bar is both instance of itself and base class Foo
print(isinstance(bar, Bar))     # True
print(isinstance(bar, Foo))     # True

```
[[Go back]](#table-of-contents)

### Invoking parent constructor
Subclass constructor can also manually invoke parent class constructor by using `super().__init__(...args)`
```python
class Foo:
    def __init__(self, message):
        self.message = message
        print('Base class constructor invoked!')


class Bar(Foo):
    def __init__(self, message):
        super().__init__(message)
        print('Subclass constructor invoked!')


bar = Bar('hello world')
# Base class constructor invoked!
# Subclass constructor invoked!

print(bar.message)      # hello world
```
[[Go back]](#table-of-contents)

### Multiple Inheritance
Python allows subclass to inherit from multiple base class.
```python
class Foo:
    def foo(self):
        print('This is foo')


class Bar:
    def bar(self):
        print('This is bar')


class Baz(Foo, Bar):   # Inherit from Foo and Bar
    def baz(self):
        print('This is baz')


new_baz = Baz()
new_baz.baz()   # This is baz
new_baz.foo()   # This is foo
new_baz.bar()   # This is bar
```
[[Go back]](#table-of-contents)

### Method Resolution Order (MRO)
When accessing an attribute or a method in a class, Python traverses the inheritance hierarchy using Method Resolution Order (MRO).
```python
class A:
    def __init__(self):
        print('Class A init')
        super().__init__()


class B(A):
    def __init__(self):
        print('Class B init')
        super().__init__()


class C(A):
    def __init__(self):
        print('Class C init')
        super().__init__()


class D(B, C):
    def __init__(self):
        print('Class D init')
        super().__init__()


d = D()
# Class D init
# Class B init
# Class C init
# Class A init
```
Here are some helpers to determine the MRO of a class.
```python
print(D.__mro__)
# (<class '__main__.D'>, <class '__main__.B'>, <class '__main__.C'>, <class '__main__.A'>, <class 'object'>)

print(D.mro())
# [<class '__main__.D'>, <class '__main__.B'>, <class '__main__.C'>, <class '__main__.A'>, <class 'object'>]

help(D)
# class D(B, C)
#  |  Method resolution order:
#  |      D
#  |      B
#  |      C
#  |      A
#  |      builtins.object
```
[[Go back]](#table-of-contents)

### Magic Methods
Magic methods are special methods that have double underscores at the start and end of their names. They have special meaning to Python and each of them has their own use. The constructor method `__init__()` is one such magic method.
```python
class Wallet:
    # constructor
    def __init__(self, amount):
        self.amount = amount

    # string representation
    def __repr__(self):
        return f'You have {self.amount} pesos in wallet'

    # logical size
    def __len__(self):
        return self.amount

    # addition
    def __add__(self, wallet):
        if isinstance(wallet, Wallet):
            return Wallet(self.amount + wallet.amount)


wallet1 = Wallet(23)
# invoke __repr__()
print(wallet1)              # You have 23 pesos in wallet
# invoke __len__()
print(len(wallet1))         # 23

wallet2 = Wallet(10)
# invoke __add__
wallet3 = wallet1 + wallet2
# invoke __repr__
print(wallet3)              # You have 33 pesos in wallet

# __add__() returns a brand new instance of the Wallet object
print(wallet1 is wallet3)   # False
print(wallet2 is wallet3)   # False
```
[[Go back]](#table-of-contents)

### Abstract Classes
Classes that served as a base class for other classes. They contain one or more abstract methods that must be implemented in the subclass. They are not meant to be instantiated as a stand-alone object. Any instance creation must be done in their subclasses.

To designate a class as an abstract class, inherit from `ABC` class from `abc` (Abstract Base Class) built-in module. To designate specific methods inside the class as an abstract method, use the `@abstractmethod` decorator.
```python
from abc import ABC, abstractmethod

# Abstract Class
class AbstractFoo(ABC):
    @abstractmethod     # Specify hello() as abstract method
    def hello(self):
        pass

# Complete Subclass
class Bar(AbstractFoo):
    def hello(self):    # Abstract method implemented
        print('Hello world')

# Incomplete Subclass
class Baz(AbstractFoo):
    pass    # No abstract method implementation

# Complete Subclass can be instantiated
bar = Bar()
bar.hello()     # Hello world

# Abstract classes cannot be instantiated
foo = AbstractFoo()
# TypeError: Can't instantiate abstract class AbstractFoo with abstract method hello

# Incomplete Subclass cannot be instantiated
# All abstract methods must be implemented first!
baz = Baz()
# TypeError: Can't instantiate abstract class Baz with abstract method hello
```
[[Go back]](#table-of-contents)

## Enums
Enums are used to represent a list of constants that a particular variable can only hold.
```python
from enum import Enum

class CivilStatus(Enum):
    SINGLE = 1
    MARRIED = 2
    DIVORCED = 3
    WIDOWED = 4

def set_civil_status(status: CivilStatus) -> None:
    print(type(status), status)

# Autocomplete with type hinting
set_civil_status(CivilStatus.SINGLE)
# <enum 'CivilStatus'> CivilStatus.SINGLE

# Get value from enum
print(CivilStatus.MARRIED.value)    # 2

# Get string key from enum
new_status = CivilStatus.SINGLE.name
print(type(new_status), new_status)     # <class 'str'> SINGLE

# Parse int to enum object
print(CivilStatus(4))   # CivilStatus.WIDOWED

# parse str to enum object
print(CivilStatus['SINGLE'])    # CivilStatus.SINGLE

# Comparing enums
print(CivilStatus(3) == CivilStatus.DIVORCED)  # True
```
[[Go back]](#table-of-contents)

### Auto-generated enum values
If you want to make an enum without having to manually specify the values, use `auto()` to let Python generate distinct values for you.
```python
from enum import Enum, auto

class Gender(Enum):
    MALE = auto()
    FEMALE = auto()
    OTHERS = auto()

print(Gender.MALE.value)    # 1
print(Gender.FEMALE.value)  # 2
print(Gender.OTHERS.value)  # 3
```
[[Go back]](#table-of-contents)

## Iterators and Iterables
Iterables are data structures that can be iterated upon, like say with a `for... in` loop. Examples of iterables are `list`, `dict`, `set`, `tuple` and so forth. Iterables can be passed to `iter()` in order to access their iterator.

Iterators are a special interface provided by iterables. They are passed to `next()` in order to retrieve data in a sequential manner. Once the data is exhausted, `next()` raises a `StopIteration` exception.
```python
# list iterable
numbers = [1, 2, 3, 4]

# iter() returns an iterator from iterable
num_iterator = iter(numbers)

print(type(num_iterator))  # <class 'list_iterator'>

# next() is called on iterator to get each item
print(next(num_iterator))  # 1
print(next(num_iterator))  # 2
print(next(num_iterator))  # 3
print(next(num_iterator))  # 4

# next() fails once at the end of the list
print(next(num_iterator))  # StopIteration exception
```
[[Go back]](#table-of-contents)

## Generators
Generators are a subclass of [iterators](#iterators-and-iterables). There are two types: generator functions and generator expressions.

### Generator Functions
Generator functions are functions that can pause and resume execution. These functions use `yield` instead of `return`. Unlike regular functions, they return a `generator` object. Like iterators they can be passed to `next()` to resume the execution of the paused function and to get the next value.
```python
# generator function
def loop_through(seq):
    size = len(seq)
    current = 0
    while current < size:
        yield seq[current]
        current += 1


num_generator = loop_through([1, 2, 3, 4])

print(type(num_generator))  # <class 'generator'>

print(next(num_generator))  # 1
print(next(num_generator))  # 2
print(next(num_generator))  # 3
print(next(num_generator))  # 4
print(next(num_generator))  # StopIteration exception
```
[[Go back]](#table-of-contents)

### Generator Expressions
Generator expressions are another way of creating generators. Their syntax are quite similar to [list comprehension](#list-comprehension) but using parenthesis instead.

Syntax
```python
new_gen = (expression for each_item in iterable)
```

Example
```python
# generator expression
num_generator = (num for num in range(1, 5))

print(type(num_generator))  # <class 'generator'>

print(next(num_generator))  # 1
print(next(num_generator))  # 2
print(next(num_generator))  # 3
print(next(num_generator))  # 4
print(next(num_generator))  # StopIteration exception
```
[[Go back]](#table-of-contents)

## Decorators
Decorators are a type of higher-order functions. They are typically used to wrap other functions and alter their behavior. A decorator uses an `@` sign followed by the name of the decorator. They are placed a line before the function they are supposed to alter.
```python
# decorator function
def enhanced(func):
    def wrapper():
        print('decorator invoked')
        return func()
    return wrapper

# no decorator
def foo(): print('foo')
foo() # foo

# with decorator
@enhanced     # bar() is now enhanced
def bar(): print('bar')

bar() # decorator invoked
      # bar
```
[[Go back]](#table-of-contents)

### Decorators with Variable Argument Support
Functions can have different parameter signatures. In order to deal with this, decorators should be able to capture all arguments passed to the function. To do this, simply use `*args` and `**kwargs` in the wrapper function. 

This way you can intercept all positional and keyword arguments and be able to passed them to the underlying function.

```python
# decorator for inspecting return values
def var_dump(fn):
    def wrapper(*args, **kwargs): # capture all arguments passed
        val = fn(*args, **kwargs)
        print(f'Value: "{val}", Type: {type(val)}')
        return val
    return wrapper


@var_dump
def greet(first_name, last_name, age):
    return f"Hi I'm {first_name} {last_name}. I'm {age} y/o."


@var_dump
def get_even(*nums):
    return [num for num in nums if num % 2 == 0]


greet(age=21, last_name='Doe', first_name='John')
# Value: "Hi I'm John Doe. I'm 21 y/o.", Type: <class 'str'>

get_even(1, 2, 3, 4, 5, 6)
# Value: "[2, 4, 6]", Type: <class 'list'>
```
[[Go back]](#table-of-contents)

### Preserving Metadata in Decorators
Decorator alters a function by calling it inside a wrapper function. Because of this, any metadata (like docstrings) becomes overwritten by the wrapper function.
```python
def foo(fn):
    def wrapper(*args, **kwargs):
        """This is wrapper function"""
        return fn(*args, **kwargs)
    return wrapper

@foo
def bar():
    """This is bar function"""
    pass

print(bar.__doc__)  # This is wrapper function
```
In order to preserve function metadata, you may decorate the inner wrapper function with the `@wraps` decorator from `functools`.
```python
from functools import wraps

def foo(fn):
    @wraps(fn)   # clone metadat from original function into wrapper function
    def wrapper(*args, **kwargs):
        """This is wrapper function"""
        return fn(*args, **kwargs)
    return wrapper

@foo
def bar():
    """This is bar function"""
    pass

print(bar.__doc__)  # This is bar function
```
[[Go back]](#table-of-contents)

### Decorators with Arguments
Decorators may also accept arguments. To do this, simply add another inner function to capture the argument.
```python
from functools import wraps

def foo(val):
    def inner(fn):  # wrap another function
        print(f'foo decorator invoked with value of {val}')

        @wraps(fn)
        def wrapper(*args, **kwargs):
            return fn(*args, **kwargs)
        return wrapper
    return inner

@foo('baz')     # decorators with arguments
def bar():
    pass

bar()
# foo decorator invoked with value of baz
```
[[Go back]](#table-of-contents)

## Type Hinting and Annotations
### Install `mypy`
```bash
$ pip install mypy
```
[[Go back]](#table-of-contents)

### Enable VSCode Support for `mypy`
- Press `Ctrl + Shift + P`
- Select `Python: Select Linter`
- Select `mypy` from the list

[[Go back]](#table-of-contents)

### Basic Type Annotation
Syntax
```
var_name: type = some_expr
```
Example
```python
age: int = 21                   # int
height_cm: float = 152.67       # float
greeting: str = 'hello'         # str
flag_enabled: bool = True       # bool
metadata: Any = 'somedata'      # Any (see Any section for import)
```
[[Go back]](#table-of-contents)

### List Annotation
```python
fruits: list[str] = ['apple', 'mango', 'banana', 'orange']
```
[[Go back]](#table-of-contents)

### Tuple Annotation
```python
# Implicit annotation
coord: tuple = (32.5, 61.2)

# Explicit annotation
strict_coord: tuple[float, float, float] = (25.6, 983.1, 22.4)
```
[[Go back]](#table-of-contents)

### Dictionary Annotation
```python
customer: dict[str, str] = {
    'first_name': 'John',
    'last_name': 'Doe',
}
```
[[Go back]](#table-of-contents)

### Set Annotation
```python
cities: set[str] = {'Davao', 'Manila', 'Cebu'}
```
[[Go back]](#table-of-contents)

### Function Annotation
```python
def add_numbers(a: int, b: int, c: int) -> int:
    return a + b + c

# No return value (None)
def greet() -> None:
    print('Hello world')
```
[[Go back]](#table-of-contents)

### Optional Argument Annotation
```python
from typing import Optional

def foo(output: Optional[bool] = False):
    pass
```
[[Go back]](#table-of-contents)

### `Any` type Annotation
```python
from typing import Any

def get_field(field: Any) -> Any:
    return field
```
[[Go back]](#table-of-contents)

### Union Type Annotation
Specify multiple acceptable types
```python
def set_mileage(distance_km: int | float) -> None:
    pass

set_mileage(35)     # int
set_mileage(21.67)  # float
```
[[Go back]](#table-of-contents)

### Custom Type Annotation
```python
# Assign alias to types
Vector = List[float]

def set_velocity(new_velocity: Vector) -> Vector:
    return new_velocity

# Aliases can also be used as types in other aliases
Vectors = List[Vector]

def set_velocities(new_velocities: Vectors) -> Vectors:
    return new_velocities
```
[[Go back]](#table-of-contents)

### Sequence Type Annotation
Types that can be accessed with an index (i.e `list`, `tuple`, and `str`)
```python
from typing import Sequence

def set_places(places: Sequence[str]):
    pass

set_places(['a', 'b', 'c'])     # Lists are ok
set_places(('a', 'b', 'c'))     # Tuples are ok
set_places('abcd')              # Strings are ok as well
```
[[Go back]](#table-of-contents)

  ### Callable Type Annotation
Types for annotating functions and lambdas.

Syntax
```
var_name: Callable[[first_arg, second_arg, nth_arg], return_type]
```

Example
```python
from typing import Callable

def greet_name(first_name: str, last_name: str, age: int) -> str:
    return f'Hello, my name is {first_name} {last_name}, I am {age} years old'

def set_callback(callback: Callable[[str, str, int], str]) -> None:
    result = callback('John', 'Doe', 29)
    print(result)

set_callback(greet_name)
```
[[Go back]](#table-of-contents)

### Generics Annotations
```python
from typing import TypeVar

T = TypeVar('T')

def get_element(elements: List[T], index: int) -> T:
    return elements[index]
```
[[Go back]](#table-of-contents)

## Dataclasses
Dataclasses are a good way write short classes whose sole purpose is to simply store data. They can be used as an alternative to dictionaries. Dataclasses makes use of type hinting, making it possible for IDEs to provide autocompletion with their fields.

To turn a regular class into a dataclass, simply use the `@dataclass` decorator.
```python
from dataclasses import dataclass

# Define a dataclass
@dataclass
class Customer:
    first_name: str
    last_name: str
    age: int
    active: bool = False    # Optional field

# Create instance
john = Customer(
    first_name='John',
    last_name='Doe',
    age=31,
)

# String repr
print(john)
# Customer(first_name='John', last_name='Doe', age=31, active=False)

# Accessing field values
print(john.first_name)  # John
print(john.last_name)   # Doe

# Changing field values
print(john.age)     # 31
john.age = 26
print(john.age)     # 26
```
[[Go back]](#table-of-contents)

### Converting Dataclasses to `dict` and `tuple`
To convert an instance of dataclass into a `dict` or a `tuple`, simply use `asdict()` and `astuple()` respectively.
```python
from dataclasses import dataclass, asdict, astuple

# Convert to dict
print(asdict(john))
# {'first_name': 'John', 'last_name': 'Doe', 'age': 26, 'active': False}

# Convert to tuple
print(astuple(john))
# ('John', 'Doe', 26, False)
```
[[Go back]](#table-of-contents)

### Immutable Dataclasses
To make a dataclass immutable, set the `frozen` argument to `True` in the decorator. This will make its fields read-only after initialization.
```python
from dataclasses import dataclass

@dataclass(frozen=True)     # Immutable dataclass
class Customer:
    first_name: str
    last_name: str
    age: int
    active: bool = False    # Optional field

# Create instance
john = Customer(
    first_name='John',
    last_name='Doe',
    age=31,
)

print(john.age)     # 31
john.age = 29
# dataclasses.FrozenInstanceError: cannot assign to field 'age'
```
[[Go back]](#table-of-contents)

### Ordered Dataclasses
If you want a dataclass that supports comparison operators, set the `order` argument to `True` in the decorator. This will also come in handy when you want to perform sorting with dataclasses.
```python
from dataclasses import dataclass

# Define an ordered dataclass
@dataclass(order=True)
class Customer:
    first_name: str
    last_name: str
    age: int
    active: bool = False    # Optional field


# Create instance
john = Customer('John', 'Doe', 31)
mike = Customer('Mike', 'Sanders', 28)

print(john > mike)  # False
print(john < mike)  # True
print(john >= mike)  # False
print(john <= mike)  # True
```
[[Go back]](#table-of-contents)

### Default Values for Mutable Fields
For fields that makes use of mutable types, like `lists`, you need to use the `field()` helper method with the `default_factory` argument set to method to call when instantiating the default value for the field.
```python
from dataclasses import dataclass, field

# Define a dataclass
@dataclass
class Customer:
    first_name: str
    last_name: str
    contacts: list[str] = field(default_factory=list)
    # calls list() when initializing field

# Create instance
john = Customer('John', 'Doe')
mike = Customer('Mike', 'Sanders')

# Both contacts are unique instances
print(john.contacts is mike.contacts)   # False
```
[[Go back]](#table-of-contents)

## Testing
### Assertions
Syntax
```python
assert expr, 'description'
```
Example
```python
def is_even(num):
    return num % 3 == 0

assert is_even(4), '4 should be even'
assert not is_even(5), '5 should not be even'
```
[[Go back]](#table-of-contents)

### Doctest
Doctest allows you to write tests inside docstrings.

`demo.py`
```python
def is_even(num):
    """
    >>> is_even(4)
    True

    >>> is_even(5)
    False
    """
    return num % 2 == 0
```
Terminal
```bash
$ python -m doctest -v demo.py
Trying:
    is_even(4)
Expecting:
    True
ok
Trying:
    is_even(5)
Expecting:
    False
ok
1 items had no tests:
    demo
1 items passed all tests:
   2 tests in demo.is_even
2 tests in 2 items.
2 passed and 0 failed.
Test passed.
```
[[Go back]](#table-of-contents)

### Unit Testing
Python provides `unittest` module for performing unit testing.

`foo.py`
```python
def is_even(num: int | float) -> bool:
    """Check if number is even"""
    if not type(num) in (int, float):
        raise ValueError('num should be an int or float')
    return num % 2 == 0
```
`test_foo.py`
```python
import unittest
from foo import is_even

class FooTests(unittest.TestCase):
    def test_is_even_on_even(self):
        """is_even(6) returns true"""
        self.assertEqual(is_even(6), True)

    def test_is_even_on_odd(self):
        """is_even(5) returns false"""
        self.assertEqual(is_even(5), False)

    def test_is_even_not_number(self):
        """is_even() should fail when argument not a number"""
        with self.assertRaises(ValueError):
            is_even('test')

if __name__ == '__main__':
    unittest.main()
```
Terminal
```bash
$ python test_foo.py -v
test_is_even_not_number (__main__.FooTests.test_is_even_not_number)
is_even() should fail when argument not a number ... ok
test_is_even_on_even (__main__.FooTests.test_is_even_on_even)
is_even(6) returns true ... ok
test_is_even_on_odd (__main__.FooTests.test_is_even_on_odd)
is_even(5) returns false ... ok

----------------------------------------------------------------------
Ran 3 tests in 0.001s

OK
```
[[Go back]](#table-of-contents)

### `setUp()` and `tearDown()`
These methods allows you to run code at every start and end of each test case.

`test_foo.py`
```python
import unittest

class FooTests(unittest.TestCase):
    def setUp(self) -> None:
        self.message = 'setup executed'
        return super().setUp()

    def tearDown(self) -> None:
        return super().tearDown()

    def test_if_setup_ran(self):
        self.assertEqual(self.message, 'setup executed')

if __name__ == '__main__':
    unittest.main()
```
Terminal
```bash
$ python test_foo.py -v
test_if_setup_ran (__main__.FooTests.test_if_setup_ran) ... ok

----------------------------------------------------------------------
Ran 1 test in 0.000s

OK
```
[[Go back]](#table-of-contents)

## File Operations
Examples in this section read the following example file.

`readme.html`
```
Sunday
Monday
Tuesday
Wednesday
Thursday
Friday
Saturday
```
[[Go back]](#table-of-contents)

### Reading
Read the entire file
```python
f = open('readme.html')
print(f.read())
# Sunday
# Monday
# Tuesday
# Wednesday
# Thursday
# Friday
# Saturday

f.close()
```
[[Go back]](#table-of-contents)

### Moving Cursor
Move the cursor using `seek()`
```python
f = open('readme.html')
f.seek(32)
print(f.read())
# Thursday
# Friday
# Saturday

f.close()
```
[[Go back]](#table-of-contents)

### Read Line
Read the file one line at a time. Also returns a trailing '\n' character.
```python
f = open('readme.html')
print(f.readline())     # Sunday\n
f.close()
```
[[Go back]](#table-of-contents)

### Read All Lines
Read all the lines and return them as a list. Also includes trailing '\n' characters.
```python
f = open('readme.html')
print(f.readlines())
# ['Sunday\n', 'Monday\n', 'Tuesday\n', 'Wednesday\n', 'Thursday\n', 'Friday\n', 'Saturday']

f.close()
```
[[Go back]](#table-of-contents)

### Check File Handler State
To check if the file handler is closed, use the `.closed` property.
```python
f = open('readme.html')
print(f.closed)         # False
print(f.readline())     # Sunday\n
f.close()

print(f.closed)         # True
print(f.readline())     # ValueError: I/O operation on closed file.
```
[[Go back]](#table-of-contents)


### Closing Files using `with`
Opening files using `with` makes it possible to close files automatically regardless of any error that might occur. This is the most preferred way to open files as it makes it safe against data loss.
```python
with open('readme.html') as file:
    print(file.readline())  # Sunday\n
    print(file.closed)      # False

print(file.closed)          # True
```
[[Go back]](#table-of-contents)

### Writing
To perform a write operation to a file, simply open it with a `w` flag as the second argument.
```python
with open('hello.txt', 'w') as file:
    file.write('Hello world!')
```
`hello.txt`
```
Hello world!
```
[[Go back]](#table-of-contents)

### Truncating
Trims/removes all the data after the cursor.
```python
filename = 'hello.txt'

with open(filename, 'w') as file:
    file.write('Hello world')   # Write Hello world

with open(filename, 'r+') as file:
    file.seek(5)    # Seek cursor to offset 5, before world
    file.truncate() # Remove the rest of data

with open(filename) as file:
    print(file.read())  # Hello
```
[[Go back]](#table-of-contents)

## CSV File Processing
### Reading with `reader`
Returns each row in the CSV file as a `list`

`customers.csv`
```
first_name,last_name,gender
John,Doe,male
Jane,Collins,female
```
`csv_demo.py`
```python
from csv import reader

with open('customers.csv') as file:
    customers = reader(file)
    for customer in customers:
        print(customer)
```
Output
```bash
$ python csv_demo.py 
['first_name', 'last_name', 'gender']
['John', 'Doe', 'male']
['Jane', 'Collins', 'female']
```
[[Go back]](#table-of-contents)

### Writing with `writer`
Write each row as a `list`

`csv_demo.py`
```python
from csv import writer

with open('customers.csv', 'w', newline='') as file:
    csv_writer = writer(file)
    csv_writer.writerow(['first_name', 'last_name', 'gender'])
    csv_writer.writerow(['John', 'Doe', 'male'])
    csv_writer.writerow(['Jane', 'Collins', 'female'])
```
`customers.csv`
```
first_name,last_name,gender
John,Doe,male
Jane,Collins,female
```
[[Go back]](#table-of-contents)

### Reading with `DictReader`
Returns each row as a `dict`

`customers.csv`
```
first_name,last_name,gender
John,Doe,male
Jane,Collins,female
```
`csv_demo.py`
```python
from csv import DictReader

with open('customers.csv') as file:
    customers = DictReader(file)
    for customer in customers:
        print(customer)
```
Output
```bash
$ python csv_demo.py 
{'first_name': 'John', 'last_name': 'Doe', 'gender': 'male'}
{'first_name': 'Jane', 'last_name': 'Collins', 'gender': 'female'}
```
[[Go back]](#table-of-contents)

### Writing with `DictWriter`
Write each row as a `dict`

`csv_demo.py`
```python
from csv import DictWriter

with open('customers.csv', 'w', newline='') as file:

    # Fields
    headers = ('first_name', 'last_name', 'gender')

    writer = DictWriter(file, fieldnames=headers)
    writer.writeheader()    # write fields

    writer.writerow({
        'first_name': 'John',
        'last_name': 'Doe',
        'gender': 'male'
    })
    writer.writerow({
        'first_name': 'Jane',
        'last_name': 'Colins',
        'gender': 'female'
    })
```
`customers.csv`
```
first_name,last_name,gender
John,Doe,male
Jane,Colins,female
```
[[Go back]](#table-of-contents)

## Serialization with `pickle`
Save object state into a file and reinstantiate it at a later time.
```python
import pickle

# sample class
class Customer:
    def __init__(self, first_name, last_name, gender):
        self.first_name = first_name
        self.last_name = last_name
        self.gender = gender

    def __repr__(self) -> str:
        return f'{self.first_name} {self.last_name}, {self.gender}'


# sample object
original = Customer('John', 'Doe', 'male')
print(original)     # John Doe, male

# serialize object into file
with open('customer.bin', 'wb') as file:
    pickle.dump(original, file)

# deserialize file into object
with open('customer.bin', 'rb') as file:
    saved_customer = pickle.load(file)
    print(saved_customer)       # John Doe, male
```
[[Go back]](#table-of-contents)

## Serialization with JSON
### Encoding JSON
```python
import json

original_dict = {
    'first_name': 'John',
    'last_name': 'Doe',
    'age': 32,
    'active': False,
    'balance': None
}

json_encoded = json.dumps(original_dict)
print(type(json_encoded))     # <class 'str'>
print(json_encoded)
# {"first_name": "John", "last_name": "Doe", "age": 32, "active": false, "balance": null}
```
[[Go back]](#table-of-contents)

### Decoding JSON
```python
import json

original_json = '{"first_name": "John", "last_name": "Doe", "age": 32, "active": false, "balance": null}'

json_decoded = json.loads(original_json)
print(type(json_decoded))   # <class 'dict'>
print(json_decoded)
# {"first_name": "John", "last_name": "Doe", "age": 32, "active": false, "balance": null}
```
[[Go back]](#table-of-contents)

## Asynchronous Programming
Python provides `asyncio` module for asynchronous I/O.
```python
import asyncio
```
[[Go back]](#table-of-contents)

### Coroutines
Coroutines are functions that can be executed asynchronously at runtime. They are the basic building blocks of any asynchronous Python program. To turn a function into a coroutine, simply use the `async` keyword.
```python
import asyncio

async def main():
    pass
```
[[Go back]](#table-of-contents)

### Event Loop
To execute a coroutine, it has to be run inside an event loop. This is accomplished by using `asyncio.run()`.
```python
import asyncio

async def main():
    print('Hello world')

asyncio.run(main())
```
[[Go back]](#table-of-contents)

### `await` keyword
Coroutines may execute other coroutines and wait for their execution to finish. To accomplish this, use the `await` keyword.
```python
import asyncio

async def main():
    print('Program start.')
    await long_process()    # will wait until it's finished
    print('Process end.')

async def long_process():
    await asyncio.sleep(5)
    print('Long process done.')

asyncio.run(main())
```
[[Go back]](#table-of-contents)

### Futures
Coroutines can also return values that might resolve at a later time.
```python
import asyncio

async def main():
    print('Sending mock HTTP request...')
    response = await web_call()     # wait for response

    print(response)  # Some text from the HTTP request

async def web_call():
    await asyncio.sleep(5)
    return 'Some text from the HTTP request'

asyncio.run(main())
```
[[Go back]](#table-of-contents)

### Creating tasks
To execute tasks asynchronously without having to wait for them to finish, use `asyncio.create_task()`. 

Do note that you still need to `await` all the tasks from the calling coroutine or else they might be terminated prematurely once the script ends.

`demo.py`
```python
import asyncio

async def main():
    print('Spawning coroutines...')
    counter_a = asyncio.create_task(start_counter('Red', 6))
    counter_b = asyncio.create_task(start_counter('Blue', 6))

    print('Spawning done. Waiting for coroutines to finish!')

    await counter_a
    await counter_b

    print('End of program.')

async def start_counter(name, limit):
    for i in range(1, limit + 1):
        print(f'{name}: {i}')
        await asyncio.sleep(1)

asyncio.run(main())
```
In this example, both `start_counter()` calls will execute concurrently without having to wait for the other to finish. 

Output:
```
$ python demo.py 
Spawning coroutines...
Spawning done. Waiting for coroutines to finish!
Red: 1
Blue: 1
Red: 2
Blue: 2
Red: 3
Blue: 3
Red: 4
Blue: 4
Red: 5
Blue: 5
Red: 6
Blue: 6
End of program.
```
[[Go back]](#table-of-contents)

### Threading with async
If you want to perform blocking I/O without having to block the event loop, you may opt to run it in a separate thread using `asyncio.to_thread()`.
```python
import asyncio
import requests

async def main():
    web_task = asyncio.to_thread(web_call)
    print('If you see then the thread is not blocked :)')

    await web_task
    print('Program end.')

def web_call():
    # Simulated api delay
    response = requests.get('https://hub.dummyapis.com/delay?seconds=10')
    print('Api call finished')

asyncio.run(main())
```
[[Go back]](#table-of-contents)

## `pip` Package Manager
### `pip list`
Lists all installed packages
```bash
# List all packages
$ pip list

# List all packages that are outdated
$ pip list --outdated
```
[[Go back]](#table-of-contents)

### `pip freeze`
List all install packages along with their version number, in a `requirements.txt` format.
```bash
$ pip freeze
```
[[Go back]](#table-of-contents)

### `pip show`
Show information for an installed package
```bash
$ pip show package-name
```
[[Go back]](#table-of-contents)

### `pip install`
Install package from [PyPi repository](https://pypi.org/).
```bash
# Install package
$ pip install package-name

# Install with version
$ pip install package-name==2.20.0

# Update existing package to latest version
$ pip install package-name --upgrade

# Install all packages listed in "requirements.txt" file
$ pip install -r requirements.txt
```
[[Go back]](#table-of-contents)

### `pip uninstall`
Uninstall a package from the system.
```bash
# Uninstall package
$ pip uninstall package-name

# Uninstall all packages listed in "requirements.txt" file
$ pip uninstall -y -r requirements.txt 
```
[[Go back]](#table-of-contents)

### Get `pip` version
```bash
$ pip --version
pip 23.0.1 from <path> (python 3.11)
```
[[Go back]](#table-of-contents)

### Upgrade `pip` version
```bash
$ python -m pip install --upgrade pip
```
[[Go back]](#table-of-contents)

## Virtual Environment with `venv`
Make a project-specific installation directory for all the packages your project needs.
### Create environment
```bash
$ python -m venv .venv
```
[[Go back]](#table-of-contents)

### Activate environment
Once activated, all `pip install` goes in `.venv` directory.
```bash
# Windows (git-bash)
$ source .venv/Scripts/activate

# Linux
$ source .venv/bin/activate
```
[[Go back]](#table-of-contents)

## Dependency Management with `pipenv`
`pipenv` manages your project dependencies as well as setting up virtual environments where they will be installed. Your dependencies will be stored in `Pipfile` and `Pipfile.lock` files.

### Install `pipenv`
```bash
$ pip install pipenv

# Virtual env directory will use current project directory
$ echo "export PIPENV_VENV_IN_PROJECT=1" >> ~/.bashrc
```
[[Go back]](#table-of-contents)

### Install dependency
```bash
# Default
$ pipenv install package-name

# Dev-dependency
$ pipenv install -d package-name

# Install specific version
$ pipenv install -d package-name==2.0.0

# Install all default dependencies
$ pipenv install

# Install both default and dev-dependencies
$ pipenv install -d

# Install all default packages (production)
$ pipenv install --ignore-pipfile 
```
[[Go back]](#table-of-contents)

### Synchronize virtual environment
```bash
# Create venv and install dependencies
$ pipenv sync

# Same, but also includes dev-dependencies
$ pipenv sync -d
```
[[Go back]](#table-of-contents)

### Update dependency
```bash
# Check dependencies if outdated
$ pipenv update --outdated

# Update all default dependency
$ pipenv update

# Update all default and dev dependencies
$ pipenv update -d

# Update default dependency
$ pipenv update package-name

# Update dev-dependency
$ pipenv update -d package-name
```
[[Go back]](#table-of-contents)

### Uninstall dependency
```bash
# Regular uninstall
$ pipenv uninstall package-name

# Dev dependency uninstall
$ pipenv uninstall -d package-name
```
[[Go back]](#table-of-contents)

### Activate virtual environment
```bash
$ pipenv shell
```
[[Go back]](#table-of-contents)

### Import from `requirements.txt`
```bash
$ pipenv install -r requirements.txt
```
[[Go back]](#table-of-contents)

### Show dependency graph
```bash
$ pipenv graph
```
[[Go back]](#table-of-contents)

### Check security vulnerabilities
```bash
$ pipenv check
```
[[Go back]](#table-of-contents)