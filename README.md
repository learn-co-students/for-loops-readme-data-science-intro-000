
# For loops

### Learning Objectives

* Understand how `for` loops can allow us to perform the same operations on different data 

### Introduction to the For Loop

A `for` loop in Python, is good at going through elements of a list one by one.  Let's take an initial array.


```python
zero_to_three = [0, 1, 2, 3]
```

Now to print the elements of a list, we could do the following: 


```python
print(zero_to_three[0])
print(zero_to_three[1])
print(zero_to_three[2])
```

> Press shift + enter

So in the code above, we increased the index by one each time, going from the 0 to 1 to 2.  A `for` loop is great at going through sequential elements in a list, like 0 through 2.  For example:


```python
for i in [0, 1, 2]:
    print(i + 5)
```

> Again, press shift + enter

So above, our expression prints three times -- once for each element in our list.  The first time it starts with the number 0, as that is the first element in the array.  Then it goes forward to the second element, and then the third.  So we can use the `for` loop to operate on the numbers zero through two, and the `i` represents a successive element in our list each time.

Pay careful attention to the syntax.  What is that colon at the end of the first line?  Essentially, Python needs to know when the body of the loop begins and when it ends.  So we mark the beginning of the loop's body with a colon, `:`, and then indent each successive line of the loop.  (If you press enter after the colon, the next line will automatically indent).  To end the body of the loop, we simply unindent. 


```python
for i in [0, 1, 2]:
    print(i + 5)
print(10)
```

Just like any other variable, we can call the `i` whatever we like.  Below, we call it `number`.


```python
for number in [0, 1, 2]:
    print(number + 5)
```

Whichever word we place after the `for` keyword will be the name of our loop variable to reference later on.  If we are inconsistent, we receive an error.


```python
for number in [0, 1, 2]:
    print(what + 5)
```

> Press shift + enter

### Using list elements as indices

In the above section we iterated through a list of successive numbers.  But we can also use our `for` loop to access successive elements of a separate list, like so.


```python
countries = ['Croatia', 'USA', 'Argentina']
for i in [0, 1, 2]:
    print(countries[i])
```

So notice what happened there.  Just like previously, our loop variable, `i`, is an increasing number for each iteration.  Because these successive numbers are also successive indices of our `countries` list, we can use them to access and then operate on the elements of the `countries`.


```python
for i in [0, 1, 2]:
    print(i)
    print(countries[i])
```

Of course, this does not work if we have more number of iterations does not match up with the size of our list.


```python
for i in [0, 1, 2, 3]:
    print(i)
    print(countries[i])
```

So it would be nice to perform some calculation to ensure that this is the case.  Let's do it.  We can use the `len` function to calculate the size of our list.


```python
len(countries)
```




    3



Then we can turn this length into a successive list of elements with the following.  

First, create a range object:


```python
range(0, len(countries))
```




    range(0, 3)



And then convert this into a list:


```python
list(range(0, len(countries)))
```




    [0, 1, 2]



Note that the range object is marking the starting and ending point, and excluding the end.  So this works perfectly:


```python
for i in list(range(0, len(countries))):
    print(countries[i])
```

    Croatia
    USA
    Argentina


And as we add or subtract countries, we will still be iterating through our list elements.


```python
countries = ['Croatia', 'USA', 'Argentina']
countries.append('Mexico')
for i in list(range(0, len(countries))):
    print(countries[i])
```

    Croatia
    USA
    Argentina
    Mexico


### Iterating through different datatypes

So far our loop variable has always been an element of a list that is a number.  However, our loop variable can represent any data type.  For example, let's have the loop variable represent each of the countries directly:


```python
countries = ['Croatia', 'USA', 'Argentina']
for i in countries:
    print(i)
```

    Croatia
    USA
    Argentina


So now `i` points to each element of the `countries` list.  We previously used `i` as `i` was equal to an index of a list.  However, here our loop variable will equal an individual country.  Might as well be expressive:


```python
for country in countries:
    print(country)
```

    Croatia
    USA
    Argentina


This is a standard pattern.  The variable name pointing to a list is plural, and to refer to a singular element as a loop variable, use the singular version.  So if we were printing out a list of friends name, we would write it as the following:


```python
friends = ['Bob', 'Sally', 'Fred']
for friend in friends:
    print(friend)
```

    Bob
    Sally
    Fred


And there we are printing out a list of friends.

### Summary

In this section, we saw how we can use loops to iterate through various elements.  We started with iterating through a list of numbers, and performed the same operation on each number.  Then we saw how we can loop through the numbers and have each number be used to access a successive element from a separate list, like `countries`.  We showed that to ensure that our list of numbers matched the indices of a separate list, we could use the expression, `for element in list(range(0, len(list)))`.  Finally, we saw that we can also just iterate through the list of elements directly as in the expression, `for friend in friends:`.
