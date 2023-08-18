---
title: 2. Spelling Bee
# draft: true
---

# Spelling Bee

In this lab, you will learn about the different layers that make up a game.

---

## [0] Play the Game



👾 **Let's start by playing Spelling Bee: [https://www.nytimes.com/puzzles/spelling-bee](https://www.nytimes.com/puzzles/spelling-bee).**

{{< checkpoint >}}

✏️ **As you play, complete the worksheet with your partner.** 

Consider, how would you build this game in Python?

{{< /checkpoint >}}

---

## [0] Setup

{{< code-action "Start by going into your" >}} `cs9/unit02_games` **folder.**
```shell
cd ~/desktop/making_with_code/cs9/unit02_games
```

{{< code-action "Clone your starter code." >}} Be sure to change `YOUR-GITHUB-USERNAME` to your actual Github username.
```shell
git clone https://github.com/the-isf-academy/lab_spellingbee_yourgithubusername
```


{{< code-action "Enter the Poetry shell and install the requirements:" >}}
```shell
poetry shell
poetry install
```

This lab includes the following files to play the Spelling Bee game:
- `spellingbee.py`
- `game.py`
- `view.py`

---

## [1] Fixing the View 

In this version of Spelling Bee, the game is separated into 3 distinct layers:
- game structure (`spellingbee.py`)
- game logic (`game.py`)
- game output (`view.py`)

{{< figure src="images/courses/cs9/unit02/00_spellingbee.png" width="100%" >}}

In this lab, the game structure and the game logic are complete. **It is up to you to up to you to customize the game output.**

---

### [Play the Game]

{{< code-action "Let's start by playing the game." >}} 

```shell
python3 game.py
```

It runs like so:
```shell 
---Welcome to Spelling Bee---

[RULES]
You can use any of these letters: ['T', 'C', 'O', 'L', 'I', 'N', 'M']
You must you use the letter M

---Mystery Method 2---
 > 

---Mystery Method 6---

---Mystery Method 2---
 > 
```

**🤔 It works perfectly, but the messages are a mystery!**

---

### [Solving the Mysteries]

**The `View` class is purely responsible for the output and communication of what is happening in the game with the user.** It does not affect the game flow or logic. 

The `View` is unique in that it only has methods and has no properties. It's methods are only responsible for printing information and getting user input. 

✔️ **It's up to you to solve the mystery methods and fix the `View()`!** This will require you to understand the logic of the game in `game.py`. 

{{< code-action >}} **Edit each `mystery_method` in the `View()` class so the messages accurately communicate to the user what is happening the game.** 

{{< code-action >}} **Make the code more readable by renaming all of the `mystery_methods` in the `View()`.** 
> *Once you change the name of a method in the `View()`, you will also need to change it in `game.py`*

{{< code-action >}} **Play test your and make sure it works bug free!** 

👾 **Play test your partner's game and see how they implemented their `View()`!** 


## [3] Deliverables


{{< deliverables  >}}

**Once you've successfully completed the game be sure to fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLScul5QUTuRN2MQUlX2rwvpCnxARWolbrP3R045kwjUsNXuN3g/viewform?usp=sf_link)**.


{{< code-action "Push your work to Github:" >}}
- git status
- git add -A
- git status
- git commit -m "describe your drawing and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push

{{< /deliverables >}}


---

## [3] Extension: Menu


Currently, this game does not have a menu system. **It's up to you to implement one!**


{{< code-action >}} **Implement the [`simple-term-menu`](https://pypi.org/project/simple-term-menu/) into `game.py`.** A user should be able to:

- make a guess
- view the rules 
- view their previous successful guesses
- quit the game

> *Hint: take a look at the `game_interface.py` and `helpers.py`the Pet lab. What will you need to copy?*

---

### [Multiple difficulty levels]

Every time you play the game, it's exactly the same. 

{{< code-action >}} **Incorporate at least 2 `SpellingBee()` objects that the user can choose from.** 







