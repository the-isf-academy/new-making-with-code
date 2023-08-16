---
title: 12. Ball Animation
draft: true
---

# Ball Animation Lab

In this lab we are going to create 3 different ball animations.

---

## [0] Set up


{{< code-action "Go to your" >}} `cs9/unit00_drawing` **folder.**

```shell
cd ~/desktop/making_with_code/cs9/unit00_drawing/
```

{{< code-action "Clone your repo. This will copy it onto your computer." >}}  
```shell
git clone https://github.com/the-isf-academy/lab_ball_animation_yourGithubUsername
```
> Below you'll see that the `git clone` command has a `yourGithubUsername`. 
>
> **You need to replace this with your username**
>
> *e.g. `https://github.com/the-isf-academy/lab_ball_animation_emmaqbrown`*


{{< code-action "In the Terminal, type the following command to open the lab folder." >}}
```shell
cd lab_ball_animation_yourGithubUsername
```

{{< code-action "Enter the Poetry Shell to start the lab." >}} As a reminder, we will run this command at the start of each lab, but only when we are inside a lab folder.
```shell
poetry shell
```

{{< aside "Exiting the poetry shell" >}}
When you want to exit the shell, you can type `exit` or `^D`
{{< /aside >}}

{{< code-action "Take a look at the files inside with:" >}} `ls`
- `breathing_animation.py`
- `movement_animation.py`
- `color_animation.py`
- `basic_shapes.py`
- `helpers.py`
- `settings.py`
- `extension_animation.py`

---

## [1] Ball Animations


### [Breathing]

{{< code-action "Open the file:" >}} `breathing_animation.py`

{{< code-action "Try running the file:" >}} `python breathing_animation.py`. Currently, there is no animation. A purple ball just appears on the screen. 

{{< code-action "Change the code so the ball grows and shrinks." >}} It should look like it's "breathing".

{{< figure src="images/courses/cs9/unit00/breathing_animation.gif" width="50%">}}

---



### [Movement]

{{< code-action "Open the file:" >}} `movement_animation.py`

{{< code-action "Try running the file:" >}} `python movement_animation.py`. Currently, there is no animation. A light blue ball just appears on the screen. 

{{< code-action "Change the code so the ball moves around the screen." >}} It up to you to decide how it moves. It could:
- move up or down
- move up and down
- move diagonally
- move randomly 

{{< figure src="images/courses/cs9/unit00/movement_animation.gif" width="50%">}}


---


### [Color]

{{< code-action "Open the file:" >}} `color_animation.py`

{{< code-action "Try running the file:" >}} `python color_animation.py`. Currently, there is no animation. A green ball just appears against a yellow background on the screen.

{{< code-action "Change the code so the ball changes in color." >}} It up to you to decide how the color changes.
> Note, the color is decided with RGB values as opposed to names of colors. 
> 
> - `line 39`: changes the color mode to accept RGB values

{{< figure src="images/courses/cs9/unit00/color_animation.gif" width="50%">}}


---

## [3] Deliverables


{{< deliverables "For this lab, you should:" >}}

**Once you've successfully completed the sequence be sure to fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLScz0x6-s3GRD9P7oZlcqq24XifGDTw9BQ_j8t8TIqqRYw0naw/viewform?usp=sf_link)**.


{{< code-action "Push your work to Github:" >}}
- git status
- git add file_name.py file_name2.py
- git status
- git commit -m "describe your drawing and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push

{{< /deliverables >}}


---

# [4] Extension


{{< code-action "Open the file:" >}} `extension_animation.py` in Atom. It is just an empty file. 


{{< code-action "Code a custom animation of your choosing!" >}} Here is an example of what you could create:

{{< figure src="images/courses/cs9/unit00/extension_animation.gif" width="50%">}}

