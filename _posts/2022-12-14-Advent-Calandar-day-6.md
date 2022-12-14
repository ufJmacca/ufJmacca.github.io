---
title: Advent Calandar Day 5
date: 2022-12-14 10:00:00 +1100
categories: [advent 2022, python]
tags: [python,openai] 
---

# Advent Day 6

Today we are going to be looking at the Advent of Code problem from Day 6. This problem involves finding the start of a packet and the start of a message in a string of characters. We will be using Python to solve this problem, so let's dive right in!

The first step is to read in the input string. We can do this using the `requests` library:

```python
import requests

r = requests.get('https://adventofcode.com/2022/day/6/input', headers={'cookie': config['day-2']['cookie']})

signal = r.text
```

We also create a helper function to check if a string is composed of unique characters. This will come in handy when checking our input string for the start of the packet and the start of the message:

```python
def unique_string(string):
    characters = Counter(string)
    if len(characters) == len(string):
        return True
    else:
        return False
```

Now that we have the input string and the helper function, we can start looking for the start of the packet. To do this, we iterate through the input string and check for a unique 4-character string:

```python
# Part 1 - Start of Packet
for i in range(len(signal)-4):

    if unique_string(signal[0+i:4+i]):
        print(i + 4)
        break
```

Finally, we can use the same approach to find the start of the message. This time, however, we look for a unique 14-character string:

```python
# Part 2 - Start of message
for i in range(len(signal)-14):

    if unique_string(signal[0+i:14+i]):
        print(i + 14)
        break
```

And that's it! With a few lines of Python code, we were able to find the start of the packet and the start of the message in the input string. This is just one example of the power of Python when it comes to solving real-world problems.

The code for this challenge, and the others I completed in 2022 can be found on [my github](https://github.com/ufJmacca/advent2022)