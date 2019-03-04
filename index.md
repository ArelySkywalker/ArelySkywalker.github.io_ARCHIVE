---
layout: default
title: Arely Miramontes Rodríguez
---

# Hi, I'm Arely

I am a Web Developer for Powderkeg, based in Madison Wisconsin. I graduated with a Bachelor's in Computational Mathematics with Computer Science at the University of New Mexico. Tech and Sofware has always been my passion. I built this site to post coding challenges that I have solutions to - these are very useful to help you prepare for developer interviews, whether you want to be a Web Developer or Software Engineer. Reach out to me if you have any questions or a fun challenge for me. Enjoy!



## Today's Coding Challenge

There are many different ways to solve these problems. This is just my code that I time myself to complete within an hour. If you have better solutions, feel free to email me and I'll mention you and your code in the problem!

Given an array of integers, find the first missing positive integer in linear time and constant space. In other words, find the lowest positive integer that does not exist in the array. The array can contain duplicates and negative numbers as well.

You can modify the input array in-place.

```
# Example:
# input = [3, 4, -1, 1] => output = 2
# input = [[1, 2, 0] => output = 3
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
