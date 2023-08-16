---
title: 03. Loops
draft: true
---

# Loops Lab
In this lab, we will learn how to make the computer do the same instruction over and over.

In Python, when you want to run the same code multiple times, we use loops.
If you have used Scratch before, you have seen loops before:

{{< figure src="images/courses/cs9/unit00/00_loops_scratch_loop.png" width="200px" alt-text="Scratch loop" >}}

How does a loop work in python? Let's see.

## [0] How to loop

Due to an issue with our website, you will clone this lab manually. 

{{< code-action >}} **Start by going into your `unit00_drawing` folder.**
```shell
cd ~/desktop/making_with_code/cs9/unit00_drawing/
```
{{< code-action "Then clone the lab" >}}
```shell
git clone https://github.com/the-isf-academy/lab-loops.git
```

{{< code-action "Now that you have the lab, go into its folder." >}}
```shell
cd lab-loops
```
<!-- 
{{< code-action "Start by opening the Terminal cloning this lab onto your laptop." >}} As a reminder, we will run this command at the start of each lab.
```shell
mwc update
```
{{< code-action "In the Terminal, type the following command to open the lab folder." >}}
```shell
cd ~/desktop/making_with_code/cs9/unit00_drawing/lab-loops
```  -->

{{< code-action "Enter the Poetry Shell to start the lab." >}} As a reminder, we will run this command at the start of each lab, but only when we are inside a lab folder.
```shell
poetry shell
```
{{< aside "Exiting the poetry shell" >}}
When you want to exit the shell, you can type `exit` or `^D`
{{< /aside >}}

{{< code-action "Take a look at the files inside with:" >}} `ls`
- `loops-repetition.py`
- `loops-square.py`
- `geometric-sequence.py`

---

### [Repetition]

{{< code-action "Let's start by openning" >}} `loops-repetition.py` **in Atom.**
```shell
atom loops-repetition.py
```

{{< code-action "Run your program and see what gets output:" >}}
```shell
python loops-repetition.py
```

This loop runs 10 times, repeating everything indented to the right of the `for i in range(10):` line.
`i` is a variable that gets incremented by one every time the loop runs.

{{< code-action "Edit the code to make the loop run a different number of times" >}} Maybe 5 or 14.
Can you figure out how to do it?


{{< code-action "Edit the loop again to print the square of numbers 0-12." >}} *Remember, the square of a number, is the number multiplied by itself.*

When you run `python loops-repitition.py` it should output:
```shell
0
1
4
9
16
25
36
49
64
81
100
121
144
```



<hr>

### [Looping a Square]


{{< code-action >}} **Use atom to open `loops-square.py`**

```shell
atom loops-square.py
```

Take a look at the code we've been using to draw a square:

```python
forward(100)
right(90)
forward(100)
right(90)
forward(100)
right(90)
forward(100)
right(90)
```

Pretty repetitive, right?

{{< code-action "Edit the code so that it uses a loop to draw a square, instead of repeating the same code over and over again." >}}

---

## [1] Geometric sequences

Loops are particularly useful when we need to do things over time. To see this, we're going to explore geometric sequences.

**Geometric sequences are sequences where there is a common ratio between each
number in the sequence.** A geometric sequence always begins with `1`. Each subsequent number in the sequence is calculated by finding the product of the number that precede it and the ratio.


{{< figure src="https://www.storyofmathematics.com/wp-content/uploads/2021/01/geometeric-sequence-example.png" width="50%" alt-text="geometric sequence" >}}

> For example, `1, 2, 4, 16,...` is a geometric sequence
where each number is 2 times the number before it.
>
> The ratio between the sequence is 2

**In `geometric-sequence.py`, you will write a program that displays 10 digits of any geometric sequence.**

---


### [Pseudocode]

**Pseudocode is an outline of the program we plan to write. When writing pseudocode, we don't worry about using Python syntax.** You can write in regular words to figure out the logic of the problem, then translate it into the correct syntax. 

{{< code-action >}} **To get started, open up `geometric-sequence.py`.**
```shell
atom geometric-sequence.py
```

{{< write-action >}} **Use `comments` to complete the pseudocode to list the first 10 numbers of any geometric sequence.** There are currently two line of pseudocode in the file.
> You've already seen examples of comments.
> Any line that begins with a `#` is a comment

Here are some things to consider:
- You will use a loop to calculate each term in the sequence. What is the formula
you will use at each step in the loop to calculate the term?
- You will need to know the previous term to calculate the current term. How will
you keep track of this?

{{< aside "FYI: Comments" >}}
If you don't want code to be executed when you run a program, you can comment it out by placing `#` at the beginning of the line.

This can be used as a debugging strategy or as a note-taking tool.
{{< /aside >}}

---

### [Code]

{{< code-action "After you are confident your pseudocode has the correct logic, translate it into python code." >}} We suggest translating one line of pseudocode at a time.

Here is an example of what the program will output when run:
```shell
$ python geometric_sequences.py
What should the ratio of the sequence be? 4
4
16
64
256
1024
4096
16384
65536
262144
1048576
```

---

### [Visualize the Geometric Sequence]

Geometric Sequences are great for creating interesting visualizations.

{{< figure src="images/courses/cs9/unit00/00_loops0.png" width=40% alt-text="geometric drawing" >}}

{{< code-action "Using the Turtle library, create a visualization of the Geometric Sequence." >}}
> You will need to include the following line at the start of your file to use the Turtle library:
>
> `from turtle import *`


## [2] Deliverables

{{< deliverables  >}}

**Once you've successfully completed the geometric sequence visualization be sure to fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSfM0nLnUFoMDa67aBk9xV9MSUw78jKlQwkGIdZi-TsrYEDNkA/viewform?usp=sf_link)**.


{{< /deliverables >}}

<hr>

## [3] Extension: Fibonacci Sequence

For the extension, explore a more complicated sequence, the Fibonacci sequence. This sequence has all kinds
of interesting properties.

The Fibonacci sequence begins with two numbers, `0` and `1`. Each subsequent number in the sequence is calculated by finding the sum of the two numbers that precede it.
> For example the first 5 digits of the sequence are:
> 0, 1, 1, 2, 3

**It is up to you to write the algorithm for determining any number of digits in the Fibonacci sequence.**

---

### [Pseudocode]

{{< code-action "Open a new file:" >}}
```shell
atom fibonacci_sequence.py
```

{{< write-action >}} **In `fibonacci_sequence.py`, use `comments` to write the pseudocode to list the first 10 digits of the Fibonacci sequence.**

---

### [Code]
{{< code-action "After you are confident your pseduocode has the correct logic, translate it into Python code." >}}

Here is an example of what the program will output when run:
```shell
$ python fibonacci_sequence.py
0
1
1
2
3
5
8
13
21
34
```

---

### [Visualize the Fibonacci Sequence]

Use your working code draw a pattern that utilizes the Fibonacci sequence.

{{< figure src="images/courses/cs9/unit00/00_variables_pinecone.png" width=75% alt-text="Fibonacci drawing" >}}

{{< code-action "First, use your Fibonacci code to draw a single spiral." >}}  You can do this by drawing a
line for each number in the Fibonacci sequence and connecting the lines at a consistent angle.

{{< figure src="images/courses/cs9/unit00/00_variables_spiral.png" title="Fibonacci spiral" >}}

### [Multiple spirals]
{{< code-action "Loop the drawing code to draw multiple spirals originating from the center." >}}

Now, the Turtle should draw something like this:

{{< figure src="images/courses/cs9/unit00/00_variables_vortex.png" title="Many spirals" >}}

{{< aside "FYI: Moving the Turtle" >}}
You can return your turtle to the center of the window using `goto(0, 0)`. You can also use `penup()` and `pendown()` to keep the turtle from drawing as it returns to the
center.
{{< /aside >}}

### [Clockwise and counterclockwise]
To get a pinecone or flower effect, you can try spiralling clockwise
and counterclockwise.

{{< code-action "Repeat your spiral code, changing it to make your spirals turn in the other direction." >}}

Feel free to add colors and personalize the visualization however you would like!
