---
title: "5. Client"
type: lab
# draft: true
---

# Client

In this lab we will create a Client in the form of a Command Line Interface(CLI) for the Riddle server. We will use the `Requests` library to send and recieve HTTP requests. To learn more about the `Requests` library, checkout its [documentation](https://requests.readthedocs.io/en/latest/).


---


## [0] What is a client?


Since the riddle server is an API with no user interface, we end up writing a lot of
HTTP requests into the Terminal to use it. What if we had a program which took care
of making these requests for us? A program like this is called a *client*.

**Any app which uses the Internet is a client.**

{{< figure src=https://res.cloudinary.com/lwgatsby/f_auto/www/uploads/2023/05/client-server-network.jpg" width="50%">}}


The client, or app, is constantly making HTTP requests
to a server to send and receive information.

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

📄 **The repository has the following files:** 
- `client.py`
- `requests_interface.py`
- `view.py`


---

## [2] Try the Client

We are going to create a Terminal interface for the riddler server. This will allow users to easily interact with the server without needing to explicitly make a `GET` or `POST` request.

{{< code-action "Try the client for the Riddle Server:" >}}
```shell
python client.py
```

```shell
Menu:
> View All Riddles                                                            
  Guess Riddle                                                           
  Quit        
```

---
{{< code-action "Open code" >}}
```shell
code client.py
```

---

### client.py

`client.py` is the main loop that triggers all the other code to be run. It imports the `RequestInterface` and the `View` and uses them to make everything happen.

```python {linenos=inline}
from requests_interface import RequestsInterface
from view import View

client_running = True
requests_interface = RequestsInterface()
view = View()

while client_running == True:

    user_choice = view.menu(
        prompt = "Menu:",
        options = [
                'View All Riddles',
                'Guess Riddle',
                'Quit']
                )

    if user_choice == 'View All Riddles':
        requests_interface.all_riddles()

    elif user_choice == 'Guess Riddle':
        user_chosen_id =  view.get_input('Enter Riddle ID')
        user_guess=  view.get_input('Enter guess')

        requests_interface.guess_riddle(user_chosen_id, user_guess)


    elif user_choice == 'Quit':
        client_running = False
        view.quit()
```

- `line 4:` `client_running` is the variable that keeps track if the user is still using the client
- `line 10:` `user_choice` stores the user's choice when they select a menu option
-  `lines 18, 21, 26:` control the logic for each menu option

---

### requests_interface.py

The `RequestsInterface` class controls the `HTTP requests` to the [Riddle Server](http://sycs.student.isf.edu.hk/riddles/all). It uses the [Requests library](https://requests.readthedocs.io/en/latest/) to send `GET` and `POST` requests. 

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
| **error_json(response_json)**       | used when the response json **contains** an error messaged       |
| **error_no_json(response)**         | used when the response json **doesn't contain** an error message |

---

### views.py

The `View` class simply controls the communication of information to the user. It has no methods and the following properties:
- `menu()`
- `get_input(prompt)`
- `welcome()`
- `all_riddles(all_riddles)`
- `guess_riddle(guess_riddle_json)`
- `error_json(error_message)`
- `error_no_json(status_code)`
- `quit()`


---

## [3] RiddleInterface

Let's start by delving into how to use the Requests library. This will require you to remember  the Riddle API. 


---

### Riddle API Refresher

🌐 **Visit [http://sycs.student.isf.edu.hk/riddles/all](http://sycs.student.isf.edu.hk/riddles/all) to view riddle server.**

💻 **As a reminder, you can make `GET` and `POST` requests to the API using the `httpie` tool in the Terminal**
```shell
http get http://sycs.student.isf.edu.hk/riddles/all
```

```shell
http post http://sycs.student.isf.edu.hk/riddles/guess id=1 guess="pickles" 
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

### `all_riddles()`

👀 **First let's look at the method`all_riddles()`** that sends an **HTTP GET** request to the Riddle server endpoint `riddles/all`.

```python {linenos=inline}
def all_riddles(self):
  '''This functions sends a GET request to riddles/all.'''

  all_riddles_address = self.riddle_server + 'all'

  response = requests.get(all_riddles_address)

  if response.status_code == 200:
      all_riddles_json = response.json()
      self.view.all_riddles(all_riddles_json['riddles'])

  else:       
      self.error(response)
```
- `line 4:` stores the full URL address of where to get all of the riddles. It uses the `riddle_server` property of the client class as the base address and adds the endpoint to the end of it.
- `line 6:` sends an HTTP GET request to the server and stores the response.
- `lines 8-10:` If the HTTP request was sucessful, it stores the JSON. Then, uses the `View` class to print the JSON is a nicely formatted bulleted list. 
  - `line 9:` converts the response from the server into JSON.
- `line 12-13`: If the HTTP request was unsuccessful, it processses the error. 

---

### `guess_riddle()`

👀 **Now, let's look at the method`guess_riddle()`** that sends an **HTTP POST** request to the Riddle server endpoint `riddles/guess`.


```python {linenos=inline}
def guess_riddle(self, user_chosen_id, user_guess):
  '''This function sends a POST request to riddles/guess.'''

  guess_riddles_address = self.riddle_server + 'guess'

  payload = {
      'id': user_chosen_id,
      'guess': user_guess
  }

  response = requests.post(guess_riddles_address, json=payload)

  if response.status_code == 200:
      guess_riddle_json = response.json()

      if 'error' not in guess_riddle_json:
          self.view.guess_riddle(guess_riddle_json['riddle'])

      else:
          self.error_json(guess_riddle_json)

  else:
      self.error_no_json(response)
```
- `line 4:` stores the full URL address of where to get one riddle.
- `lines 6-9:` stores the payload in a dictionary.
- `line 11:` sends an HTTP POST request with the payload to the server and stores the response.
- `lines 13-20:` If the HTTP request was sucessful, it checks if there was an error then uses the `View` class to communicate to the user if the guess was correct or incorrect.
  - `line 16` checks if there was a user error (like a non-existing Riddle id)
- `line 19-22`: If the HTTP request was unsuccessful, it prints the error status code and the error message.

---

## [4] Extend the Client

💻 **Your job is to add 2 functionalites to the `RiddleClient.py`.** 
- `View One Riddle` - allows the user to input a riddle id and view the specific information for the given riddle
- `Add New Riddle` - allows the user to input a riddle question and answer, send a post request, and print the newly added riddle


📄 **For each new functionality, you will need to edit:**
- `client.py`
- `requests_interface.py`
- `view.py`




{{< aside "A Few Tips... " >}}

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
{{< /aside >}}


✔️ **When completed your client will have each option fully working and look something like this:**
```shell
Menu:
> View All Riddles   
  View One Riddle                                                         
  Guess Riddle   
  Add New Riddle                                                        
  Quit        
```

<!-- 
---

### [new riddle]

This will require you to edit:
- `menu`
- `run()`



Write a method `new_riddle()`:
- take two parameters: `user_question` and `user_answer`
- send an HTTP POST request with the user's question and answer to the server's endpoint `riddles/new`
- print the newly added riddle

{{< look-action >}} **Take a look at the pseudocode for this funcitonality.**

```
0) edit the `menu` property
1) edit the `run()` method
  - add a conditional statement 
  - print a header to tell the user which menu option they are in 
  - store the user input for the riddle question and answer
  - call the `new_riddle()` method with the stored user input as parameters
2) write the `new_riddle()` method
  - store the new riddle server address
  - store the payload in a dictionary
  - make the http post request and store the response
  - if the response was successful
    - convert the response to JSON
    - print the newly added riddle in a nice format
  - else if the response was incorrect, tell the user
```

{{< code-action "Translate the pseudocode into Python code to implement the new riddle functionality into the client." >}} The client interaction should look something like this:
```shell
[New Riddle]
Enter a Riddle question: What kind of room has no doors or windows?
Enter the answer: A mushroom
Riddle Successfully Added!
  • answer: A mushroom
  • correct: 0
  • guesses: 0
  • id: 37
  • question: What kind of room has no doors or windows?
```

---

### [guess riddle]

This will require you to edit:
- `menu`
- `run()`


Write a method `guess_riddle()`:
- take two parameters: `user_chosen_id` and `user_guess`
- send an HTTP POST request with the user's guess and corresponding riddle id to the server
- print if the guess was correct or incorrect.

{{< write-action "Write pseudocode for" >}} `guess_riddle()` keeping the following in mind:
- Do you need anything from the user?
- What endpoint do you need?
- Does the endpoint require a payload?
- How do you nicely format a dictionary to print to the user?

{{< code-action "Code this functionality to allow the user to guess a riddle." >}} Reference your pseudocode to consider how to implement guessing a riddle. Be sure to look at the existing code for a starting off point.  

**The client interaction should look something like this:**
```shell
[Guess a Riddle]
Enter Riddle ID: 10
  • correct: 0
  • guesses: 2
  • id: 10
  • question: What is born with 4 legs, loses 2 legs, and has 3 before it dies?

Enter your guess: Dragon  
Incorrect!
``` -->





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

### Improved CLI!

How could you improve your CLI (command line interface) to make it more user-friendly? 

📖 **Explore the [`InquiererPy` documentaiton](https://inquirerpy.readthedocs.io/en/latest/index.html) and see what's possible with the menu package**

💻 **Improve your CLI**, here are a few ideas: 
- allow user to select a riddle from a list to see its details 
- allow a user to select a riddle, guess it 
- allow user to select multiple riddles to create their own custom guessing game

---

### GUI 

CLIs are great for low-weight applications, but if you wanted a GUI (graphical user interface)? 

💻 **Experiment with Python's built in GUI package [tkinter](https://realpython.com/python-gui-tkinter/)** 


<!-- ---

### [Magic 8]

In this extension  -->
