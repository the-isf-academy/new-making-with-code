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

{{< code-action "Try the client:" >}}
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

---
{{< code-action "Open code" >}}
```shell
code view.py
```

`views.py` controls the aesthetics and user interactions. Right now, all it has is a menu and error messaging. 

---

### Welcome Message

The first thing we need is a welcome message! You might design in the style of our previous labs like this:

```shell
-----------------------------------
---- Cards ----
-----------------------------------       
```
or you can design your own.

{{< code-action "Add a welcome method to the `View` class, and call it in `client.py`" >}}

---

### Quit Message

Add a message for when the game ends

{{< code-action "Add a quit method to the `View` class, and call it in `client.py`" >}}

---
### View Cards

Last but not least, a user needs to be able to see their cards.

{{< code-action "Add a method for viewing your cards to the `View` class, and call it in `client.py`" >}}

## [3] Deliverables

{{< deliverables "Once you've successfully completed the client:" >}}  

{{< code-action "Push your code to Github." >}}
- git status
- git add -A
- git status
- git commit -m "describe your code and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push

{{< /deliverables >}}


---


## [4] Extension - Extend the Client

💻 **Add more funtions to `client.py`.** 

Explore the documentation for the Cards API and add more features! You could add a second player, a discard pile, etc. 

If you're up for the challenge, you can try coding blackjack!


