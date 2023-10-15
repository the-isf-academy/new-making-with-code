---
title: 08. Functions III
draft: true
---
# Functions Lab | Part II

In this lab, we will continue to practice creating and calling functions. 

---

## [0] Set up

This lab will use the previous lab directory. 

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

{{< code-action "We will only be working with:" >}} `grid.py`

---

## [1] Draw Grid

Let's practice writing some more functions. Our aim is to create a grid of squares.

{{< figure src="images/courses/cs9/unit00/lab_06_functions_02.png" width="50%">}}

This is a complex problem, and thus we should use the practice of **decompsition** to break it down into smaller steps.

- **Step 1:** Drawing one square
- **Step 2:** Drawing one line of squares
- **Step 3:** Drawing a grid of squares

{{< aside "Many Solutions..." >}}

There are many solutions to this problem. If you feel confident to solve this problem in different way and without hints, please feel free to do so.

*We will accept any solution that draws a grid of squares of any square size and any gap size when you run `python grid.py`.*

{{< /aside >}}

---

### Helpful Turtle Functions

Here are some helpful Turtle functions that may make this problem easier. You are not required to use all of these functions. 

| Function     | Example Use   | Explanation                                                                                        |
|--------------|---------------|----------------------------------------------------------------------------------------------------|
| setheading() | setheading(0) | Sets the orientation of the turtle to an angle.  0 is east; 90 is north; 180 is west; 270 is south |
| goto()       | goto(0,0)     | Moves the turtle to an absolute x,y position                                                       |
| home()       | home()        | Moves the turtle to the start position (0,0)                                                       |
| penup()      | penup()       | Lifts the turtle pen up so it doesn't draw                                                         |
| pendown()    | pendown()     | Lifts the turtle pen down so it doesn't draw                                                       |
| speed()      | speed(1)      | Changes the speed of the turtle. 0 is the fastest. 1 is the slowest.                               |

---

### [Step 1]

{{< code-action "Open the file:" >}}
```shell
atom grid.py
```

{{< code-action "Fill in the" >}} `square(square_size)` function. It should draw one square of any size.

{{< figure src="images/courses/cs9/unit00/lab_06_functions_00.png" width="25%">}}

{{< code-action >}} **Test your `square()` function.** Make sure it can draw a square of any size.  


---

### [Step 2]

{{< code-action "Implement the STEP 2 functionality in the" >}} `line_of_squares(square_size, gap_size)` function. Draw one line of squares the length of `square_size` with gap the size of `gap_size`.
> You should use your `square()` function to create a line of squares.

{{< figure src="images/courses/cs9/unit00/lab_06_functions_01.png" width="50%">}}

{{< code-action >}} **Test your `line_of_squares()` function.** Make sure it can draw a line of squares of any `square_size` and `gap_size`.


---

### [Step 3]

{{< code-action "Implement the STEP 3 functionality in the" >}} `grid(square_size, gap_size)` function.
> You should use your `line_of_squares` to create a grid of squares.

{{< figure src="images/courses/cs9/unit00/lab_06_functions_02.png" width="50%">}}

{{< code-action >}} **Test your `grid()` function.** Make it sure it can draw a 4x4 grid of squares.


---

## [4] Deliverables

{{< deliverables  >}}

**If you did not fill out the Google form in "Function I", be sure to fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSdEzSmliyxzEcLmk7qHxfeCui9zp0ReDif4pJUzGoDob7sTyw/viewform?usp=sf_link)**.


{{< /deliverables >}}

---
## [5] Extension



### [Custom Grid]



{{< code-action "Expand the functionality of the program so the user can customize the following:"  >}}
- number of rows
- number of columns
- color palette


Here is an example interaction:

```shell
python grid.py

--- PATERN GENERATOR ---

How many rows?
   > Enter a number: 5
How many columns?
   > Enter a number: 3
Pick a primary color.
   > Choose a color (darkseagreen, coral, deeppink): darkseagreen
Pick a secondary color.
   > Choose a color (darkred, coral, cyan, cadetblue): coral

[Press any key to exit]
```

{{< figure src="images/courses/cs9/unit00/lab_06_functions_04.png" width="50%">}}

---

### [Polygon Grid]

{{< code-action "Expand the functionality of the grid program so the user can customize the type of polygon that is drawn."  >}}


{{< figure src="images/courses/cs9/unit00/lab_07_functions_00.png" width="50%">}}


{{< figure src="images/courses/cs9/unit00/lab_07_functions_01.png" width="50%">}}
