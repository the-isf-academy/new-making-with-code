---
Title: "Project: Backend"
# draft: true
---

# Networking: Social Computing Project

In this unit there will be 2 mini-projects for you to create a social computing app. In this part of the project, you will create the Banjo backend. 

{{< aside "Reference: Banjo Documentation" >}}

[cs.fablearn.org/docs/banjo/index.html](https://cs.fablearn.org/docs/banjo/index.html)

{{< /aside >}}


---

## [0] Project Management Sheet

This is a big project, and you will get lost or frustrated if you don't do some planning up front.
Before you start working on your project, you are required to complete the Project Management Sheet and meet with a teacher.

{{< code-action >}} **Find your project management sheet in your Google Drive folder: "Networking Project: Backend".**

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

{{< code-action "Download your repository with starter code for your project." >}} Be sure to change `yourgithubusername` to your actual Github username.

```shell
cd ~/desktop/making_with_code/cs10/unit00_networking/
git clone https://github.com/the-isf-academy/project_networking_backend_yourgithubusername.git
cd project_networking_project_networking_backend_yourgithubusername
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

The `project_networking` repository containing the following:
  - `\app`
    - `models.py` - This is where you will define your model.
    - `views.py` - This is where you will define your routes and endpoints.
  - `database.sqlite` - This is your database file.
  - `README.md` - This is documentation for the backend of your project.
  - `client.py` - This is how the user will interact with your server.

{{< code-action "Start coding your first milestone!" >}} With you project management sheet approved by a teacher and your starter code downloaded, you're ready to start creating.

---

## [2] Criteria


**This project will be assessed on the following criteria:**
- project planning [3]
- iterative development [3]
- model architecture [3]
- endpoint architecture [3]
- readability [3]
- documentation [3]


**For each criteria you will be assessed on a score from 0-3. With 8 criteria, there is a total of 24 potential points.** 
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
- I can develop my project iteratively over time
    - I can track the development of my project by successfully committing to Github a minimum of each class work day
    - I can write descriptive commit messages that accurately describe the changes made
    - I can systematically break down my project into smaller chunks
    - I can identify a Minimum Viable Product (MVP) and complete it before adding additional features
- I can write model architecture
  - I can use Banjo to effectively build a model with necessary features
  - I can write fields with appropriate data types
  - I can write methods to simplify code
  - I can write a model with multiple uses in mind
- I can write endpoint architecture
  - I can appropriately use GET and POST requests
  - I can write endpoints with user experience in mind
  - I can return descriptive and accurate JSON
  - I can return helpful error messages
- I can write code with readability in mind
  - I can use descriptive names for models, fields, methods, endpoints, variables, and  parameters
  - I can write descriptive comments
- I can write documentation with public use in-mind
  - I can write a README.md that is clear enough for someone with no prior knowledge of my project to understand
  - I can write a README.md that is complete and accurate to my final project


*Keep these success claims in mind when coding your project and assessing yourself.*

---

## [3] Deliverables


{{< deliverables  >}}

- A `Networking Project: Backend` - Google sheet. This is where you will plan your project.
- A `project_networking_backend` repository containing the following:
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
- `git add -A`
    - this adds all changed files to the commit
- `git status`
- `git commit -m "describe your updates here"`
  > be sure to customize this message, do not copy and paste this line
- `git push`
{{< /deliverables >}}
