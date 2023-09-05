---
title: "3. Banjo Server"
type: lab
slug: lab_riddle_server

draft: true
---

# Riddle Server

In this lab we are going to learn how the riddle server is made using Banjo.

📖 **Open the Banjo documentation:** [cs.fablearn.org/docs/banjo/index.html](https://cs.fablearn.org/docs/banjo/index.html)

---

## [0] Set Up

You are each able to run a locally hosted riddle server on your laptop using Banjo.

{{< code-action "Start by going into the unit folder and the lab." >}} Remember to replace `YOUR_USERNAME` with your actual Github username.
```shell
cd ~/desktop/making_with_code/cs10/unit00_networking/
cd lab_banjo/yourgithubusername
```


{{< code-action "Enter the Poetry shell" >}}
```shell
poetry shell
```


---
## [1] Local Riddle Server

You are each able to run a locally hosted riddle server on your laptop using Banjo.

### Starting the Server

{{< code-action "Now, let's start your local server." >}} We use `--debug` to provide more information when in development stage.
```shell
banjo --debug
```
```shell
No changes detected in apps 'app', 'banjo'
Operations to perform:
  Apply all migrations: admin, app, auth, contenttypes, sessions
Running migrations:
  No migrations to apply.
No changes detected in apps 'banjo', 'app'
Operations to perform:
  Apply all migrations: admin, app, auth, contenttypes, sessions
Running migrations:
  No migrations to apply.
Performing system checks...

System check identified no issues (0 silenced).
September 16, 2022 - 02:40:21
Django version 4.1.1, using settings 'banjo.settings'
Starting development server at http://127.0.0.1:5000/
Quit the server with CONTROL-C.
```

---


### Accessing the Server

💻 **You can now visit this server in your web browser, just as you did with the riddler server hosted on the internet:**  [127.0.0.1:5000/riddles/all](http://127.0.0.1:5000/riddles/all)

**In order to send requests to the other endpoints, you will need always have 2 Terminal windows open.**
- 1 window will run the server
- 1 window will send `HTTP` requests

{{< code-action "Open another Terminal window." >}} You can either open a new tab, `command+t`, or open a new window with `command+n`.

{{< code-action "View all the riddles in the second Terminal window." >}}
```shell
http get http://127.0.0.1:5000/riddles/all
```

{{< look-action " Look at the Terminal window running the server. Notice how it recorded your request." >}}
```shell
[16/Sep/2022 02:44:20] "GET /riddles/all HTTP/1.1" 200 1069
```

Your version of the riddle server only has the 2 endpoints:
- `/riddles/all`
- `/riddles/guess`

{{< checkpoint >}}

{{< code-action "Explore both endpoints via the Terminal and be sure to successfully:" >}}
- view all riddles without the answers
- guess a riddle
{{< /checkpoint >}}

---

## [2] What is Banjo?

**This server is written using [Banjo](https://cs.fablearn.org/docs/banjo/index.html)**, a wrapper for [Django](https://www.djangoproject.com/). It allows users to quickly create models with a persistant database and API.

📁 **Banjo apps must have an `app` folder. Within the app folder must be two files: `models.py`, `views.py`.** The `database.sqlite` file is created when the server is first started. It is stored at the same level as `app`. Here is an example file structure:
```shell
lab_riddle_server
|
└──app
|   ├──models.py
|   └──views.py
└──database.sqlite
```
- `models.py` - A model is essentially an abstracted class. Just as a class has properties, a model has fields. When defining a model's fields, you must specify the data type.
- `views.py` - The views are where you define the API functionality. Here is where you decide what the `endpoints` are and the type of `HTTP` request it will require.

📄 **In this lab, we are going to be primarily focused on the `views.py` file.**

---

## [3] Writing Routes

In this lab, you will build out the functionality of the Riddle server. Currently, your file only has `riddles/all` and `riddle/new`. 

**It is up to you to add the following endpoints:**
- `riddles/one`
- `riddles/guess`
- `riddle/difficulty`
- `riddle/random`



{{< code-action "Start by opening up the primary folder:" >}} `/app`

```shell
code app
```

{{< code-action >}} **Open the `views.py` file.** Here is where you will write the additional endpoints. 

📖 **Open the [Banjo Views Documentation](https://cs.fablearn.org/docs/banjo/views.html).** You will need to reference this and the exisiting routes in `views.py`.

🌐 **You may also want to reference the Riddle server that is live on the web:** [sycs.student.isf.edu.hk/api](http://sycs.student.isf.edu.hk/api). This is a unique route `/api` that provides a basic frontend interaction with the API.

---

### riddles/one

{{< code-action >}} **Write the `riddles/one` endpoint.** 
- **HTTP method:** `get`
- **Payload/args:** `id`
- **Return:** a single `Riddle` with the `question`, `guesses`, and `correct` properties


🤔 *Which `method` in the `Riddle` `model` could be useful?*

{{< checkpoint >}}

💻 **Test the `riddles/one` endpoint in a separate Terminal window from the server..**

```shell
http get http://127.0.0.1:5000/riddles/one id=0
```

{{< /checkpoint >}}

---

### riddles/guess

{{< code-action >}} **Write the `riddles/guess` endpoint.** 
- **HTTP method:**  `post`
- **Payload/args:**  `id` and `guess`
- **Return:** 
  - if the guess was correct
    - message telling the user they were correct
    - a single `Riddle` with the `question`, `guesses`, `correct`, and `answer` properties
  - if the guess was incorrect
    - message telling the user they were incorrect
    - a single `Riddle` with the `question`, `guesses`, and `correct`, properties

🤔 *Which `method` in the `Riddle` `model` could be useful?*


{{< checkpoint >}}

💻 **Test the `riddles/guess` endpoint in a separate Terminal window from the server..**

```shell
http post http://127.0.0.1:5000/riddles/guess id=1 guess="A carpet"
```

{{< /checkpoint >}}

---


### riddles/difficulty

{{< code-action >}} **Write the `riddles/difficulty` endpoint.** 
- **HTTP method:** `get`
- **Payload/args:** `id`
- **Return:** 
    - a single `Riddle` with the `question`, `guesses`, `correct`, and `difficulty` properties

🤔 *Which `method` in the `Riddle` `model` could be useful?*


{{< checkpoint >}}

💻 **Test the `riddles/guess` endpoint in a separate Terminal window from the server..**

```shell
http get http://127.0.0.1:5000/riddles/difficulty id=1 
```

{{< /checkpoint >}}

---

### riddles/random

{{< code-action >}} **Write the `riddles/random` endpoint.** 
- **HTTP method:**`get`
- **Payload/args:** none
- **Return:**  a single `Riddle` with the `question`,  `correct`, and `guess` properties 

🤔 *Which query method may be useful? Be sure to reference the [Banjo documentation](https://cs.fablearn.org/docs/banjo/index.html).*


{{< checkpoint >}}

💻 **Test the `riddles/random` endpoint in a separate Terminal window from the server..**

```shell
http get http://127.0.0.1:5000/riddles/random 
```

{{< /checkpoint >}}

---

## [4] Deliverables


{{< deliverables >}}  

**Once you've successfully completed the worksheet be sure to fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSf8yjSaASsdDp2y4Zawso8Ko77nkhPH6ADf5BOTpPcO_kdtDw/viewform?usp=sf_link).**

{{< code-action "Push your work to Github:" >}}
- git status
- git add -A
- git status
- git commit -m "describe your code and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push

{{< /deliverables >}}

---

## [5] Extension

Currently, there's not way to see the answer unless you correctly guess the riddle. 

{{< code-action >}} **Write an endpoint that has the ability to view the solution of a given Riddle.** 
> *Hint: a new method in the `Riddle` class may be useful*

It should return `JSON` that looks something like:
```shell
{
    "riddle": [
        {
            "correct": 0,
            "guesses": 3,
            "id": 1,
            "question": "It goes up and down the stairs without moving.",
            "answer": "A carpet"
        }
    ]
}
```

{{< code-action >}} **Write an endpoint that has the ability to change the question or answer or a riddle.** 
> *Consider, what kind of HTTP request would be best for this?*