---
title: "5. Client"
type: lab
draft: true
---

# Client

In this lab we will create a Client in the form of a Command Line Interface(CLI) for the Riddle server. We will use the `Requests` library to send and recieve HTTP requests. To learn more about the `Requests` library, checkout its [documentation](https://requests.readthedocs.io/en/latest/).


---


## [0] zxWhat is a client?


Since the riddle server is an API with no user interface, we end up writing a lot of
HTTP requests into the Terminal to use it. What if we had a program which took care
of making these requests for us? A program like this is called a *client*.

**Any app which uses the Internet is a client.**

{{< figure src=https://res.cloudinary.com/lwgatsby/f_auto/www/uploads/2023/05/client-server-network.jpg" width="50%">}}


The client, or app, is constantly making HTTP requests to a server to send and receive information.

---

## [1] Set Up


{{< code-action "Go to the unit folder, clone the riddler server lab, and cd into the repo." >}}
```shell
cd ~/desktop/making_with_code/cs10/unit00_networking/
git clone https://github.com/the-isf-academy/lab_client_YOURGITHUBUSERNAME
cd lab_client_YOURGITHUBUSERNAME
```

{{< code-action "Install the requirements." >}}
```shell
poetry install
```

{{< code-action "Enter the poetry shell." >}}
```shell
poetry shell
```

📄 **The repository has the following files.**  In this lab we will just focus on the bolded files.
- **`riddle_client.py`**
- **`test_riddle_client.py`**
- `gui_template.py`
- `gui_view.py`



---

## [2] Try the Client

We are going to create a **Graphical User interface (GUI)** for the riddler server. This will allow users to easily interact with the server without needing to explicitly make a `GET` or `POST` request.

{{< code-action "Try the client for the Riddle Server:" >}} `python client.py`
> Click on the various buttons to test the interaction

{{< figure src="images/courses/cs10/unit00/05_client_0.png" width="50%" alt-text="An HTTP GET request" >}}

{{< aside >}}

You can close the GUI with `command + w`, just like you would a normal window.

{{< /aside >}}


{{< code-action "Close the GUI and Open code:" >}} `code client.py`


---

### client.py

`client.py` creates a simple application using the `CustomTkinter` library.

{{< aside "CustomTkinter Documentation" >}}

📖 View the documentation [HERE](https://customtkinter.tomschimansky.com/documentation/)

{{< /aside >}}

**We use CustomTkinter to creates various [widgets](https://customtkinter.tomschimansky.com/documentation/widgets)** for the user to interact with and view information, this includes:
- text box
- buttons
- labels
- entry boxes

**`client.py` has a ton of code, you don't have to be too concerned with understanding each line.** Focus on reading the comments in the code to understand specific pieces. 

**The key piece to understand is the `__init__`, this is where the scren is setup and the the widgets are defined.** Here is an abreviated version with the setup and a menu button. 

```python {linenos=inline}
class RiddleGUI:
    def __init__(self):

        self.riddler_interface = RiddlerInterface()

        # Create and Setup the application window 
        self.app = customtkinter.CTk()
        self.app.geometry("600x400")
        self.app.title("Riddler Client")

        # Create menu buttons
        self.menu_view_all_button = customtkinter.CTkButton(
            self.app, 
            text="View All", 
            command=self.view_all_riddles, # method activated
            font=customtkinter.CTkFont(size=16)
        )

        # Place menu buttons on grid 
        self.menu_view_all_button.grid(row=0, column=0, padx=20, pady=20, sticky="ew")
```
- `line 4` - creates a `RiddlerInterface` subject which controls the HTTP requests
- `lines 7-9` - creates a CustomTinkter application
- `lines 12-17` - creates a button
- `line 20` - places the button the screen

---

## [3] RiddleInterface

Let's start by delving into how to use the Requests library. This will require you to remember the Riddle API. 


---

### Riddle API Refresher

🌐 **Visit [http://sycs.student.isf.edu.hk/riddle/all](http://sycs.student.isf.edu.hk/riddle/all) to view riddle server.**

💻 **As a reminder, you can make `GET` and `POST` requests to the API using the `httpie` tool in the Terminal**
```shell
http get http://sycs.student.isf.edu.hk/riddle/all
```

```shell
http post http://sycs.student.isf.edu.hk/riddle/guess id=1 guess="pickles" 
```

Here is a cheatsheet of the Riddle endpoints, what parameters they take in their payload, and what they do:

| Method | URL                                | Required Payload     | Action                                                                                   |
| ------ | ---------------------------------- | -------------------- | ---------------------------------------------------------------------------------------- |
| `GET`  | `/riddles/all`   |                      | Returns a list of all the riddles, without answers.                                      |
| `GET`  | `/riddles/one`   | `id`                 | Returns the riddle if it exists. (Otherwise, it returns an error with status code 404.)  |
| `GET`  | `/riddles/difficulty`   | `id`                 | Returns the riddle if it exists with its difficulty score. (Otherwise, it returns an error with status code 404.)  |
| `POST` | `/riddles/new`   | `question`, `answer` | Creates a new riddle (with an automatically-assigned id). Returns the riddle.            |
| `POST` | `/riddles/guess` | `id`, `guess`        | Checks whether the guess is correct. In the response, `correct` is `True` or `False`.    |

---

### requests_interface.py

The `RequestsInterface` class controls the `HTTP requests` to the [Riddle Server](http://sycs.student.isf.edu.hk/riddle/all). It uses the [Requests library](https://requests.readthedocs.io/en/latest/) to send `GET` and `POST` requests. 

It has two properties:

| Property      | Description                                     |
|---------------|-------------------------------------------------|
| **riddle_server** | stores the url of the riddle server             |
| **view**          | stores a View object for displaying information |

And the following methods:

| Method                          | Description                                                          |
|---------------------------------|----------------------------------------------------------------------|
| **view_all_riddles()**              | GETS all of the riddles and prints them as a bulleted list       |
| **guess_riddle(user_chosen_id, user_guess)** | GETS one riddle with the requested ID                            |


--- 

### `all_riddles()`

👀 **First let's look at the method`all_riddles()`** that sends an **HTTP GET** request to the Riddle server endpoint `riddles/all`.

```python {linenos=inline}
def all_riddles(self):
    '''This functions sends a GET request to riddles/all.'''

    all_riddles_address = self.riddle_server + 'all'

    response = requests.get(all_riddles_address)

    if response.status_code == 200:
        all_riddles_json = response.json()
        return all_riddles_json['riddles']

    else:     
        return f"HTTP error {response.status_code}"

```
- `line 4:` stores the full URL address of where to get all of the riddles. It uses the `riddle_server` property of the client class as the base address and adds the endpoint to the end of it.
- `line 6:` sends an HTTP GET request to the server and stores the response.
- `lines 8-10:` If the HTTP request was sucessful, it stores the JSON. Then, uses the `View` class to print the JSON is a nicely formatted bulleted list. 
  - `line 9:` converts the response from the server into JSON.
  - `line 10:` returns the list of all of the riddles in the database
- `line 12-13`: If the HTTP request was unsuccessful, return the error status code

---

### `guess_riddle()`

👀 **Now, let's look at the method`guess_riddle()`** that sends an **HTTP POST** request to the Riddle server endpoint `riddle/guess`.


```python {linenos=inline}
def guess_riddle(self, user_chosen_id, user_guess):
  '''This function sends a POST request to riddle/guess.'''

  guess_riddles_address = self.riddle_server + 'guess'

  payload = {
      'id': user_chosen_id,
      'guess': user_guess
  }

  response = requests.post(guess_riddles_address, json=payload)

  if response.status_code == 200:
      guess_riddle_json = response.json()

      if 'riddle' in guess_riddle_json:
          return guess_riddle_json['riddle'])

      else:
          return guess_riddle_json

  else:
      return f"HTTP error {response.status_code}"
```
- `line 4:` stores the full URL address of where to get one riddle.
- `lines 6-9:` stores the payload in a dictionary.
- `line 11:` sends an HTTP POST request with the payload to the server and stores the response.
- `lines 13-` Checks if the HTTP request was sucessful
  - `line 14` - get the json from the HTTP request
  - `line 16-17` - if riddle in JSON, return the riddle dictionary
  - `line 19-20` - returns error JSON
- `line 22-23`: If the HTTP request was unsuccessful, return the error status code

---

## [4] Extend the Client

### `View One Riddle`

Add the ability for the user to input a riddle id and view the specific information for the given riddle.

Edit requests_interface.py

Edit client.py

It should look like this

---

### `Add New Riddle`

Add the ability for the user to input a riddle question and answer, send a post request, and print the newly added riddle

Edit requests_interface.py

Edit client.py

It should look like this


---

### A few tips


🐞 **Debugging**
- Test, test, test! Make sure you are confident in each piece before moving on. 
- Use `print()` statements CONSTANTLY to give yourself more information 
- Copy and Paste are your best friends 

---

📚 **Parsing JSON**

The HTTP response is given to us in `JSON`.  

JSON is a standardized format to transfer data over a network. It represents data in a key/value pair, just like a Python dictionary.

**You can parse JSON, just as you would a [Python dictionary](https://realpython.com/iterate-through-dictionary-python/).**

💡 *What is in the `JSON` response if the guess is correct? If the guess is incorrect?*



---

## [5] Deliverables

{{< deliverables "Once you've successfully completed the client:" >}}  


{{< write-action >}} **Fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSe-mGrk41m6_-iZtqw5X1LpmYrfhF68Kbw8XJBCNv0XsqHG-Q/viewform?usp=sf_link)**

{{< code-action "Push your code to Github." >}}
- git status
- git add -A
- git status
- git commit -m "describe your code and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push

{{< /deliverables >}}


---

## [6] Extension

### Gamify!

👾 Currently, the client simply takes care of the HTTP requests in a nicely formatted view. But, **let's make it more fun and turn it into a game!**

{{< code-action "Extend the functionality of the client and allow the user to play a guessing game." >}}

The game should:
- display each riddle on the riddle server
- allow the user to guess each riddle

Gameplay should look something like this:
```shell
-----------------------------------
---- Welcome to the Riddler ----
-----------------------------------

[Riddler Game]
Question: Do you exist?
Enter your guess: no
Correct!

Question: What can fill a room but takes up no space?
Enter your guess: silence
Incorrect!

Question: What cups do not hold water?
Enter your guess:
```

🤔 **Even more extension feature ideas:**
- keep score of how many riddles the user guesses correctly
- display the current score after each riddle is guessed
- randomly display each riddle


---
