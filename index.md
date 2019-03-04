---
layout: default
title: Arely Miramontes Rodríguez
---

# Hi, I'm Arely

I am a Web Developer for Powderkeg, based in Madison Wisconsin. I graduated with a Bachelor's in Computational Mathematics with Computer Science at the University of New Mexico. Tech and Sofware has always been my passion. I built this site to post coding challenges that I have solutions to - these are very useful to help you prepare for developer interviews, whether you want to be a Web Developer or Software Engineer. Reach out to me if you have any questions or a fun challenge for me. Enjoy!



## Today's Coding Challenge

There are many different ways to solve these problems. This is just my code that I time myself to complete within an hour. If you have better solutions, feel free to email me and I'll mention you and your code in the problem!

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

