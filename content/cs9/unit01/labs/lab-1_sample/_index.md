---
title: -1. Micro Lab 
---

# Micro Lab: Lists

In this Micro Lab, we'll explore lists, a useful data structure.

## [0] Set up

{{< code-action "Start by making a new folder in your" >}} `cs9` **folder.**
```shell
cd Desktop/cs9
mkdir unit_01
cd unit_01
```

{{< code-action "Then, clone your starter code." >}} Be sure to change `YOUR-GITHUB-USERNAME` to your actual Github username.
```shell
git clone https://github.com/the-isf-academy/lab-micro-lists-YOUR-GITHUB-USERNAME.git
```

## [1] Lists

What is a list? We call a **list** a **data structure** because they give structure to data. They put things in an ordered grouping, so you can access each element at an index. 


{{< code-action "Begin by openning the file" >}} `lists_intro.py`. Change the value of the variables `my_name` and `friend_name` to anything you want. Something like:

```python
#VARIABLES
my_name = "Wall-E"
friend_name = "Eva"
```
 
The program currently prints out "help! I am trapped inside the computer!".

{{< code-action >}} **Replace that string with the following objects one at a time.** For each one, save your program and run it to see what the output.

0. `cs1_dessert_list`
0. `cs1_dessert_list[0]`
0. `cs1_dessert_list[3]`
0. `cs1_dessert_list[-1]`
0. `len(cs1_dessert_list)`
0. `cs1_dessert_list[100]`
0. `my_name + " likes to eat " + cs1_dessert_list[0] + " but " + friend_name + " likes to eat " + cs1_dessert_list[1]`


### [Looping through a list]

*Paste the code block below into the 'Part B' section of your list_intro.py file.*

```python
print("Ms. Brown and Ms. Genzlinger go to the store for dessert. They decide to buy...")
for thing in cs1_dessert_list:
    print(thing)
```

In the loop above, `thing` is a variable that we use to store each element within cs1_desserts as we loop through one by one. `thing` is not a very descriptive variable name - there are lots of things in the world. How will we know what thing the variable is storing?

{{< code-action >}} **Try changing `thing` to a more descriptive word in both lines**, like `sweet` or `dessert_item` and see if the output changes.


### [Looping Through Part of a List]
To give you more options, you can specify a range for your for-loop.

*Paste the code block below into the 'Part C' section of your list_intro.py file.*


```python
print("But then they realized they ran out of money, so they can only buy 4 desserts. They decide to buy...")
for i in range(1, 5):
    print(cs1_dessert_list[i])
```

**Oops! This code has an error!**

The first four desserts in the cs1_dessert_list list are ice cream, brownies, mochi, and timtams.
But our code prints out brownies, mochi, timtams, and creme brulee. 

{{< code-action >}} **Change the code to print out the first 4 desserts only.**

<hr>


## [2] Lists: To-do Program

Whenever we use lists everytime we make a written to-do list. So let's digitize it and create a terminal version!

**Let's start with the most basic version of a to-do list.** Here is the pseudocode:
```
create an empty list
infinite loop
    print the current list
    ask what the user would like to add to the list 
    add their item to the list
```

{{< code-action "It's up to you to translate the pseudocode into Python code and create a working to-do program.">}} Your code will go in `lists_todo.py`.

{{< aside "Adding to a list" >}}

Let's create a list of pizza toppings:
```python
pizza_toppings = ['cheese','pineapple']
```

To add something to this list:
```python
pizza_toppings.append('ham')
```

The list now looks like:
```python
pizza_toppings = ['cheese','pineapple','ham']
```
{{< /aside >}}

### [Advanced To-do]

Let's expand our app to allow us to remove items from the to-do list.

Here is the more pseudocode for the most advanced to-do list: 

```
create an empty list
infinite loop
    print the current list

    if the list has zero items in it
        ask what the user would like to add to the list 
        add their item to the list
    else
        ask the user if they would like to add to the list or remove from the list
        if the user wants to add to the list
            ask what the user would like to add to the list 
            add their item to the list
        if the user wants to remove from the list
            ask what the user would like to remove from the list
            remove the item from the list
```
{{< code-action "Expand the functionality of your to-do program." >}} 


{{< aside "Advanced lists" >}}

Consider our `pizza_toppings` list:
```python
pizza_toppings = ['cheese','pineapple','ham']
```

What if we wanted to remove `'pineapple'` from our list?
```python
pizza_toppings.remove('pineapple')
```

Now our `pizza_toppings` list looks like:
```python
pizza_toppings = ['cheese','ham']
```

What if we wanted to check how many pizza toppings we have? 
```python
number_of_toppings = len(pizza_toppings)
```

`number_of_toppings` will now hold the value `2`.
{{< /aside >}}


<!-- ## [2] Dictionaries

Now that you know about lists, which are a great way to store things that naturally come one after another, like subway stops on a subway line, or homework assignments in a class. 

The structure of a list works well for things that have a natural order (like zodiac cycles), but what about things that don't have a natural order to them?

A **dictionary** is another kind of data structure that is useful for information that does not have a natural order. **Dictionaries connect keys to values**. For each unique key (for example, an animal name like `'pig'`), a dictionary stores a unique value (like a translation `猪`). 

<br>


```python
animal_dict = {
"rat": "鼠",
"ox": "牛",
"tiger": "虎",
"rabbit": "兔",
"dragon": "龙",
"snake": "蛇",
"horse": "马",
"sheep": "羊",
"monkey": "猴",
"rooster": "鸡",
"dog": "狗",
"pig": "猪"
}
```


<br>


{{< code-action >}} Read the function `my_zodiac_year` in `dictionaries_introduction.py`
- Open a Python shell and import `my_zodiac_year` from `dictionaries_introduction.py`

- Run the `my_zodiac_year` function passing in your birth year as the argument

```shell
> python3 
>>> from dictionaries_introduction import my_zodiac_year
>>> my_zodiac_year(1995)
I was born in the year of the pig.
```

Let's add the Chinese translation the English Sentence "I was born in the year of the ________" to the `my_zodiac_year` function. 

{{< code-action >}} Below the `print` statement in the `my_zodiac_year` function of `dictionaries_introduction.py`, print the Chinese translation. Use the `animal_dict` dictionary to access the character for your `birth_year_animal`. 

**Values in a dictionary are accessed via the key.** For example:
```shell
> python3 
>>> from dictionaries_introduction import animal_dict
>>> animal_dict['dog']
'狗'
```

{{< code-action >}} Open a new python shell and import and run the `my_zodiac_year` function again with your new code. Now you should see something like:

```shell
>>> from dictionaries import my_zodiac_year
>>> my_zodiac_year(1995)
I was born in the year of the pig.
我出生在猪年
```


## B: Dictionaries in action

Dictionaries can be used to show one-to-one relationships like how capitals are connected countries, how students are connected to grade levels, or how books are connected to authors. 

Often we use dictionaries to describe properties of an object. A hero in an adventure game is defined in `PART B`:

```python
def create_character_traits():
    return {
        "courage": 8,
        "beauty": 4,
        "strength": 7,
        "empathy": 5
    }
```

{{< code-action >}} Open a python shell and import the `describe_character` and `create_character_traits` functions from the `dictionaries.py` file. Create a `character_traits` dictionary using the `create_character_traits` function and run the `describe_character` function:

```shell
>>> from dictionaries import describe_character, create_character_traits
>>> character_traits = create_character_traits()
>>> describe_character(character_traits)
You are foolhardy.
```

You can loop through a `dict` in almost the same way you can loop through a list:

```shell
>>> for trait, value in character_traits.items():
...     print("You have a {} value of {}.".format(trait, value))
You have a courage value of 8.
You have a beauty value of 4.
You have a strength value of 7.
You have a empathy value of 5.
```
 -->
