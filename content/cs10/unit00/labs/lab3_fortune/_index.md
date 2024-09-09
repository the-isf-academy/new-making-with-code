---
title: "4. Banjo - Fortune"
type: lab
slug: lab_fortune_server

# draft: true
---

# Fortune Server

In this lab we are going to delve further into Banjo by focusing on `models.py` and error handling in `views.py`.


📖 **Open the Banjo documentation:** [the-isf-academy.github.io/banjo_docs/](https://the-isf-academy.github.io/banjo_docs/)


{{< expand "Debugging" >}}

**If you are getting an "Access Denied" error when visiting the `/api` route:**

0. Go to <a href="chrome://net-internals/#sockets" >chrome://net-internals/#sockets</a>
0. Select "Flush socket pool"
0. Refresh the page

{{< /expand >}}


---

## [0] Set Up

For this lab, we need to download software to view the database in a nicely formatted chart.

{{< code-action "Download dbsqlite onto your computer:" >}} [https://sqlitebrowser.org/dl/](https://sqlitebrowser.org/dl/)

{{< figure src="https://sqlitebrowser.org/images/sqlitebrowser.svg" alt-text="database icon" >}}

You are each able to run a locally hosted fortune server on your laptop using Banjo.

{{< code-action "Now, let's clone the repository" >}} in your `cs10\unit00_networking` folder.  Be sure to change `yourgithubusername` to your actual Github username.

```shell
cd ~/desktop/making_with_code/unit04_networking/
git clone https://github.com/the-isf-academy/lab_fortune_yourgithubusername
cd lab_fortune_yourgithubusername
```

{{< code-action "Get the necessary packages" >}}
```shell
poetry update
```


{{< code-action "Enter the Poetry shell" >}}
```shell
poetry shell
```



---
## [1] Running the Fortune Server


{{< code-action "Start your local server." >}}
```shell
banjo --debug
```


💻 **Test the server using `HTTPie`:**  [127.0.0.1:5000/fortune/all](http://127.0.0.1:5000/fortune/all)

{{< figure src="https://m.media-amazon.com/images/I/71DW-Qp7J6L.jpg" width="25%">}}

---



## [2] Models.py 

Banjo has 4 basic options for Field types
- `StringField`
- `IntegerField`
- `FloatField`
- `BooleanField`


👀 **Let's start by looking at the model for `Fortune`.**

```python
from banjo.models import Model, StringField, IntegerField, BooleanField

class Fortune(Model):
    statement = StringField()
    category = StringField()
    likes = IntegerField()
    archive = BooleanField()
```

---

### Viewing the Database

You have just downloaded a simple server that hosts `Fortunes` onto your laptop. Let's start by looking at the its database.

{{< code-action "Open the database in the DB Browser:" >}}
```shell
open database.sqlite
```

{{< code-action "Select" >}} `Browse Data`

{{< figure src="images/courses/cs10/unit00/02_banjo_00.png" alt-text="databases" >}}


{{< look-action "Here you will see all of the riddles that are in your locally hosted server." >}} This database file gets updated each time make a `POST` request.

{{< figure src="images/courses/cs10/unit00/02_banjo_01.png" alt-text="databases" >}}

{{< code-action "Try changing or adding rows." >}} 

{{< code-action >}} **Be sure to save `command + s` the database to ensure the changes are saved.**


💻 **See you changes by sending a `GET` request to:**  [127.0.0.1:5000/fortune/all](http://127.0.0.1:5000/fortune/all)

---

**In this lab you will edit `models.py` and `views.py`.**

{{< code-action "Start by opening up the primary folder:" >}} `/app`

```shell
code app
```

{{< code-action >}} **Open the `models.py` file.** You will write two methods to update the `likes` and `statement` fields.

---

### Update the `likes`

{{< code-action >}} **Write the `increase_likes()` method.**
- increase `likes` by 1
- save the object 

**Example usage:**

```shell
one_fortune = Fortune.objects.get(id=1])
one_fortune.increase_likes()
```

---

### Update the `statement`

{{< code-action >}} **Write the `change_statement()` method.**
- it takes `new_statement` as a parameter
- it changes the `statement` field to the `new_statement`
- reset the `likes` to 0
- save the object 

**Example usage:**

```shell
one_fortune = Fortune.objects.get(id=1])
one_fortune.change_statement('You will win a tesla')
```

---

## [3] Views.py

{{< code-action >}} **Open the `views.py` file.** This server has 2 endpoints:
- `/new`
- `/all`

It is up to you to write `/likes`, `/change_statement`, and `/search`


--- 


### /like

{{< code-action >}} **Write the `fortune/like` endpoint.** 
- **HTTP method:**  `post`
- **Payload/args:**  `id`
- if the fortune exists 
    - increase the likes 
    - return the fortune with the `id`, `statement`, `likes`, `category`
- else  
    - a helpful error message

{{< checkpoint >}}

💻 **Test the endpoint in the `HTTPie desktop app`**

```shell
http://127.0.0.1:8000/fortune/like id=1
```

✔️ **It should return `json` like:**

```json
{
  "fortune": {
    "id": 1,
    "statement": "You will win a tesla",
    "likes": 10,
    "is_happy": "true"
  }
}
```
{{< /checkpoint >}}

---

### /change_statement

{{< code-action >}} **Write the `fortune/change_statement` endpoint.** 
- **HTTP method:**  `post`
- **Payload/args:**  `id`, `new_statement`
- if the fortune exists 
    - change the statement
    - return the fortune with the `id`, `statement`, `likes`, `category`
- else  
    - a helpful error message

{{< checkpoint >}}

💻 **Test the endpoint in the `HTTPie desktop app`**

```shell
http://127.0.0.1:8000/fortune/change_statement id=1 new_statement="You will win a new iPhone"
```

✔️ **It should return `json` like:**

```json
{
  "fortune": {
    "id": 1,
    "statement": "You will win a new iPhone",
    "likes": 0,
    "is_happy": "true"
  }
}
```
{{< /checkpoint >}}

---


### /all/happy

{{< code-action >}} **Write the `fortune/all/happy` endpoint.** 
- **HTTP method:**  `get`
- **Payload/args:**  none
- It should return all of the fortunes with `is_happy` set as `True`

📖 **Check the banjo documentation to find the best way to query the database:** [the-isf-academy.github.io/banjo_docs/](https://the-isf-academy.github.io/banjo_docs/)

🤔 **Consider:**
- Which existing endpoint is similar? 
- How should you format the json that you return?
- What should you return to the user if no fortunes match their search term?

{{< checkpoint >}}

💻 **Test the endpoint in the `HTTPie desktop app`**

```shell
http://127.0.0.1:8000/fortune/all/happy
```

✔️ **It should return `json` like:**

```json
{
    "fortunes": [
        {
        "id": 1,
        "statement": "A surprise pizza is coming",
        "likes": 0,
        "is_happy": true
        },
        {
        "id": 2,
        "statement": "A random act of kindness will lead to a new friendship",
        "likes": 0,
        "is_happy": true
        },
    ]
}
```
{{< /checkpoint >}}

---


### /search

{{< code-action >}} **Write the `fortune/search` endpoint.** 
- **HTTP method:**  `get`
- **Payload/args:**  `keyword`
- It should return all of the fortunes with the keyword. 
- If no fortunes exist, provide a helpful error message

📖 **Check the banjo documentation to find the best way to query the database:** [the-isf-academy.github.io/banjo_docs/](https://the-isf-academy.github.io/banjo_docs/)

🤔 **Consider:**
- Which existing endpoint is similar? 
- How should you format the json that you return?
- What should you return to the user if no fortunes match their search term?

{{< checkpoint >}}

💻 **Test the `fortune/like` endpoint in the `HTTPie desktop app`**

```shell
http://127.0.0.1:8000/fortune/search keyword="surprise"
```

✔️ **It should return `json` like:**

```json
{
  "fortunes": [
    {
      "id": 1,
      "statement": "A surprise pizza is coming",
      "likes": 0,
      "is_happy": true
    },
    {
      "id": 6,
      "statement": "A surprise typhoon day is in your future",
      "likes": 0,
      "is_happy": true
    }
    ]
}
```
{{< /checkpoint >}}


---

## [6] Deliverables


{{< deliverables >}}  

**Once you've successfully completed the worksheet be sure to fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSdzNtmIQhpra6TBJ2A4s4b9wpne6fdaP0w5dTd9vDjkWJQxZw/viewform?usp=sf_link).**

{{< code-action "Push your work to Github:" >}}
- git status
- git add -A
- git status
- git commit -m "describe your code and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push

{{< /deliverables >}}

---

## [7] Extensions


### Archive 

Currently there is no feature to delete a fortune. It can be risky to permanently delete an item from the database, so instead let's utilize the archive feature.

💻 **Write a method `change_archive()`** that sets the `archive` field to `False`.

💻 **Write a new route `/change_archive` to change the `archive` field of a fortuen with a given `id`.**

💻 **Change your exisitng routes (`/all`, `/search`) to only return fortunes with `arhive` set to `True`.**


---

### Calculate Popularity % 

💻 **Create a new field `popularity_percentage` to store a  for each `Fortune`.** It should be a `FloatField`. It is up to you to decide how to calculate this percentage. You may want to:
- add additional fields 
- loop through all of the database



---


### Foreign Key

Banjo has the ability to have relational databases. 

```python
from banjo.models import Model, StringField, IntegerField, ForeignKey, BooleanField, FloatField

class Artist(Model):
    name = StringField()


class Song(Model):
    name = StringField()
    artist = ForeignKey(Artist)
```

As Banjo is a wrapper over Django, it works just as the Django documentation states [HERE](https://docs.djangoproject.com/en/4.2/topics/db/examples/many_to_one/).

In the example code above, a **Artist** can be associated with many **Song** objects, but a **Song** object can only have one **Artist** object. 

💻 **Try to incorporate a many-to-one relationship in `models.py`.** An example:
- each `Person` could have many `Fortune`s.


<!-- 
### Error Handling 

Each endpoint works, but there is currently NO error handling.

💻 **Systematically test each endpoint and add in the necessary error JSON messages.** The best way to systematically test, is to try to break it! 
> Be sure to provide error messages that provide relevant information to the user.


{{< code-action >}} **When are you confident your endpoints are perfect, run the server outside of `--debug` mode.**
```shell
banjo 
```

💻 **Test the server at the `/api` route:**  [127.0.0.1:5000/api](127.0.0.1:5000/api)

☑️ **Successful error should recieve zero HTTP 500 errors.** If you recieve a 500 error, you have not properly handled all the potential errors. -->
