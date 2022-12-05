---
title: Advent Calandar Day 4
date: 2022-12-06 10:00:00 +1100
categories: [advent 2022, python]
tags: [python,openai] 
---

# Advent Day 4

Are you stuck trying to find your way through the puzzles of the 2022 Advent of Code? Have no fear! This blog post is here to help you with day 4 of the 2022 Advent of Code.

We'll be using Python to help solve this puzzle. First, we'll need to import some Python libraries. We'll be using the requests library, the tomli library, and the re library.
```
import requests
import tomli
import re 
```

Next, we'll open the secrets.toml file and store it in the config variable. We'll then use the requests library to get the input from the website.
```
with open("secrets.toml", mode="rb") as fp:
    config = tomli.load(fp)

r = requests.get('https://adventofcode.com/2022/day/4/input', headers={'cookie': config['day-2']['cookie']})
```

We'll then parse the data into an array of assignment pairs by using a regular expression.
```
assignment_pairs = []

for line in r.text.splitlines():
    assignment_pairs.append([int(x) for x in re.split('[-,]+', line)])
```

Now, we'll write a function. The function will take an array of items and a function (either min or max) as parameters. This function will return the index of the item in the array that matches the min or max value.
```
def get_value_index(items, func):
    if func == 'min':
        value = min(items)
    else:
        value = max(items)

    return [i for i, val in enumerate(items) if val == value]
```

In the first part of the code, the program iterates through each line in the text, and uses the defined function to check if the values are fully contained within each other. If they are, it stores the outcome as “fully contained” in a list, otherwise it stores an empty string: 
```
outcomes = []

for assignment in assignment_pairs:
    min_index_location = get_value_index([assignment[0], assignment[2]], 'max')

    if len(min_index_location) == 1:
        if min_index_location[0] == 0:
            if assignment[1] <= assignment[3]:
                outcome = 'fully contained'
            else:
                outcome = ''
        elif min_index_location[0] == 1:
            if assignment[3] <= assignment[1]:
                outcome = 'fully contained'
            else:
                outcome = ''
    else:
        outcome = 'fully contained'

    outcomes.append(outcome)

print(outcomes.count('fully contained'))
```

In the second part of the code, the program checks if the values are partially contained within each other. If they are, it stores the outcome as “partially contained” in a list, otherwise it stores an empty string: 
```
outcomes = []

for assignment in assignment_pairs:
    if assignment[0] <= assignment[3] and assignment[1] >= assignment[2]:
        outcome = 'partially contained'
    else:
        outcome = ''
    outcomes.append(outcome)

print(outcomes.count('partially contained'))
```

We hope this blog post has been helpful in helping you solve the 2022 Advent of Code day 4 puzzle. Good luck!

The code for this challenge, and the others I completed in 2022 can be found on [my github](https://github.com/ufJmacca/advent2022)