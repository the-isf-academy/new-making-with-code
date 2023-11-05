---
title: "5. Client"
type: lab
# draft: true
---

# Client

In this lab we will create a Client in the form of a Command Line Interface(CLI) for the Riddle server. We will use the `Requests` library to send and recieve HTTP requests.To learn more about the `Requests` library, checkout its [documentation](https://requests.readthedocs.io/en/latest/)


---


## [0] What is a client?


Since the riddle server is an API with no user interface, we end up writing a lot of
HTTP requests into the Terminal to use it. What if we had a program which took care
of making these requests for us? A program like this is called a *client*.

**Any app which uses the Internet is a client.**

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
-----------------------------------
---- Welcome to the Riddler ----
-----------------------------------

> View All Riddles                                                            
  View One Riddle                                                             
  Quit        
```

---
{{< code-action "Open code" >}}
```shell
code client.py
```

---

### [RiddleClient]

The `RiddleClient` has the following properties:

| Property      | Description                         |
|---------------|-------------------------------------|
| riddle_server | stores the url of the riddle server |
| menu_options  | stores a list of the menu options   |

And the following methods:

| Method                          | Description                                                          |
|---------------------------------|----------------------------------------------------------------------|
| menu()                          | allows user to pick a menu option and returns the option as a string |
| run()                         | runs the client and controls the logic of the client - all user input is taken here               |
| view_all_riddles()              | GETS all of the riddles and prints them as a bulleted list           |
| view_one_riddle(user_chosen_id) | GETS one riddle with the requested ID                                |




---

### [run()]

{{< look-action >}} **Let's start by taking a look at the method `run()`.** This method controls the logic of the client. It also is the only method in the client that takes user input.


```python {linenos=table}
def run(self):
        '''This function runs the client.'''

        print("-"*35)
        print("---- Welcome to the Riddler ----")
        print("-"*35,"\n")

        client_running = True

        while client_running == True:
            user_choice = self.menu()

            if user_choice == 'View All Riddles':
                print('[View All Riddles]')

                self.view_all_riddles()

            elif user_choice == 'View One Riddle':
                print('[View One Riddle]')

                user_chosen_id = input('Enter Riddle ID: ')
                self.view_one_riddle(user_chosen_id)


            elif user_choice == 'Quit':
                client_running = False

                print("="*75)

            print()
```

- `lines 4-6:` prints a starting message to the user
- `line 8:` `client_running` is the variable that keeps track if the user is still using the client
- `line 11:` stores the user's choice when they select a menu option
-  `lines 13, 18, 25:` control the logic for each menu option


---


### [view_all_riddles()]

{{< look-action >}} **Now let's look at the working method `view_all_riddles()`.** This method sends an HTTP GET request to the Riddle server endpoint `riddles/all` and prints all of the riddles in a bulleted list.

```python {linenos=table}
def view_all_riddles(self):
        '''This functions sends a GET request to riddles/all.
        It gets all of the riddles and nicely formats them into a bulleted list.'''

        all_riddles_address = self.riddle_server + 'riddles/all'

        response = requests.get(all_riddles_address)

        if response.status_code == 200:
            all_riddles_json = response.json()

            for riddle in all_riddles_json['riddles']:
                print("  • {} (#{})".format(riddle['question'], riddle['id']))
        else:
            error_json = response.json()
            print('Server {} Error. Try again...'.format(response.status_code))
            print('-- {}'.format(error_json['errors'][0]))
```
- `line 5:` stores the full URL address of where to get all of the riddles. It uses the `riddle_server` property of the client class as the base address and adds the endpoint to the end of it.
- `line 7:` sends an HTTP GET request to the server and stores the response.
- `lines 9-13:` If the HTTP request was sucessful, it prints each riddle one at a time in a nicely formatted bulleted list.
  - `line 10:` converts the response from the server into JSON.
- `line 14-17`: If the HTTP request was unsuccessful, it prints the error status code and the error message.

---

### [view_one_riddle()]

{{< look-action >}} **Finally take a look at the method `view_one_riddle()`.** This method sends an HTTP GET request to the Riddle server endpoint `riddles/one` and print a single riddle with the requested ID.

```python {linenos=table}
def view_one_riddle(self, user_chosen_id):
        '''This function sends a GET request to riddles/one.
        It gets a single riddle with a specific ID and then formats it in a nice list.'''

        one_riddles_address = self.riddle_server + 'riddles/one'

        one_riddle_payload = {
            'id': user_chosen_id
        }

        response = requests.get(one_riddles_address, json=one_riddle_payload)

        if response.status_code == 200:
            one_riddle_json = response.json()

            for key, value in one_riddle_json.items():
                print("  • {}: {}".format(key,value))

        else:
            error_json = response.json()
            print('Server {} Error. Try again...'.format(response.status_code))
            print('-- {}'.format(error_json['errors'][0]))
```
- `line 5:` stores the full URL address of where to get one riddle.
- `lines 7-9:` stores the payload in a dictionary.
- `line 11:` sends an HTTP GET request with the payload to the server and stores the response.
- `lines 13-17:` If the HTTP request was sucessful, it prints a single riddle with each of its properties in a bulleted list.
  - `line 14:` converts the response from the server into JSON.
- `line 19-22`: If the HTTP request was unsuccessful, it prints the error status code and the error message.

---

## [3] Extend the Client

**Your job is to add 2 functionalites to the `RiddleClient.py`.** This will require you to edit a property, edit a method, and add methods to `RiddleClient`.
- `new riddle` - should allow the user to input a riddle question and answer, send a post request, and print the newly added riddle
- `guess riddle` - should allow the user to guess a specific riddle, send a post request, and print a message telling the user is their guess was correct or incorrect

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
```


{{< expand "Hint: Parsing JSON" >}}

When we guess a riddle, the response is given to us in `JSON`.  

JSON is a standardized format to transfer data over a network. It represents data in a key/value pair, just like a Python dictionary.

**You can parse JSON, just as you would a Python dictionary.**

💡 *What is in the `JSON` response if the guess is correct? If the guess is incorrect?*
{{< /expand >}}





---

## [4] Deliverables

{{< deliverables "Once you've successfully completed the client:" >}}  


{{< write-action >}} **Fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSedWRG5sYR_HfmgT7-uguhNNF27QK0Nh6jKv_tYR-UGimJqvA/viewform?usp=sf_link)**

{{< code-action "Push your code to Github." >}}

{{< /deliverables >}}


---

## [5] Extension



### [Gamify]

Currently, the client simply takes care of the HTTP requests in a nicely formatted view. But, let's make it more fun and turn it into a game!

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

Potential further extension features:
- keep score of how many riddles the user guesses correctly
- display the current score after each riddle is guessed
- randomly display each riddle

---

### [Magic 8]

In this extension 