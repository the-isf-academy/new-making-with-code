---
title: 08. Functions III
draft: true
---
# Functions Lab | Part III

In this lab, we will deepen our understanding with a series of design challenges.

---

## [0] Set up

This lab will use the previous lab directory.

{{< code-action "In the Terminal, type the following command to open the lab folder." >}}
```shell
cd ~/desktop/making_with_code/cs9/unit00_drawing/lab_functions
```
{{< code-action "Run mwc update to get the latest code." >}}
```shell
mwc update
```

{{< code-action "Enter the Poetry Shell to start the lab." >}} As a reminder, we will run this command at the start of each lab, but only when we are inside a lab folder.
```shell
poetry shell
```

{{< aside "Exiting the poetry shell" >}}
When you want to exit the shell, you can type `exit` or `^D`
{{< /aside >}}

<!-- {{< code-action "Create a new file:" >}}
```shell
atom circle_patterns.py
```

{{< code-action "Copy and paste the starter code into the file:" >}}
```python
from turtle import *

def filled_circle(circle_size,circle_color):
    pencolor(circle_color)
    pensize(0)
    fillcolor(circle_color)
    begin_fill()
    circle(circle_size)
    end_fill()
``` -->
{{< code-action "Open circle_patterns in atom:" >}}
```shell
atom circle_patterns.py
```
{{< look-action "Take a look at the code inside" >}}

```python
from turtle import *

def filled_circle(circle_size,circle_color):
    pencolor(circle_color)
    pensize(0)
    fillcolor(circle_color)
    begin_fill()
    circle(circle_size)
    end_fill()
```


### [Helpful Turtle Functions]

Here are some helpful Turtle functions that may make this problem easier. You are not required to use all of these functions.

| Function     | Example Use     | Explanation                                                                                        |
|--------------|-----------------|----------------------------------------------------------------------------------------------------|
| setheading() | setheading(0)   | Sets the orientation of the turtle to an angle.  0 is east; 90 is north; 180 is west; 270 is south |
| goto()       | goto(0,0)       | Moves the turtle to an absolute x,y position                                                       |
| home()       | home()          | Moves the turtle to the start position (0,0)                                                       |
| penup()      | penup()         | Lifts the turtle pen up so it doesn't draw                                                         |
| pendown()    | pendown()       | Lifts the turtle pen down so it doesn't draw                                                       |
| speed()      | speed(1)        | Changes the speed of the turtle. 0 is the fastest. 1 is the slowest.                               |
| forward()    | forward(100)    | Draws a straight line in the current direction                                                     |
| backward()   | backward(100)   | Draws a straight line in the opposite direction                                                    |
| right()      | right(90)       | Turns the turtle a certain number of degrees right                                                 |
| left()       | left(90)        | Turns the turtle a certain number of degrees left                                                  |
| bgcolor()    | bgcolor('blue') | Changes the background of the turtle screen                                                        |
| colormode()  | colormode(255)  | Changes the turtle color to accept rgb colors.  e.g. color(255,15,23)                              |

---

## [1] Circle Patterns

This mini lab is designed to be a pick and choose adventure. The patterns below are in order of difficulty. It is up to you to choose patterns that are at an appropriate level of difficulty for you.

**Each of the pattenrs rely on the `filled_circle()` function provided in the starter code.**

---

### [Alternating Pattern]


{{< figure src="images/courses/cs9/unit00/lab_08_functions_00.png" width="50%">}}

{{< code-action >}} **Code a function `alternating_pattern(num_circles)`**
> *Example function call: `alternating_pattern(5)`*
   - It takes `num_circles` as a parameter - this will change the amount of circles in the pattern
   - Hard code the 2 colors to alternate between
   - *Hint: look at the conditionals lab*

For an additional challenge:
- add `num_circle_size` as a parameter - this will change the size of the circles in the pattern
   - *Example function call: `alternating_pattern(5,200)`*

---

### [Bullseye]

{{< figure src="images/courses/cs9/unit00/lab_08_functions_01.png" width="50%">}}


{{< code-action >}} **Code a function `bullseye_pattern(num_circles, starting_circle_size)`**
> *Example function call: `bullseye_pattern(5, 200)`*

   - It takes `num_circles` and `starting_circle_size` as parameters - the number of circles and the size of the bullseye should adjust accordingly
   - Hard code the 2 colors to alternate between

For an additional challenge:
- add `color1` and `color2` as parameters - this will change the colors of the pattern.
   - *Example function call: `bullseye_pattern(5, 200, 'coral', 'light blue')`*

---

### [Size Pattern]
{{< figure src="images/courses/cs9/unit00/lab_08_functions_02.png" width="50%">}}

{{< code-action >}} **Code a function `size_pattern(num_columns, num_rows, color)`**
> *Example function call: `size_pattern(6,5,'coral')`*

- It takes `num_columns`, `num_rows`, and `color` as parameters

---

### [Half-tone Pattern]

{{< figure src="images/courses/cs9/unit00/lab_08_functions_03.png" width="50%">}}

{{< code-action >}} **Code a function `halftone_pattern(num_columns, num_rows, color1, color2)`**
> *Example function call: `halftone_pattern(6,5,'dark blue','light blue')`*

- It takes `num_columns`, `num_rows`, `color1`, and `color2` as parameters

---

### [Random Pattern]

{{< figure src="images/courses/cs9/unit00/lab_08_functions_04.png" width="50%">}}

{{< code-action >}} **First, code a function `thick_circle(circle_size, circle_color, thickness)`**
- It should draw a circle of any color, size, and any pen thickness

{{< code-action >}} **Second, code a function `random_pattern(num_circles, background_color)`**
> *Example function call: `random_pattern(20,'black')`*

- It should create a random pattern of thick circles and filled circles
- The circles should all be of random colors and sizes.


**This will require you to:**
-  use the `randint()` function from the random library
   - add `from random import randint` to the top of your file
- change the color mode to accept rgb colors
   - add `colormode(255)` to the start of the function

---

## [4] Deliverables

{{< deliverables  >}}

**At then end of class, be sure to fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSf932ws3hURuj4q-X7E-zOkCSrgQLQVbNLI0P_XlFI5w56_Nw/viewform?usp=sf_link)**.


{{< /deliverables >}}
