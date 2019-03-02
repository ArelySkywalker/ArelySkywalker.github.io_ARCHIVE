---
layout: code
title: Daily Coding Problems
---

I like to challenge myself everyday with coding problems. I will find challenges online and solve them. Once I do, I'll post them here! If you have any questions or any cool challenges for me, just shoot me an email! :)

There are many different ways to solve these problems. This is just my code that I time myself to complete within an hour. If you have better solutions, feel free to email me and I'll mention you and your code in the problem!

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
# k = 17_
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