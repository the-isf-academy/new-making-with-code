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
Before you start working on your project, you are required to complete the Project Management Sheet and meet with a teacher.

{{< code-action >}} **Find your project management sheet in your Google Drive folder: "Networking Project Management Sheet".**

✏️ **Fill out the brainstorm and plan your API.**

✋ **Meet with a teacher to discuss your idea before beginning to code.**

{{< aside "A few ideas to build on from last year's projects:" >}}

- collaborative story telling (each person adds a new word to a collaborative story)
- r/place, but with emojis or symbols 
- collaborative counting game like [this IRL game](https://dramaresource.com/count-to-20/#:~:text=Sit%20or%20stand%20in%20a,start%20again%20from%20the%20beginning.)
- collaborative hangman

{{< /aside >}}

---

## [1] Starter Code


In this lab, you will be working in groups, storing your shared code in your group's repository.

{{< code-action "Download your repository with starter code for your project." >}} Be sure to change `yourgithubusername` to your actual Github username.

```shell
cd ~/desktop/making_with_code/cs10/unit00_networking/
git clone https://github.com/the-isf-academy/project_networking_yourgithubusername.git
cd project_networking_project_networking_yourgithubusername
```

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
- project planning [3]
- iterative development [3]
- model architecture [3]
- api architecture [3]
- readability [3]
- documentation [3]


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


{{< deliverables  >}}

- A `Networking Project Management Sheet` - Google sheet. This is where you will plan your project.
- A `project_networking` repository containing the following:
  - `\app`
    - `models.py` - This is where you will define your model.
    - `views.py` - This is where you will define your routes and endpoints.
  - `database.sqlite` - This is your database file.
  - `README.md` - This is documentation for the backend of your project.

---

**🗓️ Timeline**

You have 5 in-class work days. You may find it necessary to work outside of school, however if you are focused in class you can complete the project within the allotted blocks. Our office hours are Tuesday during CCA in B405. 

| CS10.1 Dates | CS10.2 Dates | Agenda                         |
|--------------|--------------|--------------------------------|
| 12 Oct       | 11 Oct       | Project Intro & Planning Sheet |
| 16 Oct       | 17 Oct       | Work Day - MVP                 |
| 17 Oct       | 18 Oct       | Work Day - Peer Review         |
| 19 Oct       | 20 Oct       | Work Day - Documentation       |
| 24 Oct       | 25 Oct       | Due at End of Class            |

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
