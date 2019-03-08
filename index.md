---
layout: default
title: Arely Miramontes Rodríguez
---

# Hi, I'm Arely

I am a Web Developer for Powderkeg, based in Madison Wisconsin. I graduated with a Bachelor's in Computational Mathematics with Computer Science at the University of New Mexico. Tech and Sofware has always been my passion. I built this site to post coding challenges that I have solutions to - these are very useful to help you prepare for developer interviews, whether you want to be a Web Developer or Software Engineer. Reach out to me if you have any questions or a fun challenge for me. Enjoy!



## Current Coding Challenge

There are many different ways to solve these problems. This is just my code that I time myself to complete within an hour. If you have better solutions, feel free to email me and I'll mention you and your code in the problem!

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

