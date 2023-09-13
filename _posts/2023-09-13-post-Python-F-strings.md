---
title: "Understanding Python F-strings: A Beginner's Guide"
date: 2023-09-13
classes: wide
categories:
  - Blog
tags:
  - python
---

I was recently asked to put together a small blog post explaing f-strings, so that's just what I'm doing. 

### What are F-strings?

F-strings, introduced in Python 3.6, are a way to embed expressions inside string literals. They come prefixed with the letter 'f', which is where the name "f-strings" comes from.

### Why are F-strings Useful?

1. **Readability**: F-strings enhance the readability of your code by letting you directly embed variables into strings. This eliminates the need for older methods like `.format()` or the `%` formatting.
2. **Conciseness**: They significantly reduce the amount of code you need to format a string.
3. **Performance**: Typically, f-strings offer better performance when compared to other string formatting methods.

### How to Use F-strings?

To craft an f-string, simply prefix your string with `f` or `F` and use curly braces `{ }` to embed your variables or expressions.

In our first example below, we initially define and set our variables, and we then we use four different techniques to print them to the screen. 

As you walk through the example, note how they all produce the exact same outcome despite using very different approaches. Which approach you choose will be based on your needs, although f-strings will often win out. 

I highly recommend that your fork the [replit](https://replit.com/@rodmhgl/MidnightblueAptProcessor) for this post and experiment on your own! 
[https://replit.com/@rodmhgl/MidnightblueAptProcessor](https://replit.com/@rodmhgl/MidnightblueAptProcessor)

{% highlight Python %}
# Consolidated from https://realpython.com/python-f-strings/
# First, let's set some variables that we'll print to the screen later
first_name = "Eric"
last_name = "Idle"
age = 74
profession = "comedian"
affiliation = "Monty Python"

# Using string concatenation
# Here, we will use string concatenation 
# to inject the variables into the string
# This method works but it can become very clunky 
# to read and understand the formatting of the string
print("Hello, " + first_name + " " + last_name + ". You are " + str(age) + ". " + 
      "You are a " + profession +". You were a member of " + affiliation +".\n")

# Using percent formatting
# Here, we will use percent formatting to put placeholders into the string
# We then map those placeholders to variables. 
# These variables are mapped in order, 
# which can make future additions or deletions difficult
# It is also hard to comprehend the meaning of the sentence 
# without the context of the variable names
print("Hello, %s %s. You are %s. You are a %s. You were a member of %s.\n" % 
      (first_name, last_name, age, profession, affiliation))

# Using string.format()
# Here, we use placeholders to represent variables in the string
# And then map them within the .format() function call 
# These variables are mapped by name, which makes future 
# additions/deletions easier than with percent formatting
# It is also easier to comprehend the meaning of the sentence 
# than it is with percent formatting due to the context of 
# the variable names being available
print(("Hello, {first_name} {last_name}. You are {age}. " + 
       "You are a {profession}. You were a member of {affiliation}.\n") \
       .format(first_name=first_name, last_name=last_name, age=age, \
               profession=profession, affiliation=affiliation))

# Using f-string
# Here, we can place the variable names directly into the fString
# Very similar to string.format() but it removes 
# the need to add the mappings separately
# This is much more concise and readable than the previous methods
# It is considerably faster than string.format() as well. 
print(f"Hello, {first_name} {last_name}. You are {age}. " + 
       f"You are a {profession}. You were a member of {affiliation}.\n")
{% endhighlight %}


### Other Practical F-String Examples:

1. **Basic Usage with Variables**:
    {% highlight Python %}
    name = "Alice"
    age = 30
    greeting = f"My name is {name} and I am {age} years old."
    print(greeting)  # "My name is Alice and I am 30 years old."
    {% endhighlight %}

2. **Embedding Expressions**:
    Operations can be performed right inside the curly braces.
    {% highlight Python %}
    x = 10
    y = 5
    result = f"{x} multiplied by {y} is {x * y}."
    print(result)  # "10 multiplied by 5 is 50."
    {% endhighlight %}

3. **Using Methods and Attributes**:
    Here, we call the .upper() method inside of the f-string
    {% highlight Python %}
    word = "hello"
    output = f"Uppercase of {word} is {word.upper()}."
    print(output)  # "Uppercase of hello is HELLO."
    {% endhighlight %}

5. **Data Formatting**:
    Data can be formatted directly inside the curly braces.
    {% highlight Python %}
    pi = 3.14159265
    formatted = f"Value of pi rounded to 2 decimal places: {pi:.2f}"
    print(formatted)  # "Value of pi rounded to 2 decimal places: 3.14"
    {% endhighlight %}

F-strings are an elegant and efficient solution for string formatting and interpolation in Python. By using them, you can improve the readability and conciseness of your Python code.
