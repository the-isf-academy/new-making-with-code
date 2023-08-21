---
title: 02. Variables

# draft: true

---

# Variables Lab
In this lab, we will learn about variables, a powerful storage container of information.

## [0] Variable tests
<!-- 
{{< code-action "Start by opening the Terminal cloning this lab onto your laptop." >}} As a reminder, we will run this command at the start of each lab.
```shell
mwc update
``` -->

{{< code-action >}} **Then, use `cd` to change directories to your `Desktop`.** A directory is just a fancy word for a folder.

```shell
cd ~/Desktop/making_with_code/unit00_drawing
```

{{< code-action "Clone the lab" >}}
```shell
git clone https://github.com/the-isf-academy/lab_variables
```
<!-- 
{{< aside "Windows Users" >}}

I suggest not copying the path command, and instead using `cd` and `ls` to ensure you are in the correct `making_with_code` folder.

{{< /aside >}} -->

{{< code-action "Enter the Poetry Shell." >}} We will also run this command at the start of each lab, but only when we are inside a lab folder.
```shell
poetry shell
```
{{< aside "Exiting the poetry shell" >}}
When you want to exit the shell, you can type `exit` or `^D`
{{< /aside >}}

{{< code-action "Take a look at the files inside with:" >}} `ls`
- `variable_test0.py`
- `variable_test1.py`
- `variable_test2.py`
- `responsive_drawing.py`

---

### [Variable test 0]

{{< code-action "First let's start by running" >}} `variable_test0.py`.
```shell
python variable_test0.py
```

You should see words print out in the Terminal.


{{< code-action "Let's see how that is happening by opening the file in Atom:" >}} `atom variable_test0.py`
> Atom is the code editor we will be using throughout this course.

```python
#####################
# Unit 0 Lab 2
# variable_test0.py
#####################

name = "YOUR NAME"
print("Hello")
print(name)
```

{{< code-action >}} **Start by replacing `"YOUR NAME"` with your name (but keep the `""`).** Now you have *declared* the `name` variable and *assigned* your name as its value.

{{< code-action "Save the file and run the program again." >}} You should see an output similar to the one below:
> *Tip: Use the up arrow to cycle through your previous commands in Terminal*

```shell
$ python variable_test0.py
Hello
Emma
```

What just happened? After storing your name in the `name` variable, `print(name)` prints out whatever is stored in the variable.

Let's do another test.

{{< code-action "Add the following lines of code to your file." >}}

```python
name = "YOUR FRIEND'S NAME"
print("HELLO")
print(name)
```

{{< code-action >}} **Replace** `"Friend's name"` **with your friend's name.**

Now our program is printing the `name` variable twice but we've assigned different values to the
variable at different places in the code. What do you think will happen?

{{< code-action "Run the code to find out!" >}} You should see an output similar to the one below:
```shell
$ python variable_test0.py
Hello
Emma
Hello
Britte

```
---

### [Variable test 1]

{{< code-action "Let's continue explore variables by running a different variable test:" >}} `python variable_test1.py`

Hmm, something is wrong here.

{{< code-action "Open up the code and try to fix the bug:" >}} `atom variable_test1.py`

```python
#####################
# Unit 0 Lab 2
# variable_test1.py
#####################

favorite_color = "color"
print("Your favorite color is " + favorite_color)
print("Your favorite fruit is " + favorite_fruit)
favorite_fruit = "fruit"
```


---

### [Variable test 2]
{{< code-action "Now, let's experiment with user input. Run the 3rd variable test:"  >}} `python variable_test2.py`

```python
#####################
# Unit 0 Lab 2
# variable_test2.py
#####################


favorite_artist = input("What is your favorite artist? ")
print("Oh, I love " + favorite_artist + "!")
```

{{< code-action "Run your program multiple times and change up what artist you type." >}}

This shows how your programs can be responsive to user input and how you can store
information from the user in variables that may change every time your program runs.


---


## [1] Responsive Drawing


The last variable test showed how your programs can be responsive to user input and how you can store information from the user in variables that may change every time your program runs.

**This means that we can use variables to make our code do different things at different times based on input.** Can you imagine how that might help use make more interesting turtle drawing?

{{< figure src="images/courses/cs9/unit00/blue_hexagon2.png" width="30%" alt-text="blue hexagon" >}}


{{< code-action "Create a turtle drawing that is responsive to user input." >}} Open the file `responsive_drawing.py` to get started.
- a numerical user input
- a word based user input
- 1 Turtle function not included on the `0. Turtle` lab page
    - You may want to look at the official documentation at [https://docs.python.org/3/library/turtle.html](https://docs.python.org/3/library/turtle.html)


{{< aside "FYI" >}}
You can get input from the user while your program is running using `input("PROMPT")`. By default, `input("PROMPT")` collects words.

If you want to get a number from the user, use `int(input("PROMPT"))`. This is because
Python treats numbers and words differently. We'll talk more about this next unit.

*For example:*
```python
age = int(input("How old are you?"))
```

{{< /aside >}}

---

### [Deliverables]


{{< deliverables  >}}

**Once you've successfully completed the responsive drawing be sure to fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSdj2v10XtImu8somw--aWTTspN6CxBJpYRTAfGIrSfC0o4EpA/viewform?usp=sf_link)**.


{{< /deliverables >}}

---

## [2] Extension: Size Factor Drawing

**Create a turtle drawing of a face that changes sizes based on a user inputed size factor.**

For example, if the user inputs `1` the face should be an average size. If the user inputs `.5`, the face should be half size. If the user inputs `2`, the face should be twice the size.


{{< code-action "Create a new file:" >}} `atom size_factor.py`.
> *Make note of how we create a new file.* `atom <file_name.py>`
