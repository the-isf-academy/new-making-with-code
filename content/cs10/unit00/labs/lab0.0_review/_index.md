---
title: "0.0 Review: Turtle"
---

# Review: Turtle Drawing

Welcome to CS10! We hope you're excited for what we have planned this year! 😄

Let's review by taking it back to CS9 Turtle drawings!

---

## [0] Set up

Now that you're in **cs10** you need a `cs10` folder! 

{{< code-action  >}} **In the Terminal, go into your `making_with_code` folder and create a `cs10` folder.**

```shell
cd ~/desktop/making_with_code
mkdir cs10
```

{{< code-action  >}} **Then, go into the `cs10` folder and create a `unit00_networking` folder.**

```shell
cd cs10
mkdir unit00_networking
```

{{< code-action "Then, clone your starter code." >}} Be sure to change `YOUR-GITHUB-USERNAME` to your actual Github username.
```shell
git clone https://github.com/the-isf-academy/lab_turtle_review_yourgithubusername
cd lab_turtle_review_yourgithubusername
```

{{< code-action >}} `cd` **into the lab**
```shell
cd lab_typing_game_yourGithubUsername
```


{{< aside "Windows Users" >}}

We suggest not copying the path command, and instead using `cd` and `ls` to ensure you are in the correct `making_with_code` folder.

{{< /aside >}}

{{< code-action "Enter the Poetry Shell." >}} Remember, we run this command at the start of each lab, but only when we are inside a lab folder.
```shell
poetry shell
```
{{< aside "Exiting the poetry shell" >}}
When you want to exit the shell, you can type `exit` or `^D`
{{< /aside >}}



---

## [1] Create a Turtle Drawing

{{< code-action >}} **Using the starter code in `turtle_drawing.py` create a drawing that includes at least 3 of CS concepts below:**
- Variables
- Loops
- Conditionals
- Lists
- Dictionaries
- Functions with parameters

{{< figure src="https://freshgadgets.nl/wp-content/uploads/2014/12/inspirograph2.jpg" width="75%">}}


### A Few Helpful Functions



| Function |       Input      |   Example Use  | Explanation                                                                                                                      |
|:--------:|:----------------:|:--------------:|----------------------------------------------------------------------------------------------------------------------------------|
|  forward |      amount      |  `forward(100)`  | Moves the turtle forward by the specified amount                                                                                 |
| backward |      amount      |  `backward(100)` | Moves the turtle backward by the specified amount                                                                                |
|   right  | angle in degrees |    `right(45)`   | Turns the turtle clockwise by the specified angle                                                                                |
|   left   | angle in degress |    `left(45)`    | Turns the turtle counter clockwise by the specified angle                                                                        |
|   color  |     colorname    |  `color('red') ` | Sets the color for drawing. Use "red", "black", etc.  [Here's a list of all the colors](https://trinket.io/docs/colors).                                           |
|   speed  | number from 0-10 |    `speed(0)`    | Determines the speed at which the turtle moves around the window. 1 for slowest, 3 for normal speed, 10 for fast, 0 for fastest. |
|  pendown |       None       |    `pendown()`   | Puts down the turtle/pen so that it draws when it moves                                                                          |
|   penup  |       None       |    ` penup()`    | Picks up the turtle/pen so that it doesn’t draw when it moves                                                                    |
| pensize  |       width      |   `pensize(4)`   | Sets the width of the pen for drawing                                                                                            |
| setheading  |       angle      |   `setheading(90)`   | Sets the pen to the 0th degree                                |
| circle  |       size      |   `circle(10) `  | Sets the radius of the circle                                                                                            |
| goto  |       x, y      |   `goto(90,0) `  | Moves turtle to a given coordinate                                                 |
| begin_fill  |       None     |  `begin_fill()`  | Marks the start of the color fill       |
| end_fill  |       None     |   `end_fill()`   | Marks the end of the color fill           |
| fillcolor  |       colorname     |   `fillcolor('purple') `  | Sets the color of the fill          |



## [2] Deliverables


{{< deliverables  >}}

🤔 **Remeber, at the end of each class we push to *Github***

{{< code-action "Push your work to Github:" >}}
- git status
- git add -A
- git status
- git commit -m "describe your drawing and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push

{{< /deliverables >}}
