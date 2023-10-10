---
Title: "Project: Backend"
# draft: true
---

# Networking: Social Computing Project

In this unit there will be 2 mini-project for you to create a social computing app. In this part of the project, you will create the Banjo backend. 


{{< aside "Reference: Banjo Documentation" >}}

[cs.fablearn.org/docs/banjo/index.html](https://cs.fablearn.org/docs/banjo/index.html)

{{< /aside >}}


---

## [0] Project Management Sheet

This is a big project, and you will get lost or frustrated if you don't do some planning up front.
Before you start working on your project, you are required to complete the both tabs of the Project Management Sheet.

{{< code-action >}} **Find your project management sheet in your Google Drive folder: "Networking Project Management Sheet".** Share the sheet with your group member(s)

{{< write-action "Fill out the both tabs." >}} Once you're completed, meet with a teacher to discuss your idea before beginning to code.

{{< aside "A few ideas..." >}}

- collaborative story telling (poetry, madlibs, etc.)
- collaboarative art project with emojis, symbols, or [ASCII art](https://www.asciiart.eu/)
- collaborative messaging board

{{< /aside >}}

---

## [1] Starter Code


In this lab, you will be working in groups, storing your shared code in your group's repository.

{{< code-action "Download your repository with starter code for your project." >}}

```shell
cd ~/desktop/making_with_code/cs10/unit00_networking/
git clone https://github.com/the-isf-academy/project_networking_group#.git
cd project_networking_group#
```
> replace `#` with your group number


{{< code-action "Enter the poetry shell." >}}
```shell
poetry shell
```

{{< code-action "Install requirements" >}}
```shell
poetry install
```

{{< code-action "Install Banjo" >}}
```shell
pip3 install django-banjo
```

It contains the following :
- A `project_networking` repository containing the following:
  - `\app`
    - `models.py` - This is where you will define your model.
    - `views.py` - This is where you will define your routes and endpoints.
  - `database.sqlite` - This is your database file.
  - `README.md` - This is documentation for the backend of your project.
  - `client.py` - This is how the User will interact wiht your server.

{{< code-action "Start coding your first milestone!" >}} With you project management sheet approved by a teacher and your starter code downloaded, you're ready to start creating.

---

## [2] Criteria


**This project will be assessed on the following criteria:**
- project management [3]
- iterative development [3]
- backend
  - model architecture [3]
  - api architecture [3]
  - backend readability [3]
- frontend
  - frontend readability [3]
  - frontend user error handling [3]
  - user interaction usability [3]


**For each criteria you will be assessed on a score from 0-3. With 8 criteria, there is a total of 24 potential points.** For each criteria, you will be awarded the same grade as your group member(s). However, the one exception is the *iterative development* criteria, which will be individually awarded.
- 0 - no evidence of the practice
- 1 - limited evidence of the practice
- 2 - adequate evidence of the practice
- 3 - substantial evidence of the practice


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
    - I can systematically break down my project into smaller chunks  
- I can develop a backend
  - I can write model architecture
    - I can use Banjo to effectively build a model with necessary features
    - I can write field with appropriate data types
    - I can write methods to simplify code
    - I can write a model with multiple uses in mind
  - I use write API architecture
    - I can appropriately use GET and POST requests
    - I can write endpoints with user experience in mind
    - I can return descriptive and accurate JSON
  - I can write backend code with readability in mind
    - I can use descriptive names for models, fields, methods, endpoints, variables, and  parameters
    - I can write descriptive comments
- I can develop a frontend
  - I can write frontend code with readability in mind
    - I can use descriptive names for variables, functions, data structures, etc.
    - I can write descriptive comments
  - I can write frontend code with user error handling in mind
    - I can provide appropriate error messaging to the user if a user error occurs
    - I can prevent unexpected user scenarios from crashing the client
  - I can write frontend code with user interaction in mind
    - I can write an easy to use client with clear instructions and appropriate formatting
    - I can ensure users are able to interact with the client as it is intended


*Keep these success claims in mind when coding your project and assessing yourself.*

---

### [Scoring]

The project is scored out of 7. It will be calculated by adding the score from each criteria, then referencing the bands:
- 1 = 0-1
- 2 = 2-4
- 3 = 5-8
- 4 = 9-13
- 5 = 14-18
- 6 = 19-22
- 7 = 23-24

---

## [3] Deliverables

{{< deliverables  "Projects are due on Friday, 25 Novemeber." >}}

- A `Networking Project Management Sheet` - Google sheet. This is where you will plan your project.
- A `project_networking` repository containing the following:
  - `\app`
    - `models.py` - This is where you will define your model.
    - `views.py` - This is where you will define your routes and endpoints.
  - `database.sqlite` - This is your database file.
  - `README.md` - This is documentation for the backend of your project.
  - `client.py` - This is how the User will interact wiht your server.

---

**🗓️ Timeline**

The project will begin on Wednesday, 02 November. You have 8 in-class work days. You may find it necessary to work outside of school, however if you are focused in class you can complete the project within the allotted blocks.

---

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
