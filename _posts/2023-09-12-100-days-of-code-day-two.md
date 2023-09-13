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

The exercises are enjoyable, but I'm really looking forward to the more project-oriented portions of the course. Onwards!