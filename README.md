
# For loops

## Introduction
Programming is all about making things my dynamic and more efficient, right? Well a big part of making our code more efficient and dynamic are loops! They allow us to iterate over each element in a collection, like a list. Perhaps we could already do that by writing out a line of code for each element in the collection, but that wouldn't be very efficient, would it? No, not at all. With loops, we can write one line of code that operates on each element in a collection. Pretty cool, right? Let's get started!

### Learning Objectives

* Understand how to write a for loop
* See different ways for loops can be used

## What is a for loop and how do I write one?

A `for` loop in Python, is primarily used for going through elements of a list one by one. We'll use a simple collection with 4 elements `0,1,2,3` as an example. Without a loop, if we wanted to print each element of the list we'd have to write it out like we do below:


```python
zero_to_three = [0, 1, 2, 3]
```


```python
print(zero_to_three[0])
print(zero_to_three[1])
print(zero_to_three[2])
print(zero_to_three[3])
```

> Press shift + enter

In the example above, we are sequentially accessing each index in the list and printing its value (the element). That works well enough, but if our list were 100 element long it would become extrememly tedious. And what if the length of our list were ***unknown***. Spooky, right? 

In fact, it may very often be the case that we don't know the length of the collection we are working with. So, writing all this static code for each element becomes not only unmanageable, but impossible.

Let's see how we would do the same operation above with a for loop!


```python
for number in zero_to_three:
    print(number)
```

Great! We were able to reproduce the exact same functionality as we had previously. However, in this example, we used only **2** lines of code. 

Now, the for loop may look a bit confusing at first, so, let's take a closer look at the syntax. A for loop essentially has two necessary components, which we'll refer to as arguments. The first argument is the variable name we are assigning to an element, or in this case, `number`. The second argument is the collection we are iterating over, or in this case, the list `zero_to_three`.

We can give any name to the variable. The important thing to understand here is **it is the reference** to each **element** in the collection. So, when we print `number`, we are printing an element of the collection `zero_to_three`. 

Every for loop needs to end the first line with a colon `:`. This indicates the start of the **block** of code. The block is simply the code that we want executed in each iteration of our loop. So, if all we want to do is print each element, then the line that prints the element is our block. Our block is indicated by indenting. So the first line after the colon `:` should be indented. When we want to end our block, we simply stop indenting. Any code follwing the for loop will only be executed after the for loop finishes.

> *Remember, the block of code in a for loop is executed the same amount of times as there are elements in the collection.*

Let's take a look at changing the variable names and adding more code to our example:


```python
iteration_count = 0
for whatever_we_want in zero_to_three:
    iteration_count += 1
    print("This is iteration:", iteration_count)
    print(whatever_we_want)
print("The for loop is finished now! I am not in the for loop block, which is why I only printed once!")
```

## Using list elements as indices

In the examples above, we used the elements in our list to perform an operation, which was printing them. We can also use a list of numbers to access elements from another list. Let's take a look at an example.


```python
countries = ['Croatia', 'USA', 'Argentina', 'France', 'Brazil', 'Japan', 'Vietnam', 'Israel']
```


```python
for index in [0,1,2,3,4,5,6,7]:
    print(index)
    print(countries[index])
```

So, in the example above, we are still using the elements in the list of numbers from 0 to 7 in our for loop, but we are instead using them to access each element of another list. This example is a bit contrived, but perhaps you have two lists that are ordered correctly and have information like the capital cities in one list and the the corresponding countries in another. How would we print both of those out in the same line?


```python
countries = ['Croatia', 'USA', 'Argentina', 'France', 'Brazil', 'Japan', 'Vietnam', 'Israel']
cities = ['Zagreb', 'Distric of Columbia', 'Buenos Aires', 'Paris', 'Rio de Janeiro', 'Tokyo', 'Hanoi', 'Tel Aviv']
```


```python
for index in [0,1,2,3,4,5,6,7]:
    print(cities[index]+",", countries[index])
```

Of course, this does not work if we have more number of iterations does not match up with the size of our list.


```python
for index in [0,1,2,3,4,5,6,7,8,9,10]:
    print(cities[index]+",", countries[index])
```

So, the preferred way of figuring out the amount of iterations on a list when you are unsure of its length would be to use the `len` function to calculate the size of the list.


```python
len(countries)
```

Then we can turn this length into a successive list of elements with the following.  

First, create a range object:


```python
range(0, len(countries))
```

And then convert this into a list:


```python
list(range(0, len(countries)))
```

Note that the range object is marking the starting and ending point, and excluding the end.  So this works perfectly:


```python
for index in list(range(0, len(countries))):
    print(cities[index]+",", countries[index])
```

And as we add or subtract countries, we will still be iterating through our list elements.


```python
countries.append('Mexico')
cities.append('Mexico City')
for index in list(range(0, len(countries))):
    print(cities[index]+",", countries[index])
```

## Iterating through different datatypes

So far our loop variable has always been an element of a list that is a number.  However, our loop variable can represent any data type.  For example, let's have the loop variable represent each of the countries directly:


```python
different_elements = ['A String', ["a", 'list', "of", 5, ["elements"]], {'this': "is a dictionary"}]
for element in different_elements:
    print(element)
```

Now that we know we can iterate through a list that contains multiple data types, let's explore iterating through a data type that's **not a list**. 

Another collection we commonly will iterate over is a **dictionary**. Dictionaries differ from list, on a high level, in that elements are **key, value pairs** instead of one single element. So, when we go through each item in a dictionary, we are actually working with a two-part element (with a key & value). Similarly to how we name a variable for the element in a list for a for loop, we name a variable for both the **key** and **value** when we iterate over a dictionary. However, in Python, we can't iterate directly over the dictionary, we iterate over the **items** of a dictionary, which are the key value pairs.  Let's take a look at an example.


```python
example_dictionary = {'first_name': "Terrance", 'last_name': "KOAR", 'favorite_language': "Python"}
print(example_dictionary.items())
type(example_dictionary.items())
```

Here we can see this **dict_items** object looks almost like a list, but each item has **two** parts, the **key** and **value**. So, in our first iteration, the first **key** will be **first_name**, and the first **value** will be **Terrance**.


```python
for key, value in example_dictionary.items():
    print("this is the key:", key)    
    print("this is the value:", value, "\n")
```

So, we can see that the **dict_items** object groups the key values together in a way that we can iterate over them and access them. We can even use them to inform our program to operate on keys and values in a certain way. Such as, the last name is inexplicably in all caps. Let's look at how we can rectify that and title case the last name when we print out the full name of the `example_dictionary` object.


```python
first_name = ""
last_name = ""
for key, value in example_dictionary.items():
    if key == "last_name":
        last_name = value.title()
    if key == "first_name":
        first_name = value
print(first_name, last_name)
```

## Conventional Naming Patterns

Typically, when we are looping through a collection of things like `countries`, we will name the looping variable, `country`, since that is the singular version of the plural name that represents our list. This is convention and helps to not only remind us, but tell other people looking at our code what that variable is. Let's take a look at a couple examples.


```python
for country in countries:
    print(country)
```


```python
ice_cream_flavors = ['Mint Chocolate Chip', 'Coffee', 'Cookie Dough', 'Fudge Mint Brownie', 'Vanilla Bean']
for ice_cream_flavor in ice_cream_flavors:
    print('I love ' + ice_cream_flavor + ' ice cream!!')
```

### Summary

In this lesson, we learned how to use loops to iterate through a collection of elements. We started with iterating through a list of numbers, and performed the same operation on each number. Then we saw how we can loop through the numbers and have each number be used to access a successive element from a separate list, like `countries`.  We then saw that to ensure that our list of numbers matched the indices of a our other list, we had to use the expression, `for element in list(range(0, len(list)))`. Finally, we introduced a naming convention that is commonly used when naming the variable for our loops when iterating over a collection that is a list of common elements (i.e. `ice_cream_flavor` for a list of `ice_cream_flavors`).
