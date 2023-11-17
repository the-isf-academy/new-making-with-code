---
title: "6. Cards"
type: lab
# draft: true
---

# Cards

In this lab we will create a Client in the form of a Command Line Interface(CLI) for the Deck of Cards API. We will use the `Requests` library to send and recieve HTTP requests. To learn more about the `Requests` library, checkout its [documentation](https://requests.readthedocs.io/en/latest/).


---


## [0] Deck of Cards API

The API that we will use for today is called the Deck of Cards API. It is free, simple, and easy-to-use. Here is a link to the [API Documentation](https://www.deckofcardsapi.com/). You will need to reference this in today's lab.

---

## [1] Set Up


{{< code-action "Go to the unit folder, clone the cards lab, and cd into the repo." >}}
```shell
cd ~/desktop/making_with_code/cs10/unit00_networking/
git clone https://github.com/the-isf-academy/lab_cards_YOURGITHUBUSERNAME
cd lab_cards_YOURGITHUBUSERNAME
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

## [2] Improve the Views

Even though `client.py` and `requests_interface.py` are fully filled in and working, the game isn't very aesthetically pleasing. And you can't even see what cards you have! Let's improve `views.py` so that the user experience is better.

{{< code-action "Try the client" >}}
```shell
python client.py
```

```shell
Menu:
> Start New Deck                                                         
  Deal a Card
  View Cards
  Reset Deck                                                         
  Quit        
```

It's pretty boring. There's no welcome message, and it doesn't tell you what's happening. You can't even see your cards!


{{< code-action "Open up the code" >}}
```shell
code .
```


---

### Welcome Message

The first thing we need is a welcome message! You might design in the style of our previous labs like this:

```shell
-----------------------------------
---- Cards ----
-----------------------------------       
```
or you can design your own.

💻 **Add a welcome method to the `View` class, and call it in `client.py`**

---

### Quit Message

Add a message for when the game ends

```shell
-----------------------------------
---- Goodbye ----
-----------------------------------
       
```

💻 **Add a quit method to the `View` class, and call it in `client.py`**

---
### View Cards

Last but not least, a user needs to be able to see their cards.

```shell
Menu: View Cards
9 ♥
4 ♠
A ♦
J ♣️
```

💻 **Add a method for viewing your cards to the `View` class, and call it in `client.py`**

---

## [3] Error Handling

### No Deck

You might notice right now that if you attempt to deal, view, or reset before you start a deck, you get an error:

```shell
TypeError: can only concatenate str (not "NoneType") to str
```

This is because you haven't made a deck yet!

👀 **Look at the constructor of the `RequestsInterface` class below:**

```python {linenos=inline, hl_lines=9,linenostart=9}
def __init__(self):
    self.deckofcards_url = 'https://www.deckofcardsapi.com/api/deck/' # the base url for the cards api

    self.view = View()

    # deck_id is initalized in get_new_deck()
        # you may want to hard code it during testing 
        # you can hard code it by finding a valid deck_id by printing the deck_json under line 27
    self.deck_id = None  
```

Notice how `self.deck_id` starts as `None`, because it hasn't been created yet. You need to add error handling to the client that checks whether the `deck_id` is `None``, and if it is, let the user know that they should make a deck first.

💻 **Add an error message method in `views.py` telling the user to make a deck first.**
<br>

💻 **Add error handling to `client.py` to trigger this message.**

---

## [4] Deliverables

{{< deliverables "Once you've successfully fixed the client" >}}  

{{< code-action "Push your code to Github." >}}
- git status
- git add -A
- git status
- git commit -m "describe your code and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push

{{< /deliverables >}}


---


## [5] Extension - Improve the Client

The Deck of Cards API has so many features! Choose one of the options below to add to the existing client:

### Draw multiple cards at a time

Right now you can only ever deal one card at a time

💻 **Add a new menu item that allows you to draw any number of cards.** 

---

### Multiplayer

Right now, there is just one player with cards, but the API allows you to add as many as you want.

💻 **Add in multiple players** 

Remember, you'll need to **deal** to multiple players, and also to **view** multiple different players!

---

### Discard Pile

Create a new pile, and let the player discard to it!

💻 **Add a new menu item that allows you to discard to the discard pile.** 

---

### Fix the 500 Error

Right now, if you try to view your cards before you have any, you get a 500 error

```shell
[Error: HTTP 500]
```
💻 **Add in error handling so that the 500 error doesn't happen.**





