---
layout: default
title: Arely Miramontes Rodríguez
---

# Hi, I'm Arely

I am a Web Developer for Powderkeg, based in Madison Wisconsin. I graduated with a Bachelor's in Computational Mathematics with Computer Science at the University of New Mexico. Tech and Sofware has always been my passion. I built this site to post coding challenges that I have solutions to - these are very useful to help you prepare for developer interviews, whether you want to be a Web Developer or Software Engineer. Reach out to me if you have any questions or a fun challenge for me. Enjoy!



## Current Coding Challenge

There are many different ways to solve these problems. This is just my code that I time myself to complete within an hour. If you have better solutions, feel free to email me and I'll mention you and your code in the problem!

There exists a staircase with N steps, and you can climb up either 1 or 2 steps at a time. Given N, write a function that returns the number of unique ways you can climb the staircase. The order of the steps matters.

or example, if N is 4, then there are 5 unique ways:

*   1, 1, 1, 1
*   2, 1, 1
*   1, 2, 1
*   1, 1, 2
*   2, 2

What if, instead of being able to climb 1 or 2 steps at a time, you could climb any number from a set of positive integers X? For example, if X = {1, 3, 5}, you could climb 1, 3, or 5 steps at a time.

Let f(n) be the number of different ways to climb n stairs. How can we reach the nth stair?

1. Bet at the (n-2) stair, then climb 2 steps
2. Bet at the (n-1) stair, then climb 1 step
For (1), number of ways to reach the the (n-2) stair is f(n-2)
For (2), number of ways to reach the the (n-1) stair is f(n-1)

f(n) = f(n-1) + f(n-2) + .... We can use this Fibonacci sequence to help up find the number of ways it would take to reach the Nth step given a set of rules. 

#### View Solution:

```python
def staircase(n, X):
    S = [0 for _ in range(n + 1)]
    S[0] = 1
    for i in range(n + 1):
        S[i] += sum(S[i - x] for x in X if i - x > 0)
        S[i] += 1 if i in X else 0
    return S[-1]

steps = 4
rules = {1,2}
rules2 = {1,3,5}

print(staircase(steps,rules))
print(staircase(steps,rules2))
```

Output:
```
5
3
```

