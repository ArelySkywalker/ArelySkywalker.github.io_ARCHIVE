---
layout: default
title: Arely Miramontes Rodríguez
---

# Hi, I'm Arely

I am a Web Developer for Powderkeg, based in Madison Wisconsin. I graduated with a Bachelor's in Computational Mathematics with Computer Science at the University of New Mexico. Tech and Sofware has always been my passion. I built this site to post coding challenges that I have solutions to - these are very useful to help you prepare for developer interviews, whether you want to be a Web Developer or Software Engineer. Reach out to me if you have any questions or a fun challenge for me. Enjoy!



## Today's Coding Challenge

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
