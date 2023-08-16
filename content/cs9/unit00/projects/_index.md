---
Title: Project
draft: true
---

# Animation Project

In this project you will make an animated drawing (or a GIF!) using Python's turtle library.

It's up to you to make a drawing you actually care about making. Your teachers will help you choose a project that's a good level of challenge.

Here are a few examples from last year to get you started. More can be found at the `gallery` page.

{{< columns >}}

{{< figure src="images/courses/cs9/unit00/00_project_2021_edwin.gif" width="75%" title="by Edwin" >}}
<--->
{{< figure src="images/courses/cs9/unit00/00_project_2021_charlotte.gif" width="75%" title="by Charlotte" >}}
{{< /columns >}}




---

## [0] Project Management Booklet: Planning 

This is a big project, and you will get lost or frustrated if you don't do some planning up front. You are required to fill out the planning section of the Project Booklet and get it approved by a teacher. 


{{< write-action "Fill out the Project Overview and Project Design sections of the Booket." >}}

**👀 Once you have completed your planning document, meet with a teacher to talk through your project.**


---

##  [1] Starter Code

For this project, your code will live in a git repository. It is your responsibility to regularly commit to your repository.

{{< code-action "Download your respository with starter code for your project." >}}
> replace the `yourGithubUsername` with your Github username.
>
> *example:*
>
> *`git clone https://github.com/the-isf-academy/project_animation_emmaqbrown.git`*


```shell
cd ~/Desktop/making_with_code/cs9/unit00_drawing/
git clone https://github.com/the-isf-academy/project_animation_yourGithubUsername.git
```

It contains the following files:
- `project.py` When this program runs, it should draw your project.
- `settings.py` This is where you settings for your animation should be stored.
- `README.md` This is documentation for your project for other people who may want to use your project.


{{< code-action "Start coding your first milestone!" >}} With you design document approved by a teacher and your starter code downloaded, you're ready to start creating.

---

## [3] Criteria

{{< columns >}}

{{< figure src="images/courses/cs9/unit00/00_project_2020_eric.gif" width="75%" title="by Eric" >}}
<--->
{{< figure src="images/courses/cs9/unit00/00_project_2020_austin.gif" width="75%" title="by Austin" >}}
{{< /columns >}}

**This project will be assessed on the following criteria:**
- project managment
- iterative development
- readability
- abstraction
- decomposition

**For each criteria you will be assessed on a score from 0-3:**
- 0 - no evidence of the practice
- 1 - limited evidence of the practice
- 2 - adequate evidence of the practice
- 3 - substantial evidence of the practice

*To do well in this project, you should be able to concretely demonstrate that you can successfully do each practice*

---


### [Success Claims]

Successful computer scientists should be able to make the following claims:
- I can thoughtfully plan and manage a large computer science project.  
    - I can consider the components of my project before coding
    - I can manage my time well and complete the project by the deadline
    - I can update my process journal on an ongoing basis to organize by thoughts for the next work day
- I can develop my project iteratively over time
    - I can track the development of my project by successfully committing to Github a minimum of each class work day
    - I can write descriptive commit messages that accurately describe the changes made
    - I can systematically breakdown my project into smaller chunks  
- I can write code with readability in mind
    - I can write code as readable as possible for another CS student to understand
    - I can use descriptive names for modules, variables, and functions
    - I can write descriptive comments to describe complex pieces of the code
- I can effectively use the principle of abstraction to make my code more efficient and elegant
    - I can write a function with paramters
    - I can manipulate control flow with conditional statements
    - I can use loops to repeat commands
     can write functions with parameters
- I can effictively use the principle of decomposition to make my code more efficient and elegant
    - I can write functions to be used in different scenarios
    - I can write modules for different aspects of my project

*Keep the success claims in mind when coding your project.*

---

### [Scoring]

The project is scored out of 7. It will be calculated by adding the score from each criteria, then referencing the bands:
- 1 = 0
- 2 = 1
- 3 = 2-3
- 4 = 4-6
- 5 = 7-11
- 6 = 12-13
- 7 = 14-15

---

## [3] Deliverables

{{< deliverables  "Projects are due on Friday, 25 Novemeber." >}}


- `Unit 00 Animation Project: Planning Document` in your Google Drive folder
- `project_animation` repository containing the following files:
    - `project.py` When this program runs, it should draw your project.
    - `settings.py` This is where you settings for your animation should be stored.
    - `README.md` This is documentation for your project
    - At least one additional module (written by you)

{{< code-action "Push your work to Github:" >}}
- `git status`
- `git add project.py`
    - you can add multiple files by putting a space inbetween each file
    - *e.g. `git add project.py settings.py`*
- `git status`
- `git commit -m "describe your drawing and your process here"`
  > be sure to customize this message, do not copy and paste this line
- `git push`
{{< /deliverables >}}



