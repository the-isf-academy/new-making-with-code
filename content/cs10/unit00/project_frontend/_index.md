---
Title: "Project: Frontend"
# draft: true
---

# Networking: Social Computing Project

In this mini-project, you will create the client frontend for your own or a peer's API.

{{< aside "Key Links" >}}

📖 [Student API Information](http://sycs.student.isf.edu.hk/)

📖 [Google Colab with Documentaiton](https://colab.research.google.com/drive/1moJbkEmXMNAnLbKFsWUxNoSD9YGbpIP_?usp=sharing)

{{< /aside >}}

---

## [0] Project Planning

Before you start working on your project, you will outline your implementation of the API. 

✏️ **Fill out the "Project Networking Backend Planning Document".** 

👋 **Meet with a teacher to discuss your idea before beginning to code**


---

## [1] Starter Code


{{< code-action "Download your repository with starter code for your project." >}} Be sure to change `yourgithubusername` to your actual Github username.

```shell
cd ~/desktop/making_with_code/cs10/unit00_networking/
git clone https://github.com/the-isf-academy/project_networking_frontend_yourgithubusername
cd project_networking_frontend_yourgithubusername
```

{{< code-action "Enter the poetry shell." >}}
```shell
poetry shell
```

{{< code-action "Install requirements" >}}
```shell
poetry install
```

📄 **It contains the following:**
- A `project_networking_frontend` repository containing the following:
  - `client.py` - This is where you will manage the user interactions. 
  - `requests_interface.py` - This is where you will manage the HTTP requests.
  - `view.py` - This is where you will manage the input and output for the user. 
  - `README.md` - This is documentation for the frontend of your project.

{{< code-action "Start coding your MVP (minimum viable product)!" >}}

---

## [2] Criteria


**This project will be assessed on the following criteria:**
- project planning [3]
- iterative development [3]
- code readability [3]
- user interaction [3]
- API usage [3]


**For each criteria you will be assessed on a score from 0-3** 
- 0 - no evidence of the practice
- 1 - limited evidence of the practice
- 2 - adequate evidence of the practice
- 3 - substantial evidence of the practice


---

### [Success Claims]

Successful computer scientists should be able to make the following claims:
- I can thoughtfully plan and manage a computer science project 
    - I can consider the components of my project before coding
    - I can choose a project of appropriate scale for the time allowed
- I can develop my project iteratively over time
    - I can track the development of my project by successfully committing to Github a minimum of each class work day
    - I can write descriptive commit messages that accurately describe the changes made
    - I can systematically break down my project into smaller chunks, priortizing the MVP 
- I can write code with readability in mind
  - I can write code another computer scientist could easily understand
  - I can keep all input/output in the view, all API calls in the requests interface, and user logic in the client
  - I can use descriptive names for variables, methods, data_structures, etc. 
  - I can write descriptive comments
  - I can include a README that describes my project
- I can write a frontend with user interaction in mind
  - I can write an easy to use client with clear instructions and appropriate formatting
  - I can ensure users are able to interact with the client as it is intended
  - I can provide appropriate error messaging to the user if a user error occurs
- I can successfully use my chosen API
  - I can create a requests interface that makes get and post requests
  - I can prevent unexpected user scenarios from crashing the client


*Keep these success claims in mind when coding your project and assessing yourself.*


---

## [3] Deliverables

{{< deliverables >}}

**🗓️ Timeline:** You have 4 in-class work days. 

You may find it necessary to work outside of school, however if you are focused in class you can complete the project within the allotted blocks. Our office hours are Tuesday during CCA in B405. 

| CS10.1 Dates | CS10.2 Dates | Agenda                         |
|--------------|--------------|--------------------------------|
| 30 Dec       | 29 Dec       | Project Intro & Planning Sheet |
| 5 Dec       | 1 Dec       | Work Day - MVP                 |
| 7 Dec       | 4 Dec       | Work Day - Peer Review         |
| 12 Dec       | 6 Dec       | Due at End of Class       |

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
