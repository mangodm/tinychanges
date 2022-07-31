---
toc: true
layout: post
description: How to write Python code efficiently
categories: [python, datacamp, data-engineering, en]
title: (EN)Writing Efficient Python Code
---

These are notes from the [Writing Efficient Python Code](https://www.datacamp.com/courses/writing-efficient-python-code) course by DataCamp.

This course covers the following topics:

- How to write clean, fast, and efficient Python code
- How to profile a code for bottlenecks
- How to eliminate bottlenecks and bad design patterns

---
# Foundations for efficiencies

- In the context of this course, efficient Python code is:
    - executing quickly for the task at hand
    - minimizing the memory footprint
    - following Python’s coding style principles (i.e., PEP)

## Building with built-ins

### Python built-in components

- Built-in components are referred as the Python Standard Library, and the library comes with every Python installation.
- Some built-in components include:
    - Built-in types (e.g., `list`, `tuple`, `set`, and others)
    - Built-in functions (e.g., `print()`, `len()`, `range()`, and others)
    - Built-in modules (e.g., `os`, `sys`, `itertools`, and others)
- Built-ins have been optimized to work within the Python language itself, so using them is recommended, if one exists.

### Useful built-ins: range()

- It returns a sequence of the given number between the given range.
- syntax
    - `range(stop)`: create a sequence of numbers from 0 to a stop value (which is **exclusive**)
    - `range(start, stop, step)`: create a sequence of numbers from a start value to a stop value (which is **exclusive**) with a step size.
- exercises
    
    ```python
    # Create a list of people that arrived at a party we're hosting.
    names = ['Jerry', 'Kramer', 'Elaine', 'George', 'Newman']
    
    # Create an empty list to store the indexed list.
    indexed_names = []
    
    # Use a for loop to get the indexed list.
    for i in range(len(names)):
        index_name = (i, names[i])
        indexed_names.append(index_name)
    ```
    

### Useful built-ins: enumerate()

- It returns an indexed list.
- syntax
    - `enumerate(iterable, start = 0)`
- exercises
    
    ```python
    # Create an empty list to store the indexed list.
    indexed_names = []
    
    # Rewrite the for loop to use enumerate
    for i, name in enumerate(names):
    	index_name = (i, name)
    	indexed_names.append(index_name)
    
    # Rewrite the above for loop using list comprehension
    indexed_names_comp = [(i, name) for i, name in enumerate(names)]
    
    # Unpack an enumerate object with a starting index of one
    indexed_names_unpack = [*enumerate(names, start = 1)]
    ```
    

### Useful built-ins: map()

- It returns a map object of the results after applying the given function to each item of a given iterable.
- syntax
    - `map(function, iterable)`
- exercises

    ```python
    # Create a list of people that arrived at a party we're hosting.
    names = ['Jerry', 'Kramer', 'Elaine', 'George', 'Newman']

    names_uppercase = []

    # Use a for loop to convert all the letters in each name to uppercase.
    for name in names:
        names_uppercase.append(name.upper())

    # Use a map function to convert each letter to uppercase.
    names_map = map(str.upper, names)

    # Unpack names_map into a list
    names_uppercase = [*names_map]
    ```

## The power of NumPy arrays

### Overview

- NumPy arrays provide a fast and memory efficient alternative to Python lists.
- NumPy arrays are homogeneous, which means that the items in an array must be of the same type. It reduces memory consumption.

### Broadcasting

- It refers to a NumPy Array’s ability to vectorize operations, so they are efficiently performed over the entire arrays.
- exercises

    ```python
    # Create a 2-D array 
    nums = np.array([[1, 2, 3, 4, 5], [6, 7, 8, 9, 10]])

    # Use a for loop to multiply each element by 2
    nums_dbl1 = []
    for num in nums:
        nums_dbl1.append(num * 2)

    # Use a broadcasting to double element efficiently.
    nums_dbl2 = nums * 2
    ```

### Boolean indexing

- It returns an array object of Boolean type, and this will be useful in filtering desired element values.
- exercises

    ```python
    nums = np.array([1, 2, 3, 4, 5])

    # Use a for loop to filter elements greater than six.
    nums_filtered1 = []
    for num in nums:
        if num > 2:
            nums_filtered.append(num)

    # Use a boolean indexing to filter elements greater than six efficiently.
    nums_filtered2 = nums[nums > 2]
    ```

---