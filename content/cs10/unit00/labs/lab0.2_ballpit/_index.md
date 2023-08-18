---
title: "0.2 Review: Ball Pit"
weight: 30

# draft: true
---

# Ball Pit

In this lab, we'll get re-aquainted with CS concepts such as classes and decomposition with the Turtle library. 

--- 

## [0] Set up


{{< code-action "Let's start by clonning the repository" >}} in your `cs10\unit00_networking` folder.  Be sure to change `yourgithubusername` to your actual Github username.

```shell
cd ~/desktop/making_with_code/cs10/unit00_networking
git clone https://github.com/the-isf-academy/lab_ballpit_yourgithubusername.git
cd lab_ballpit_yourgithubusername
```
> 🤔 *Remember, `tab` autocompletes files and folders in the Terminal*

📄 **This repository contains the following files:**
- `ball.py`
- `ballpit.py`
- `setup_ballpit_canvas.py`

---

## [1] Exploring Ball Pit

The Ballpit is a little animation made with Turtle. You can watch it by running the following command in your terminal:
 
```shell
python ballpit.py
```


{{< figure src="images/courses/cs10/unit00/lab0.2-00.png" width="50%" >}}

In the Ballpit, notice that each ball has a different behavior. One stays the same size the whole time and bounce off the walls. One doesn't bounce at all. Instead, it warps around to the opposite side of the screen. And the last ball grows and shrinks as it moves. It looks like it's breathing in and out.

### [OOP Review]

Before jumping into the details of the repository, let's review object oriented programming. Object oriented programming uses classes of objects to group related properties and functionalities.

Let's consider a `Character` object and a `Player` object. 

{{< figure src="images/courses/cs10/unit00/lab-ballpit-03.png" width="350px" >}}
*Note: the arrows signify the direction of the inheritance* 

In this model, we have a `Character` class that has...
- a `name` property
- a`introduce()` method
- a `jump()` method

The `Character` class a child class, `Player`. The `Player` class has... 
- a unique `mythical_race` property
- an inhereted `name` property
- an inhereted `jump()` method
- an overridden `introduce()` method

{{< checkpoint >}}
Before moving on, discuss the following with your partner and write down your thoughts in your notebook. 
- Why is the concept of **inheritance** useful?
- What does it mean to **override** a method?
{{< /checkpoint >}}
<br>

{{< expand "Extra Resouces: Learn more about Python Objects" >}}
- Creating a Class: [12.5 Constructors](http://programarcadegames.com/index.php?chapter=introduction_to_classes&lang=en#section_12_5)
- Inheritance: [12.6 Inheritance](http://programarcadegames.com/index.php?chapter=introduction_to_classes&lang=en#section_12_6)
{{< /expand >}}

### [Create a Model]

The BallPit contains three different types of balls. Each different type of ball is represented by a different class. The normal bouncing balls are represented with the `Ball` class. The `Ball` class is a parent class that has two child classes, `WarpBall` and `BreathingBall`. These two child classes inherit characteristics of the `Ball` class, and extend it to include additional features.  





Before you jump into tinkering with the code, create a model for each object. 

{{< write-action "With your knowledge of classes and inheritance, draw a model with your partner for how the BallPit works." >}}

For your reference, the BallPit has the following classes and functions. The `ball.py` file contains the architecture of each `Ball` object. The `ballpit.py` file initializes the Turtle and instances of the `Ball` objects. Make sure your model includes each of them.

- `ball.py`
    - `Ball`
    - `WarpBall`
    - `BreathingBall`
- `ballpit.py`
    - `ball_pit()`






## [2] Increase the chaos

At the moment, each `Ball` object is the same shade of green. Wouldn't it be nice if we could distinguish them? Your goal is to add more color into the pit!

{{< code-action "Add a unique color to the WarpBall and the BreathingBall." >}} Currently the `WarpBall` and `BreathingBall` simply call the parent `Ball` method for `set_color()`. Overide this method with the colors of your choosing. 

{{< checkpoint >}}
In this lab we've included **test files** where you can experiment with changes to the `WarpBall` and `BreathingBall` separate from the ballpit. Run the following files to check if you've successfully changed the color of each object.
- `test_add_color_to_breathingball.py`
- `test_add_color_to_warpball.py`

Check-in with a teacher by demonstrating your test files run as expected before moving on. 
{{< /checkpoint >}}

Let's try running `ballpit.py` again. You should see each `Ball` appear with a distinct color. 
```shell
python3 ballpit.py
```

<hr>

Now that we've got the colors sorted, let's add to the chaos and add more balls to the pit. At the moment, there is only one of each type of `Ball` object displayed in the Turtle window. 

{{< code-action "Increase the amount of balls in the ballpit so each type of Ball appears at least 10 times." >}}

**Hint! Consider the following...*
- *What data strucutre currently holds the instances of `Ball`, `WarpBall`, and `BreathingBall`?*
- *What is the most code efficent solution?*


{{< checkpoint >}}
Before moving on, make sure your everyone in your group understands the logic behind adding more `Ball` objects to the BallPit. 

Check-in with a teacher by demonstrating your improved `ballpit.py` file. 
{{< /checkpoint >}}

{{< figure src="images/courses/cs10/unit00/lab0.2-01.png" width="400px" >}}

### [Deliverables]

{{< deliverables "For this lab, you should push your lab-ballpit repository contianing updates to the following files:" >}}



- `ball.py`
- `ballpit.py`

Before moving onto the extension, make sure your everyone in your group understands the logic behind adding more `Ball` objects to the BallPit. 

Check-in with a teacher by demonstrating your improved `ballpit.py` file. 
{{< /deliverables >}}



<hr>

## [3] Extension: Randomizing the chaos

If time allows, ramp up the chaos even further by introducing the idea of cycling through colors. For example, every time a `Ball` object is created, it selected a different shade of green. 

{{< code-action "Add a random element to the color of the Ball, WarpBall, and BreathingBall." >}} 

**Hint! Consider how the color is currently chosen in the `set_color()` method.*


{{< code-action "Embrace the chaos of the ball pit! Cause the Ball, WarpBall, and BreathingBall to change color as they move." >}} 

Be sure to push any customization you've made to your ballpit!

{{< figure src="images/courses/cs10/unit00/lab0.2-02.gif" width="400px" >}}

