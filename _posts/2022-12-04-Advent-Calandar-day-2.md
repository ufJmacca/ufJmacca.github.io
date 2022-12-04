---
title: Advent Calandar Day 2
date: 2022-12-04 10:00:00 +1100
categories: [advent 2022, python]
tags: [python,openai] 
---

# Advent Day 2

Today we are going to take a look at a [code snippet](https://github.com/ufJmacca/advent2022/blob/main/day-2.ipynb) that helps us solve day 2 of the Advent of Code 2022 challenge.

The code starts off by importing some important libraries and packages – requests, tomli, and pandas. We then open the secrets.toml file and use the tomli library to read it. We use the requests library to get the input from the Advent of Code website and then we split the input into an array of strings. 

Next, we create a dataframe using the array of strings and assign columns for opponent and response. Then, we define a function called shape which maps the opponent and response values to their respective shapes. We also define a function called game_result which calculates the result for each game and stores it in a new column in the dataframe. Finally, we print out the sum of all the results. 

For part 2, we modify the shape and game_result functions to account for the new values. The result is then stored in a new column in the dataframe and the sum of all the results is printed out. 

And that’s how we solve the Advent of Code 2022 Day 2 puzzle using Python! By breaking the problem down into smaller pieces, we were able to come up with a solution.

The code for this challenge, and the others I completed in 2022 can be found on [my github](https://github.com/ufJmacca/advent2022)