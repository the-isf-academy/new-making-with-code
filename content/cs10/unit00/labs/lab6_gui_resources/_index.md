---
title: "7. GUI Game"
type: lab
# draft: true
---

# GUI Game

In this lab we create a guessing game with a Grapical User Interface (GUI) using the
CustomTkinter Library. 

{{< aside "CustomTkinter Documentation" >}}

📖 View the documentation [HERE](https://customtkinter.tomschimansky.com/documentation/)

{{< /aside >}}

---

## [1] Set Up

We will use the repo from the previous lab, `lab_gui_game`. 

{{< code-action "Go to the lab folder." >}}
```shell
cd ~/desktop/making_with_code/unit03_networking/lab_gui_game_YOURGITHUBUSERNAME
```

{{< code-action "Enter the poetry shell." >}} You do NOT need to install the requirements again. 
```shell
poetry shell
```

📄 **The repository has the following files.**  In this lab we will just focus on the bolded files.
- `riddle_client.py`
- `test_riddle_client.py`
- **`gui_template.py`**
- **`gui_view_game.py`**

{{< code-action "Open the folder in VS Code:" >}} `code .`


---

## [2] Play the game! 

**💻 Play the game!** `python gui_view_game.py`.

{{< figure src="images/courses/cs10/unit00/07_gui_1.png" width="75%"  >}}


---

## [3] Improve the Game

**💻 Add the following features to the game**

&nbsp;&nbsp;&nbsp;**[✔️]** randomize the order of the riddles each time

&nbsp;&nbsp;&nbsp;**[✔️]**  add a score feature

&nbsp;&nbsp;&nbsp;**[✔️]** add lives feature (e.g. 3 guesses until game over)

&nbsp;&nbsp;&nbsp;**[✔️]** add game over screen

&nbsp;&nbsp;&nbsp;**[✔️]** add difficulty feature 


{{< expand "Hint" >}}

- look into the `shuffle()` function
- what properties will you need to add to track the `score` and `lives`?
- how will you know if the game is over? 

{{< /expand >}}


---

## [4] Deliverables

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

## [6] Extension

### Customize the look!

💻 **Explore the [documentation](https://customtkinter.tomschimansky.com/documentation/) and customize the appearnce of your app.**
- experiment with using a [combo box](https://customtkinter.tomschimansky.com/documentation/widgets/combobox) to select the difficulty


💻 **Add a high score leaderboard feature.** You will need to learn how to [read and write to a file](https://www.geeksforgeeks.org/reading-writing-text-files-python/).