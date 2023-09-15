---
title: "4. Banjo - Fortune"
type: lab
slug: lab_riddle_server

# draft: true
---

# Fortune Server

In this lab we are going to delve further into Banjo by focusing on `models.py` and error handeling in `views.py`.


📖 **Open the Banjo documentation:** [cs.fablearn.org/docs/banjo/index.html](https://cs.fablearn.org/docs/banjo/index.html)

{{< expand "Debugging" >}}

**If you are getting an "Access Denied" error when visiting the `/api` route:**

0. Go to [chrome://net-internals/#sockets](chrome://net-internals/#sockets) 
0. Select "Flush socket pool"
0. Refresh the page

{{< /expand >}}


---

## [0] Set Up

You are each able to run a locally hosted riddle server on your laptop using Banjo.

{{< code-action "Start by going into the unit folder and the lab." >}} Remember to replace `YOUR_USERNAME` with your actual Github username.
```shell
cd ~/desktop/making_with_code/cs10/unit00_networking/
cd lab_fortune_yourgithubusername
```

{{< code-action "Enter the Poetry shell" >}}
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


💻 **Test the server at the `/api` route:**  [127.0.0.1:5000/api](127.0.0.1:5000/api)

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
    fortune_statement = StringField()
    num_likes = IntegerField()

    category_happy = BooleanField()
    category_sad = BooleanField()

    def increase_likes(self):
        self.num_likes += 1
        self.save()

    def change_statement(self,new_statement):
        self.fortune_statement = new_statement
        self.num_likes = 0
        self.save()
```


{{< code-action "Start by opening up the primary folder:" >}} `/app`

```shell
code app
```

{{< code-action >}} **Open the `models.py` file.** Be sure to understand how `increase_likes()` and `change_statement` are working. 


---

## [3] Views.py

{{< code-action >}} **Open the `views.py` file.** This server has 5 endpoints:
- `fortune_teller/new`
- `fortune_teller/all`
- `fortune_teller/edit`
- `fortune_teller/like`
- `fortune_teller/random`


--- 

### Error Handeling 

Each endpoint works, but there is currently NO error handeling.

💻 **Systemtically test each endpoint and add in the necessary error JSON messages.** The best way to systematically test, is to try to break it! 
> Be sure to provide error messages that provide relevant information to the user.


{{< code-action >}} **When are you confident your endpoints are perfect, runserver outside of `--debug` mode.**
```shell
banjo 
```

💻 **Test the server at the `/api` route:**  [127.0.0.1:5000/api](127.0.0.1:5000/api)

☑️ **Successful error should recieve zero HTTP 500 errors.** If you recieve a 500 error, you have not properply handled all the potential errors.

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

## [5] Extensions


### Archive 

Currently there is no feature to delete a fortune. It can be risky to peremantly delete an item from the database, so instead let's create an archive feature.

💻**Create a feature to "archive" a `Fortune` and hide it from queries.** If a `Fortune` is "archived", it should not be queried in `fortuen_teller/all`, `fortune_teller/like` or `fortune_teller/random`.

🤔 **Consider:**
- what field type is best? 
- which files will you need to edit?
- will you need a new endpoint?
- how will you edit existing endpoints?

---

### Calculate Popularity % 

💻 **Use the `FloatField` to store a `popularity_percentage` for each `Fortune`.** It is up to you to decide how to calculate this percentage. You may want to:
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

💻 **Try and incorporate a many-to-one relationship in `models.py`.** A few ideas:
- each `Fortune` can have many `Feedback`s.
- each `Fortune` can have many `Feedback`s.


<!-- 
### Interface: Riddle Client 

We will talk more about clients later in this unit, but for now just aquaint yourself with the [Requests library](https://requests.readthedocs.io/en/latest/). 

{{< code-action >}} **Create a new python file:** `client.py`

{{< code-action >}}  **Try to access the public Riddle server, [http://sycs.student.isf.edu.hk/riddles/all](http://sycs.student.isf.edu.hk/riddles/all), using the `Requests` library in this file.**

{{< code-action >}} **A few more things to try:**
- format the response JSON in a user friendly, readable format 
- hit a GET route that requires a payload
- hit a POST route that requires a payload  -->


