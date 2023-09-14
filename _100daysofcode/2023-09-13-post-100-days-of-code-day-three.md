---
title: "100 Days of Code - Day Three"
date: 2023-09-13
categories:
  - Blog
  - 100DaysOfCode
tags:
  - python
  - 100daysofcode
---

Day three is done! Today's topic was control flow and logical operators. I'm familiar with these concepts from other languages, but it's good to get a refresher.

Items covered today:
- if/elif/else
- nested if/elif/else
- logical operators (and, or, not)
- count() method
- modulo operator (%)

The final project for today was a _choose your own adventure_ style game to practice the concepts we learned today. I loved these books as a kid, so this was a fun project to work on. I'm sure there are more efficient ways to write this with classes / data structures, but I'm happy with how it turned out.

{% highlight Python %}
print("Welcome to Treasure Island.")
print("Your mission is to find the treasure.")

GAME_OVER_MSG="\nGame Over..."

CROSSROADS_MSG = "\nYou're at a crossroads, where do you want to go?" + \
                 "\nType 'left' or 'right': "
CROSSROADS_DEATH_MSG = f"\nYou fell into a hole! {GAME_OVER_MSG}"

CREEK_MSG = "\nYou come to a rushing creek. Should you try to cross or wait it out?" + \
            "\nType 'swim' or 'wait': "
CREEK_DEATH_MSG = f"\nYou were attacked by a trout! {GAME_OVER_MSG}"

DOORWAY_MSG = "\nGood decision. The creek slows and you make it across successfully." + \
              "\nYou are now faced with three doors. Which doorway do you choose?" + \
              "\nType 'red', 'yellow', or 'blue': "
BLUE_DOOR_MSG=f"\nYou were eaten by a grue! {GAME_OVER_MSG}"
RED_DOOR_MSG=f"\nYou were burned alive! {GAME_OVER_MSG}"
YELLOW_DOOR_MSG="\nYou win!"

decision = input(CROSSROADS_MSG).lower()

if decision == "left":
  decision = input(CREEK_MSG).lower()

  if decision == "wait":
    decision = input(DOORWAY_MSG).lower()

    if decision == "yellow":
      print(YELLOW_DOOR_MSG)
    elif decision == "red":
      print(RED_DOOR_MSG)
    elif decision == "blue":
      print(BLUE_DOOR_MSG)
    else:
      print(GAME_OVER_MSG)

  else:
    print(CREEK_DEATH_MSG)

else:
  print(CROSSROADS_DEATH_MSG)
{% endhighlight %}
