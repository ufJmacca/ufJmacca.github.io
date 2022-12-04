---
title: Advent Calandar Day 3
date: 2022-12-04 10:00:00 +1100
categories: [advent 2022, python]
tags: [python,openai] 
---

# Advent Day 3

Today's challenge we are asked to find a common string within components of a rucksack and then calculate the value of that item. 

To complete the challenge, we first read in the secrets.toml file and use the requests library to pull in a list of rucksack contents. 

We then create a function to calculate the common char value of the items in the rucksack. This is done by taking the character and using the ord() function to get its ASCII value, and then subtracting either 38 (for upper case characters) or 96 (for lower case characters) to get the common char value.

We then loop through the rucksacks and calculate the common char value of the items in each rucksack and store the values in a list. We then sum up the list and print out the total common value to complete part 1 of todays challenge.

For part two, we then repeat the same process to calculate the common char value of items in a group of three rucksacks. We loop through the group of rucksacks and calculate the common char value of the items in each group and store the values in a list. We then sum up the list and print out the total common value to complete part 2 of todays challenge.