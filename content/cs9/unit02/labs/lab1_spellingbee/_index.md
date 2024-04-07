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

## [1] Setup

{{< code-action "Start by going into your" >}} `unit02_games` **folder.**
```shell
cd ~/desktop/making_with_code/unit02_games
```

{{< code-action "Clone your starter code." >}} Be sure to change `YOUR-GITHUB-USERNAME` to your actual Github username.
```shell
git clone https://github.com/the-isf-academy/lab_spellingbee_YOUR-GITHUB-USERNAME
```


{{< code-action "Enter the Poetry shell and install the requirements:" >}}
```shell
poetry shell
poetry install
```


{{< code-action "cd into the lab" >}}
```shell
cd lab_spellingbee_YOUR-GITHUB-USERNAME
```

This lab includes the following files to play the Spelling Bee game:
- `model.py`
- `game.py`
- `view.py`
- `wordslist.py`
- `helpers.py`

---

## [2] Fixing the View 

In this version of Spelling Bee, the game is separated into 3 distinct layers:
- game structure (`model.py`)
- game logic (`game.py`)
- game output (`view.py`)

{{< figure src="images/courses/cs9/unit02/01_spellingbee.png" width="100%" >}}

Most of the game structure and the game logic are complete. **You will start by customizing the game output.**

---

### Play the Game

{{< code-action "Let's start by playing the game." >}} 

```shell
python game.py
```

It runs like so:
```shell 
---Welcome to Spelling Bee---

[RULES]
You can use any of these letters: ['T', 'C', 'O', 'L', 'I', 'N', 'M']
You must you use the letter M
Guesses must be more than 3 letters long

---mystery message 0---
 > lion

  -mystery message 3-  

---mystery message 0---
 > mom

  -mystery message 1-
```

**🤔 It works perfectly, but the messages are confusing!**

---

### Solving the Mysteries

**In `view.py`, we have the `TerminalView` class, which is purely responsible for input and output to the user.** In this case, it gets the guess from the user and gives them messages. It does not affect the game flow or logic. 

{{< code-action >}} **Edit each method in the `TerminalView()` class so that the messages are more clear for the user.** 

{{< code-action >}} **Play test your and make sure it works bug free!** 

👾 **Play test your partner's game and see how they implemented their `TerminalView()`!** 

## [3] Duplicate Guesses

**Right now, the user doesn't get an error message if they guess the same word multiple times.** We are keeping track of all their correct guesses in a list called `guessed_words`, but we aren't using it to give them an error message.

### Changing the Model
{{< code-action >}} **In `model.py`, add a new method called `check_if_repeat()` that checks whether if it is a repeated guess. It should return True if it's a repeat or False if not.** Hint: it will be similar to the method `check_wordlist()`.

### Changing the View
{{< code-action >}} **In `view.py`, add a new method called `repeat_guess()` that gives the user a message letting them know they've guessed that word before.** 

### Changing the game
{{< code-action >}} **In `game.py`, add a new elif statement that checks whether the user has guessed this word already, and then gives them the correct error message.** Make sure you're using the two methods you just created in your `model` and `view`!

## [4] Score 

**In the original Spelling Bee, you get points when you guess correct words.** To make this work, we will have to make changes in each of our three main files: `models.py`, `game.py`, and `view.py`.

### Changing the Model

{{< code-action >}} **In `model.py`, add a property called `score` into the `SpellingBee()` class.** What do you think a good starting value is for the user's score?

{{< code-action >}} **In `model.py` change the method `correct_word()` so that it increases the user's score by 1.** 

{{< code-action >}} **Test if your changes worked!** In game.py add a print statement that prints out the score, and try running your code. Does the score increase as you expect?

### Changing the View
**When the user guesses correctly, we should let them know what their score is!** We can't just print it out in `game.py`, because we want to keep all our user messages in the `TerminalView` class. However, the `TerminalView` class doesn't know what the score currently is. We need to pass that information using a parameter.

{{< code-action >}} **In `view.py` change the method `correct()` so that it expects a parameter called `current_score`. You can use this parameter to print out the user's score as part of their success message!** Remember, a parameter goes in the brackets. 

**Now, whenever you use the `correct()` method, you will need to include the current score as a parameter**

{{< code-action >}} **In `game.py`, change the call to the `correct()` method to include the `score` parameter.** Remember that the score is a property of your `spelling_bee` object.

👾 **Test our your game to see how the new feature works!** 

## [5] Deliverables

{{< deliverables  >}}

**Once you've successfully completed the game be sure to fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSczCgC8Y3nJeqDh30MVe7O-WXqEkoL17fc00ZBWQw-djTwcig/viewform?usp=sf_link)**.


{{< code-action "Push your work to Github:" >}}
- git status
- git add -A
- git status
- git commit -m "describe your drawing and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push

{{< /deliverables >}}


---

## [6] Extension: Menu


Currently, this game does not have a menu system. **It's up to you to implement one!**


{{< code-action >}} **Implement the `menu` from `helpers.py` into `game.py`.** A user should be able to:

- make a guess
- view the rules 
- view their previous successful guesses
- quit the game

> *Hint: take a look at the `game_interface.py` and `helpers.py`the Pet lab. What will you need to copy?*

---

### [Multiple difficulty levels]

Every time you play the game, it's exactly the same. 

{{< code-action >}} **Incorporate at least 2 `SpellingBee()` objects that the user can choose from.** 







