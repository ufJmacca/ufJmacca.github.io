---
title: Advent Calandar Day 1
date: 2022-12-04 10:00:00 +1100
categories: [advent 2022, python]
tags: [python,openai] 
---

# Advent Day 1

In this article, we'll show you how to use Python and some of its popular packages to solve the first day of Advent Calandar of 2022. In this challenge we are asked to find the elf carrying the highest calories. We'll also show you how to use the same code to find the total calories of the top three elves for part 2. Find the snippet [here](https://github.com/ufJmacca/advent2022/blob/main/day-1.ipynb)

We'll be using the requests, tomli and print functions in Python to achieve our goal. First, we'll open the secrets.toml file and read the day-1 cookie using the tomli package. This cookie will be used in the request.get() function to retrieve the data from the Advent of Code website.

Next, we'll use a for loop to iterate through each line in the retrieved data. If the line is blank, we'll add the current calories to a list and check if it's higher than the current highest calories. If it is, then we'll update the highest_calories variable. We're also resetting the calories variable to 0 so that it doesn't accumulate between lines.

Finally, we'll use the print() function to print out the highest_calories variable and the sum of the top three elements of the calories_list. This will give us the total calories of the top three highest numbers.

And that's it! With just a few lines of code, we were able to quickly solve the first day of the 2022 Advent calandar.

The code for this challenge, and the others I completed in 2022 can be found on [my github](https://github.com/ufJmacca/advent2022)