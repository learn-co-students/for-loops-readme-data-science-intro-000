
# For loops

### Learning Objectives

* Understand the components of a point in a graph, an $x$ value, and a $y$ value 
* Understand how to plot a point on a graph, from a point's $x$ and $y$ value
* Get a sense of how to use a graphing library, like Plotly, to answer questions about our data

### Picking up where we last left off

In the last lesson, we plotted some of our travel data.


```python
import pandas
file_name = './cities.xlsx'
travel_df = pandas.read_excel(file_name)
cities = travel_df.to_dict('records')
```


```python
import plotly

plotly.offline.init_notebook_mode(connected=True)

x_values = [cities[0]['City'], cities[1]['City'], cities[2]['City']]
y_values = [cities[0]['Population'], cities[1]['Population'], cities[2]['Population']]

trace_first_three_pops = {'x': x_values, 'y': y_values, 'type': 'bar'}
# plotly.offline.iplot([trace_first_three_pops])
```


<script>requirejs.config({paths: { 'plotly': ['https://cdn.plot.ly/plotly-latest.min']},});if(!window.Plotly) {{require(['plotly'],function(plotly) {window.Plotly=plotly;});}}</script>


Let's take another look at our `x_values` variable. 


```python
x_values = [cities[0]['City'], cities[1]['City'], cities[2]['City']]
```

As you can see, we go one by one through the `cities` list, and for each element of the cities list, we retrieve the `City` attribute.  This procedure of going one by one, and doing the same thing can be automated with the `for` loop.

### Learning Objectives

### Introduction to the For Loop

A `for` loop in Python, is good at going through elements of a list one by one.  Let's take an initial array.


```python
zero_to_three = [0, 1, 2, 3]
```

Now to print the elements of a list, we currently do the following: 


```python
print(zero_to_three[0])
print(zero_to_three[1])
print(zero_to_three[2])
```

    0
    1
    2


So we increase the index by one each time, starting at the number zero and ending at the number 2.  A `for` loop is great at going through these elements in the list.  For example:


```python
for i in [0, 1, 2]:
    print(i + 5)
```

    5
    6
    7


So note that above, our expression prints three times: once for each element in our list.  The first time it starts with the number 0, for that is the first element in the array, and then it goes forward to the second element, and then the third.  So we can use the `for` loop to operate on the numbers zero through two, and the `i` represents a successive element in our list each time.

Pay careful attention to the syntax.  Essentially, Python needs to know when the body of the loop begins and when it ends.  So we mark the beginning of the loop's body with a colon, `:`, and then indent each successive line of the loop.  (If you press enter after the colon, the indent will come automatically).  To end the body of the loop, we simply unindent. 


```python
for i in [0, 1, 2]:
    print(i + 5)
print(10)
```

    5
    6
    7
    10


Just like any other variable, we can call the `i` whatever we like.  


```python
for number in [0, 1, 2]:
    print(number + 5)
```

    5
    6
    7


We just have to make sure that whatever word we use after `for` is referenced in our loop later on.


```python
for number in [0, 1, 2]:
    print(what + 5)
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-23-ba9129ae8cfe> in <module>()
          1 for number in [0, 1, 2]:
    ----> 2     print(what + 5)
    

    NameError: name 'what' is not defined


### Using list elements as indices

In the above section we iterated through a list of successive numbers.  Now remember that to access elements of any lists, we use a number to do so.


```python
countries = ['Croatia', 'USA', 'Argentina']
```


```python
countries[0]
```




    'Croatia'




```python
countries[2]
```




    'Argentina'



So to iterate through the elements of `countries`, we can do the following:  


```python
for i in [0, 1, 2]:
    print(countries[i])
```

    Croatia
    USA
    Argentina


So notice what happened there.  Just like previously, our loop variable, `i`, is a different element of the list each time.  Because these elements are also the increasing indices for our list of `countries`, we can use them to access and then operate on the elements of the `countries`.


```python
for i in [0, 1, 2]:
    print(i)
    print(countries[i])
```

    0
    Croatia
    1
    USA
    2
    Argentina


Of course, this only works if the elements of the list match up with the size of our list.  So it would be nice to perform some calculation to ensure that this is the case.  Let's do it.

We can use the `len` function to calculate the size of our list.


```python
len(countries)
```




    3



Then we can turn this length into a successive list of elements with the following:

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

So far our loop variable has always been an element of a list that is a number.  However, our block variable can represent any data type.  For example, let's have the block variable represent each of the countries directly:


```python
countries = ['Croatia', 'USA', 'Argentina']
for i in countries:
    print(i)
```

    Croatia
    USA
    Argentina


So now `i` points to each element of the `countries` list.  We previously used `i` as `i` was equal to an index of a list.  However, here our block variable will equal an individual country.  Might as well be expressive:


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

In this section, we saw how we can use loops to iterate through various elements.  This is a very powerful 
