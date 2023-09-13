---
title: "100 Days of Code - Day Two"
categories:
  - Blog
  - 100DaysOfCode
tags:
  - python
  - 100daysofcode
---

Day two and we're on data type and string manipulation. Lots and lots (and lots) of type conversions happening as part of the exercises today.

I'm pretty surprised at the pace of the course so far (as it is a beginner course) but it is also a bootcamp, so I guess that makes sense.

Today's project was a simple CLI-based Tip Calculator.

{% highlight Python %}
print("Welcome to the tip calculator.")

total_bill=float(input("What was the total bill? "))
tip_percentage=float(input("What percentage would you like to tip? "))
total_diners=int(input("How many people are splitting the bill? "))

tip_amount=(total_bill * (tip_percentage/100))
subtotal=total_bill + tip_amount
total_per_person=(subtotal / total_diners)

print(f"Each person should pay: ${total_per_person:.2f}")
{% endhighlight %}

The problem with doing exercises like this as someone who has coded before, is that I'm constantly thinking about things that aren't relevant at this point such as input validation. I'm sure that we'll get to that later in the course, but it's hard to not think about it now.

This is the kind of thing that I want to do, but I know we'll get there:

{% highlight Python %}
def get_float_input(prompt: str) -> float:
    """Get a float input from the user with error handling."""
    while True:
        try:
            value = float(input(prompt))
            if value < 0:
                raise ValueError("Please enter a non-negative value.")
            return value
        except ValueError as e:
            print(f"Invalid input. {e}")

def get_int_input(prompt: str) -> int:
    """Get an integer input from the user with error handling."""
    while True:
        try:
            value = int(input(prompt))
            if value <= 0:
                raise ValueError("Please enter a positive integer.")
            return value
        except ValueError as e:
            print(f"Invalid input. {e}")

print("Welcome to the tip calculator.")

# Get inputs from the user
total_bill = get_float_input("What was the total bill? $")
tip_percentage = get_float_input("What percentage would you like to tip? ")
total_diners = get_int_input("How many people are splitting the bill? ")

# Calculate the tip amount and total per person
tip_amount = total_bill * (tip_percentage / 100)
subtotal = total_bill + tip_amount
total_per_person = subtotal / total_diners

print(f"Each person should pay: ${total_per_person:.2f}")
{% endhighlight %}

The exercises are enjoyable, but I'm really looking forward to the more project-oriented portions of the course. Onwards!
