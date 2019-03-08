---
layout: code
title: Daily Coding Problems
---

I like to challenge myself everyday with coding problems. I will find challenges online and solve them. Once I do, I'll post them here! If you have any questions or any cool challenges for me, just shoot me an email! :)

There are many different ways to solve these problems. This is just my code that I time myself to complete within an hour. If you have better solutions, feel free to email me and I'll mention you and your code in the problem!

## Problem #5
### Level: Medium

Given the mapping a = 1, b = 2, ... z = 26, and an encoded message, count the number of ways it can be decoded.

For example, the message '111' would give 3, since it could be decoded as 'aaa', 'ka', and 'ak'.

You can assume that the messages are decodable. For example, '001' is not allowed.

This looks like a problem that can be solved with recursion. So if a string starts with zero, there's no valid encoding so let's return zero. If the string's length is less than or equal to 1, the number of encodings is 1. If the string is 2 or greater, let's go through the letters or digits, and cound the encodings.

#### View Solution:

```python
def numEncodings(s):
    # This covers if the string starts with 0
    if s.startswith('0'):
        return 0
    # This covers if the string is empty
    elif len(s) <= 1:
        return 1

    total = 0

    if int(s[:2]) <= 26:
        total += numEncodings(s[2:])

    total += numEncodings(s[1:])
    return total

n = '111'
print(numEncodings(n))
```

Output:
```
3
```



## Problem #4
### Level: Medium

cons(a, b) constructs a pair, and car(pair) and cdr(pair) returns the first and last element of that pair. For example, car(cons(3, 4)) returns 3, and cdr(cons(3, 4)) returns 4.

Given this implementation of cons:

```
#   def cons(a, b):
#       def pair(f):
#           return f(a, b)
#       return pair
```

Implement car and cdr.

 We can simply create nested functions that takes a pair and returns First or Last.

#### View Solution:

```python
def cons(a, b):
    def pair(f):
        return f(a, b)
    return pair

def car(pair):
    def returnFirst(a,b):
        return a 
    return pair(returnFirst)

def cdr(pair):
    def returnLast(a,b):
        return b 
    return pair(returnLast)


print(car(cons(3,4)))
print(cdr(cons(3,4)))
```

Output:
```
3
4
```


## Problem #3
### Level: Hard

Given an array of integers, find the first missing positive integer in linear time and constant space. In other words, find the lowest positive integer that does not exist in the array. The array can contain duplicates and negative numbers as well.

You can modify the input array in-place.

```
# Example:
# input = [3, 4, -1, 1] => output = 2
# input = [1, 2, 0] => output = 3
```

Since the first missing positive number must be between 1 and len(array) + 1, we can ignore any negative numbers and numbers larger than len(array). By the end of the process, the positive numbers should be grouped together at the beginning of the array. 

#### View Solution:

```python
def findAmissingPositiveInteger(array):
    if not array:
        return 1
    for i, num in enumerate(array):
        while i + 1 != array[i] and 0 < array[i] <= len(array):
            v = array[i]
            array[i], array[v - 1] = array[v - 1], array[i]
            array[v - 1] = v
            if array[i] == array[v - 1]:
                break
    for i, num in enumerate(array, 1):
        if num != i:
            return i
    return len(array) + 1
```

Output:
```
2
3
```

This would take O(N) since we swap each number at most once. 


## Problem #2
### Level: Hard

Given an array of integers, return a new array such that each element at index i of the new array is the product of all the numbers int he original array except the one at i.

```
# Example:
# input = [1, 2, 3, 4, 5] => output = [120, 60, 40, 30, 24]
# input = [3, 2, 1] => output = [2, 3, 6]
```

An easy way to do this would to be to loop through the array, get the product of the array, and for i, divide the product by i to get the new index. But I want to solve this without using division.

#### View Solution:

```python
def indexProductExceptI(array):
    resultArray = []
    for i in range(len(array)):
        product = 1
        for j in range(len(array)):
            if i != j: product *= array[j]
        resultArray.append(product)
    return resultArray
```


Output:
```
[120, 60, 40, 30, 24]
[2, 3, 6]
```

This would take O(N^2). 

**Challenge for you:** Can you come up with a new function that would run in O(N) time and space?

## Problem #1
### Level: Easy

Given a list of numbers and a number k, return whether any two numbers from the list add up to k.

```
# Example:
# given [10, 15, 3, 7]
# k = 17
# return true since 10 + 7 is 17
```
We just want to loop through the array and test the sum, once we find an instance where we find a sum match, return true

#### View Solution:

```python
def findASum(array, sum):
    for i in range(len(array)):
        for j in range(len(array)):
            if i != j and array[i] + array[j] == sum:
                return True
    return False

numbers = [ 10, 15, 3, 7 ]
k = 22

findASum(numbers, k)
```

Output:
```
True
```

This would take O(N^2).