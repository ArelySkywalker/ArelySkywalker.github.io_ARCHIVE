---
layout: index
title: Arely Miramontes Rodríguez
---

# Hi, I'm Arely

I am a Web Developer for Powderkeg, based in Madison Wisconsin. I graduated with a Bachelor's in Computational Mathematics with Computer Science at the University of New Mexico. Tech and Sofware has always been my passion. I built this site to post coding challenges that I have solutions to - these are very useful to help you prepare for developer interviews, whether you want to be a Web Developer or Software Engineer. Reach out to me if you have any questions or a fun challenge for me. Enjoy!



## Current Coding Challenge

There are many different ways to solve these problems. This is just my code that I time myself to complete within an hour. If you have better solutions, feel free to email me and I'll mention you and your code in the problem!

* * *

**Run-length encoding is a fast and simple method of encoding strings. The basic idea is to represent repeated successive characters as a single count and character. For example, the string "AAAABBBCCDAA" would be encoded as "4A3B2C1D2A".**

**Implement run-length encoding and decoding. You can assume the string to be encoded have no digits and consists solely of alphabetic characters. You can assume the string to be decoded is valid.**

First we want to check if the input does not contain numbers, if it doesn't, we want to encode. Else, decode. 

We want to have a pointer on the start position of the string and a pointer on the next position from start. While the length of the string is greateer than 0, we want to loop through and check if the start letter st[0] and the next letter st[i] is equal to one another, if it is, let's add i to get a count of the same letter.

_NOTE: notice that I start i as 0, that's because our first check case will be start equal to start, if we started i = 1 which is the second element, we wouldn't get a correct count._

Once this while loop ends, we want to concatanate our count i plus our start letter. After this, we remove everything from position i to start, leaving us with 'BBBCCDAA'. Since st still exists, we will continue with our while loop, and our counter i gets reset to 0. We keep doing this process until len(st) is equal to 0. Return your encoded message.

If your string does contain numbers, we will decode. We can decode by using the join method.

#### View Solution:

```python
def runLengthEncodeDecode(st):

    # if the string contains no numbers, encode
    if st.isalpha():  

        encoded = ''
        while st:
            i = 0
            while i < len(st) and st[0] == st[i]:
                i += 1

            encoded += str(i) + st[0]
            st = st[i:]

        return encoded
    
    # decode since string contains numbers
    else:  

        return ''.join(c * int(n) for n, c in zip(st[::2], st[1::2]))
    
print(runLengthEncodeDecode('AAAABBBCCDAA'))
print(runLengthEncodeDecode('4A3B2C1D2A'))
```

Output:
```
4A3B2C1D2A
AAAABBBCCDAA
```

