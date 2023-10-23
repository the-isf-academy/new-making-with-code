---
title: 11. More Animation
# draft: true
---

# More Animation Lab

In this lab we are going to continue to experiment with `SuperTurtle` and exploring decomposition and abstraciton.

---


## [0] Set Up



{{< code-action "Go to your" >}} `cs9/unit00_drawing` **folder.**

```shell
cd ~/desktop/making_with_code/cs9/unit00_drawing/
```

{{< code-action "Clone your repo. This will copy it onto your computer." >}}  
```shell
git clone https://github.com/the-isf-academy/lab_animation_yourGithubUsername
```
> Below you'll see that the `git clone` command has a `yourGithubUsername`. 
>
> **You need to replace this with your username**
>
> *e.g. `https://github.com/the-isf-academy/lab_animation_emmaqbrown`*




{{< code-action "In the Terminal, type the following command to open the lab folder." >}}
```shell
cd lab_animation_yourGithubUsername
```


{{< code-action "Enter the Poetry Shell to start the lab." >}} We will run this command at the start of each lab, but only when we are inside a lab folder.
```shell
poetry shell
```

{{< code-action >}} This lab uses a package called [SuperTurtle](https://github.com/cproctor/superturtle). To use SuperTurtle in this repo, we must install it using poetry. 
```shell
poetry install
```

{{< aside "Exiting the poetry shell" >}}
When you want to exit the shell, you can type `exit` or `^D`
{{< /aside >}}


{{< code-action "Take a look at the files inside with:" >}} `ls`
- `animation_tree.py`
- `experiment.py`
- `tree_parts.py`
- `shapes.py`



---


## [1] Tree Animations


This mini lab is designed to be a pick and choose adventure for practice animating with `SuperTurtle`.

{{< aside "Documentation" >}}  

For lab, we reccomend referencing the previous lab repository, `lab_superturtle`, and the offical documentation. 

📖 **SuperTurtle Documentation:** [superturtle.readthedocs.io/en/latest/animation.html](https://superturtle.readthedocs.io/en/latest/animation.html)

The offical documentation has a lot of information, so be sure to ask a teacher and experiment if you have any questions.

{{< /aside >}}


---

{{< code-action >}} **Let's start by running `animation_tree.py`**
```shell
python animation_tree.py
```

{{< figure src="images/courses/cs9/unit00/lab_11_tree1.gif" width="50%">}}

{{< code-action >}} **Take a look at the code with:** `code .` The main animation loop is in `animation.py`. It uses the `shapes.py` file and `tree_parts.py` from the `modules` lab.


{{< code-action >}} **Fist, add a moon!** Look in `shapes.py` for a function you can use to draw the moon!

{{< figure src="images/courses/cs9/unit00/lab_11_tree2.gif" width="50%">}}

{{< code-action >}} **Now move the moon and change its color!** 

{{< figure src="images/courses/cs9/unit00/lab_11_tree3.gif" width="50%">}}



---


## [2] Deliverables

{{< deliverables "For this lab, you should:" >}}
☑️ **At then end of class, be sure to fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSdLsonbvKv_BNic0gAlq_EsCnaeKj-v2m343KQDeypw65j0YQ/viewform?usp=sf_link)**.


{{< code-action "Push your code to Github" >}} 
0. `git status`
0. `git add file.py`
0. `git status`
0. `git commit -m "describe changes here"` 
0. `git push`

{{< /deliverables >}}

---

## [3] Experiment!

{{< code-action >}} **In `experiment.py`, experiment by creating your own animation to create a new design using functions in `shapes.py`.** We included the starter code from the [documentation](https://superturtle.readthedocs.io/en/latest/introduction.html#creating-animations), but feel free to delete it and start fresh!


A few ideas...
- a face with eyes that move 
- a car that moves across the screen 
- a llama with ears taht grow

{{< code-action >}} **Explore using the additional functions available to the animation transformations in [`SuperTurtle`](https://superturtle.readthedocs.io/en/latest/introduction.html).** Experiment with:
- `debug = True`?
- `last_frame`
- `cycles`
- `restore_state_when_finished()` in `movement`
- `dashes`, `dots`, and `rainbow` in `stroke`
- the available `easing` options
