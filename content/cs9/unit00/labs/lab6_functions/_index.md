---
title: 06. Functions I

draft: true
---
# Functions Lab | Part I

In this lab, we will learn how to create and call functions. Functions are blocks of code that are reusable throughout a program. You've already encountered functions such as `print()`, which is a function built into Python.


---

## [0] Set up

{{< code-action "Start by opening the Terminal cloning this lab onto your laptop." >}} As a reminder, we will run this command at the start of each lab.
```shell
mwc update
```
{{< code-action "In the Terminal, type the following command to open the lab folder." >}}
```shell
cd ~/desktop/making_with_code/cs9/unit00_drawing/lab_functions
```

{{< code-action "Enter the Poetry Shell to start the lab." >}} As a reminder, we will run this command at the start of each lab, but only when we are inside a lab folder.
```shell
poetry shell
```
{{< aside "Exiting the poetry shell" >}}
When you want to exit the shell, you can type `exit` or `^D`
{{< /aside >}}

{{< code-action "Take a look at the files inside with:" >}} `ls`
- `triangle.py`
- `hexagon.py`
- `icecream.py`
- `grid.py`

---


## [1] What is a function?
Before we can talk about functions, we need to talk about code blocks. A **code block** is one or more lines of code. Here's one:

```python
forward(side_length)
left(120)
```

Sometimes we want to talk about how many times a code block should run, or whether it should run at all.
Consider this code, which will draw a triangle:

```python
for each_item in range(3):
    forward(side_length)
    left(120)
```

We have the same code block, but now it's indented under the condition `for each_item in range(3):`. This means
the code block should run once for each item in the range. A few things to note:



Often times we want to reuse a code block in different sections of a program. `Functions` allow for code reuse without needing to copy and paste code blocks. **Here is a code block with a function definition and a function call:**

```python {linenos=table}
def draw_triangle(side_length):
    #This function draws a triangle
    for i in range(3):
        forward(side_length)
        left(120)

draw_triangle(200)
```

> A few things to note:
>
> - `line 1`
>   - `def` defines a new function called `draw_triangle()`
>   - it takes on parameter, or argument, called `side_length`
> - `line 4`
>   - `side_length` is used as a variable
>   - you can use function's parameters inside the function as variables
> - `line 7`
>   - `draw_triangle(200)` calls the function with a `side_length` of `200`
>   - Once you have written a function, you must call it to use it.

{{< expand "A few more tips on functions..." >}}
- Whenever a code block is indented, there's always a line introducing it. This line always ends with a colon.
- The way you indent matters. **Always use the tab key to indent.**
- When you're done with a code block, just stop indenting.

- After the function's name is the list of arguments, surrounded by parentheses `(side_length)`. Arguments, or parameters, are the things you need to tell the program before you can use the function. Think of arguments as questions the program might ask about what to do. For `draw_triangle`, the program wants to know "How long should the length of the sides be?" and you have to tell it the `side_length`. Some functions won't have any arguments, so their parameters list will look like `()`. It depends how you design your functions.
- The first line of the function's code block should be a comment explaining what the function does.
- In the function's code block, you can use the arguments as variables.

{{< /expand >}}



{{< aside >}}
**Functions make your code simpler.** Instead of writing all the code for a triangle over and over, you can get it right once and put it in a function.

**Once you have written a function, you must call it.** Calling a function tells Python to run that block of code. Remember, order matters. **Code is read from top to bottom.** You cannot call a function before it has been written.

{{< /aside >}}

---

### [Editing a Function]

{{< code-action "Let's start by running" >}} `triangle.py`
```shell
python triangle.py
```

{{< figure src="images/courses/cs9/unit00/00_functions_0.png" width="300px">}}


{{< code-action "Now, let's open the file:" >}}
```shell
atom triangle.py
```
Notice how it calls the `draw_triangle()` function with a `side_length` of `200`.

{{< code-action "Experiment with editing the parameter and then re-running the program." >}} For example, change `200` to a `500`.

---

### [Writing  a Function]

Now that you've had some practice editing a function, let's write a new one.

{{< code-action "Open the file:" >}} `hexagon.py`
```shell
atom hexagon.py
```

{{< code-action "Write a function that draws a hexagon with any side_length." >}} You will need to:

0. Write the function `draw_hexagon()`.
    - It should have one parameter called `side_length`
0. Call the function `draw_hexagon()` below the function definition.
    - It should be able to be called with any number for the `side_length`.

*Your finished drawing should look something like this:*
{{< figure src="images/courses/cs9/unit00/00_functions_1.png" width="300px">}}



---


## [2] Combining functions

**When you want to draw something fancy, you need to break it down into smaller steps.** Then you can write functions to do the smaller steps, and write more functions to combine small steps into bigger steps. This concept is called **decomposition**.

{{< figure src="https://www.thespruceeats.com/thmb/btLT5e97Xl3vBzNo37xPlUgfQcI=/3135x3900/filters:fill(auto,1)/GettyImages-90053856-588b7aff5f9b5874ee534b04.jpg" width="200px">}}


The code in this lab illustrates this. If we want to draw an ice cream cone with scoops of ice cream, we can break it down into steps:

- Draw ice cream: `draw_icecream()`
    - Draw an ice cream cone: `cone()`
    - Draw a scoop of ice cream: `scoop(num_scoops)`

---

### [Draw the Ice Cream]

{{< code-action "Start by running the file: " >}} `icecream.py`. Currently, it draws an incomplete ice cream.
```shell
python icecream.py
```

{{< figure src="images/courses/cs9/unit00/00_functions_3.png" width="200px">}}


{{< code-action "Open the file: " >}} `icecream.py`. As you can see, the function definitions are already provided. You just need to edit the following functions:
- `scoop(num_scoops)`
- `cone()`
- `draw_icecream(num_scoops)`



{{< code-action "Complete the ice cream drawing by editing the funcitons. " >}} The colors of the cone and ice cream scoops are up to you!

{{< figure src="images/courses/cs9/unit00/00_functions_icecream.png" width="200px">}}


{{<aside "FYI: How to Fill a Shape with Color and More!" >}}
To fill your turtle drawing with color follow the below format. You must call `begin_fill()` before the shape has been drawn and `end_fill()` after.

```python
def draw_triangle(sideLength):
    #This function draws a triangle
    for i in range(3):
        left(120)
        forward(sideLength)

fillcolor("Blue")
begin_fill()        #Tells the turtle to start the color fill
draw_triangle(20)
end_fill()          #Tells the turtle to stop the color fill
```
<br>

*For a wide range of color options look at this [chart](http://cng.seas.rochester.edu/CNG/docs/x11color.html).*

{{</aside>}}


---

## [4] Deliverables

{{< deliverables  >}}

**Once you've successfully completed the square pattern be sure to fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSdEzSmliyxzEcLmk7qHxfeCui9zp0ReDif4pJUzGoDob7sTyw/viewform?usp=sf_link)**.


{{< /deliverables >}}

---
## [5] Extension

### [Ice Cream Parlor]

Let's return to `ice_cream.py`.

Right now, both the color of the ice cream and the number of scoops are pre-determined or hard-coded. If you wanted to change the color or number of scoops, you would have to go back into the code and change it yourself.

{{< code-action "Expand the functionality of this program to simulate an ice cream parlor."  >}} The user should be able to choose the flavor of the ice-cream and the number of scoops.

{{<aside "Hints" >}}

Consider the following:
- How will you implement the functionality of a `flavor` that is not hard-coded?
- How will you include user input?
- How will you translate the flavor "chocolate" to the color "brown?

{{</aside>}}

Here is an example interaction:

```shell
python ice_cream.py

--- Welcome to the ISF ice cream parlor ---

What flavor would you like?
   > Select a flavor (chocolate, strawberry, vanilla): chocolate
How many scoops would you like?
   > Select number of scoops (max 3): 3

--- Enjoy your ice cream! Please come again! ---

[Press any key to exit]
```

{{< figure src="images/courses/cs9/unit00/lab_06_functions_03.png" width="25%">}}

