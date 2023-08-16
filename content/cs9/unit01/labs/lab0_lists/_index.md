---
title: 0. Lists
type: lab
# draft: True

---

# Lists
In this lab, we will review lists and introduce functional programming. 

## [1] What is a list, again?

We call lists a **data structure** because they give structure to data. They put things in an ordered grouping, so you can **access each element at an index**. 

Let's use the `Python shell` to do some quick list experiments.

{{< code-action "Open the Terminal and enter the Python shell by typing:" >}} `python3`
> You should see the following output...
>
> ```shell
> Python 3.9.7 (default, Oct 13 2021, 06:44:56) 
> [Clang 12.0.0 (clang-1200.0.32.29)] on darwin
> Type "help", "copyright", "credits" or "license" for more information.
> >>> 
> ```

{{< code-action "Create a new list with 5 of your favorite foods." >}}
> ```shell
> >>> food_list = ["dumplings","pizza","strawberries","ice cream","ramen","spinach"]
> ```


{{< code-action >}} **Use the** `Python Shell` **to experiment with how to accomplish each task below.** 
> {{< write-action "In your notebook, write down how you did it." >}} 

0. Print out the first item in the list
0. Print out the last item in the list
0. Print out the middle 3 items in the list
0. Add an item to the list
0. Print out the length of the list

<hr>

## [2] Functional Programming

In functional programming, we think of functions as transformations. They take any number of **parameters** and they change them into a **return value**.

```python
def double(number):
  return 2 * number
```
> **Here, `number` is the paramter and `2 * number` is the return value.** 
>
> As its name suggests, this function returns twice, `number`.

Here is a visualization of the function `double`. We are not so focused on how the function gets its 
work done as we are on what goes in and what comes out:

{{< figure src="images/courses/cs9/unit01/00_fig1.png">}}

This unlocks a powerful new way of breaking down
problems: we can think about how functions could be connected together. How do
you quadruple a number? Just double it, and then double the result: 

{{< figure src="images/courses/cs9/unit01/00_fig2.png" width=35% >}}

>
> ```python
> quadruple_number = double(double(5))
> ```
>
> `quadruple_number` will hold the integer value of `20`

We've already experienced this with `strings`, `integers`, `operators`, and `lists`. Let's test this using the `Python shell`.

{{< code-action >}} **Use the** `Python Shell` **to figure out what the return value is for each item below.** 
> Simply copy and past each line one at a time, and print out the variable to find the return value.

0. `number = str(10)`
0. `letters = int('50')`
0. `is_greater_than = 10>50`
0. `number_of_fruits = len(['apples','oranges','lemons','watermelons'])`
> ```shell
> >>> number = str(10)
> >>> print(number)
> ```

> {{< write-action "In your notebook, record the return value for each item." >}} 



---

## [3] Setup

{{< code-action >}} `cd` **into your** `cs9/unit_01` **folder.**
```shell
cd Desktop/cs9
cd unit_01
```

{{< code-action "Then, clone your starter code." >}} Be sure to change `YOUR-GITHUB-USERNAME` to your actual Github username.
```shell
git clone https://github.com/the-isf-academy/lab-lists-YOUR-GITHUB-USERNAME.git
```

---

## [4] Transforming Lists 

Now, we will utilize a functional programming approach to transform lists. 

You will write four functions: 
- `square_lists()`
- `capitalize_list()`
- `pluralize_list()`
- `reverse_list()`

Each function takes a list as a parameter, and returns and new list.

{{< figure src="images/courses/cs9/unit01/00_fig3.png" width=75% >}}




{{< code-action "Code the function" >}} `square_list()` 
- Parameter: a list of numbers
- Return value: a new list with each element squared

{{< code-action "Code the function" >}} `capitalize_list()` 
- Parameter: a list of strings 
- Return Value:a new list with each string fully capitalized

{{< code-action "Code the function" >}} `pluralize_list()` 
- Parameter: a list of strings
- Return Value: a new list word in its plural form

{{< code-action "Code the function" >}} `reverse_list()` 
- Parameter: Takes a list of items (can be any data type)
- Return Value: a new list with items in reverse order

<br>

Here are a few helpful functions to transform the elements in the lists. Also be sure to reference the [previous lab](http://localhost:1313/courses/cs9/unit01/labs/lab00_sample/), for a reminder on looping through lists.

| Function  | Data Type  | Explanation  |  Example |
|:-:|:-:|:-:|:-:|
| `append(element`)  | lists  | adds an element to the end of a list  |  `my_list.append("lemonade")` |
|`upper() ` | strings  | capitalizes every letter in a string | `my_string.upper()`  |

### [Testing]

{{< code-action "Write tests to ensure each of your functions works as intended." >}} Use `list_transformations_test.py` to test your functions sufficiently. 


{{< checkpoint >}}
Answer the following prompts in your notebook:

0. What is a list and why is it useful? 
0. What are the benefits of using a functional programming approach to list transformations?
0. How could you have utilized lists in your Unit 0 project?

{{< /checkpoint >}}

### [Deliverables]
{{< deliverables >}}
{{< code-action >}} **For this lab, you should `push` the following files to Github.**

- `lab-lists` repository containing the following: 
    - `list_transformations.py`
    - `list_transformations_test.py` 

Also be sure to hand in your notebook with checkpoint questions.
{{< /deliverables >}}

## [5] Extension: Sort

Python has a built in function `sort()` that will organize the elements of a list. Python takes care of the logic behind the sorting for you. All you have to do is tell Python which list to sort. 

{{< code-action >}} **Test the** `sort()` **function using the** `Python shell`.
> ```shell
> >>> number_list = [390,2,49,5.3,-100]
> >>> number_list.sort()
> ```
> `number_list` now holds: `[-100, 2, 5.3, 49, 390]`

{{< code-action >}}{{< write-action>}} **The extention activity is is for you to think through and apply the logic of the sorting algothirm.**

> 0. In your notebook, write pseudocode for the `sort()` function
> 0. Apply your pseudocode and write a custom `sort_list()` function in `list_transformations.py`

Some questions to consider:
- What are the steps involved in sorting a list of items? 
- What if the list contains numbers? What if the list contains strings? 
- What if the list contains numbers and strings? 

{{< code-action >}} **Remember to `push` your work to Github.**
