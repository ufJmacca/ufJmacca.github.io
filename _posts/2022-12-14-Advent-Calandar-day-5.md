---
title: Advent Calandar Day 5
date: 2022-12-14 10:00:00 +1100
categories: [advent 2022, python]
tags: [python,openai] 
---

# Advent Day 5

Are you stuck trying to find your way through the puzzles of the 2022 Advent of Code? Have no fear! This blog post is here to help you with day 5 of the 2022 Advent of Code. We'll be looking at how to move crates in stacks using Python. 

We'll start off by importing the necessary libraries. 

```python
import requests
import tomli
import re 
```

Next, we'll open a file called `secrets.toml` and load the data into a variable called `config`. 

```python
with open("secrets.toml", mode="rb") as fp:
    config = tomli.load(fp)
```

We'll then make a request to the URL and store the response in a variable called `r`. We'll also set a `cookie` header with the data stored in the `config` variable. 

```python
r = requests.get('https://adventofcode.com/2022/day/5/input', headers={'cookie': config['day-2']['cookie']})
```

We'll now set up some variables to store the data we need. 

```python
cnt = 0
stacks = []
movements = []
```

We'll then loop through the response and store the data in the respective variables. 

```python
for line in r.text.splitlines():
    if line == '':
        cnt += 1
    elif cnt == 0:
        stacks.append(line)
    else:
        movements.append(re.findall('\d+', line))
```

Now that we have the data, we'll need to find the positions of the crates in the stack. We'll use regular expressions for this. 

```python
matches = re.match('.*?(\d)', stacks[-1:][0])

end_position = 0
index_locations = {}

while matches:
    end_position += matches.end(1)
    index_locations[matches.group(1)] = end_position
    matches = re.match('.*?(\d)', stacks[-1:][0][end_position:])
```

Now that we know the positions of the crates, we can move on to the actual task of moving the crates. 

We'll start by setting up a dictionary to store the stacks. 

```python
stacks_dict = {}

for index, _ in index_locations.items():
    stacks_dict[index] = list()
```

We'll then loop through the stacks and store the data in the dictionary. 

```python
for stack in stacks[-2::-1]:
    for key, value in index_locations.items():
        if stack[value-1:value] != ' ':
            stacks_dict[key].append(stack[value-1:value])
```

Now, we can move on to the actual task of moving the crates. 

Part 1 - Moving one crate at a time

```python
for crate, origin, destination in movements:
    for i in range(0, int(crate)):
        stacks_dict[destination] += stacks_dict[origin].pop()
```

Part 2 - Moving entire stack at once

```python
for crates, origin, destination in movements:
    stacks_dict[destination] += stacks_dict[origin][int(crates)*-1:]
    del stacks_dict[origin][int(crates)*-1:]
```

We'll then loop through the dictionary and print out the data. 

```python
for _, stack in stacks_dict.items():
    print(stack[-1])
```

That's all there is to it! With this code, you'll be able to move crates in stacks with ease.

The code for this challenge, and the others I completed in 2022 can be found on [my github](https://github.com/ufJmacca/advent2022)