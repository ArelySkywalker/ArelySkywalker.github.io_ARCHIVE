---
layout: default
title: Arely Miramontes Rodríguez
---

# Hi, I'm Arely. Nice to meet you!

I am a Web Developer for Powderkeg, based in Madison Wisconsin. I graduated with a Bachelor's in Computational Mathematics with Computer Science at the University of New Mexico. Tech and Sofware has always been my passion. I thrive to build immersive and beautiful websites through carefully crafted code.

## Daily Coding Challenge

Given an array of integers, return a new array such that each element at index i of the new array is the product of all the numbers int he original array except the one at i.

```python
# Example:
# input = [1, 2, 3, 4, 5] => output = [120, 60, 40, 30, 24]
# input = [3, 2, 1] => output = [2, 3, 6]
```

An easy way to do this would to be to loop through the array, get the product of the array, and for i, divide the product by i to get the new index. But I want to solve this without using division, because what if i = 0?

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

This could also easily be solved with JavaScript :)

```js
function indexProductExceptI(array) {
    var resultArray = []; product;
    for(var i = 0; i < array.length; i++) {
        product = 1;
        for(var j = 0; j < array.length; j++) {
            if(i !== j) product *= array[j];
        }
        resultArray.push(product);
    }
    return resultArray;
}
```

Output:
```
[120, 60, 40, 30, 24]
[2, 3, 6]
```
