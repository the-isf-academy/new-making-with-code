---
Title: Project
# draft: true
---

# Unit 02 Games Story Project

🎨 **Design Prompt:** You will create a text-based game inspired by a real piece of media or your own life. 

{{< code-action >}} **Your game must include one unique feature.** For example:
- variable messaging in the story associated with user actions
    - *e.g. "you have visited this store 5 times"*
- branches that come back together into the same Node
- Nodes that can go back to a previous Node
- a Player() class with unique properties
    - *e.g. hunger, money, or health*
- add to Node() and/or Story() to gives items
    - *e.g. a locked door where you need to first collect the key in a certain room.*


It is totally up to you what type of story you make. For example you could make:
- choose your own adventure game 
- exploration game
- puzzle game 
- narrative story game



{{< figure src="https://steamuserimages-a.akamaihd.net/ugc/1791848543425884907/18A8A93A2B7215E654F50350F4C896FFE463B456/" width="70%" >}}
> [*Zork*](https://en.wikipedia.org/wiki/Zork) is often noted as one of the best video games of all time. 
>
>*"What Zork seemed to contribute more than anything was the idea that the computer could simulate a rich virtual environment" - [Matt Barton](https://web.archive.org/web/20220809014122/https://www.gamedeveloper.com/pc/the-history-of-zork)*



---

## [0] Planning Document

This is a big project with a lot of room for customization. You will need to:
- outline your story in a graph diagram 
- plan the implementation of an additional feature 

It is important for you to plan the game prior to coding. 

{{< write-action "Plan your game prior to coding in your Google Doc:" >}} Unit 02: Games  - Story Project Planning Document. Check with a teacher before moving on to the code.

Some idea for features:
- player health
- adding enemies
- 

---


##  [1] Set Up

{{< code-action "Start by going into your" >}} `cs9/unit02_games` **folder.**
```shell
cd ~/desktop/making_with_code/cs9/unit02_games
```

{{< code-action "Clone your starter code." >}} Be sure to change `yourgithubusername` to your actual Github username.
```shell
git clone https://github.com/the-isf-academy/project_game_story_yourgithubusername
```

{{< code-action "Enter the Poetry shell and install the requirements:" >}}
```shell
poetry shell
poetry install
```

This repo includes the following files:
 - `game.py` when this program runs, it should launch your game
- `view.py`
- `story_setup.py`
- `story.py`
- `node.py`
- `README.md` - a brief description of your game


---
## [2] Assessment


✅  **This project will be assessed on the following criteria:**
- **Planning [3]** 
    - I can consider the components of my game before coding
    - I can create a graph diagram to outline the branches of my story
    - I can plan how to implement a new feature  
- **Iterative Development [3]**
    - I can track the development of my project by successfully committing to Github a minimum of each class work day, preferably after each work session
    - I can write descriptive commit messages that accurately describe the changes made
    - I can systematically break down my project into smaller chunks  
- **Readability [3]**
    - I can write easily understandable code (another CS student could understand it)
    - I can use descriptive names for modules, variables, classes, and methods
    - I can write descriptive comments to describe complex pieces of the code
    - I included a short description of my game in `README.md`
- **Feature Implementation [3]**
    - I can edit or add the necessary class(es) with appropriate properties and/or methods
    - I can add a feature that is well abstracted
        - could be used in multiple situations 
        - could be easily adapted by another CS student
- **Game Implementation [3]**
    - I can properly implement my graph diagram
    - I can design a `View` that is easily to read and understand 


**For each criteria you will be assessed on a score from 0-3. With 5 criteria, there is a total of 15 potential points.** 
- 0 - no evidence of the practice
- 1 - limited evidence of the practice
- 2 - adequate evidence of the practice
- 3 - substantial evidence of the practice

{{< expand "Scoring Breakdown" >}}

The project is scored out of 15. 

*To calculate your score for the practices & concepts, look at the following bands:*

- 1 = 0
- 2 = 1
- 3 = 2-3
- 4 = 4-6
- 5 = 7-11
- 6 = 12-13
- 7 = 14-15
{{< /expand >}}


---

## [3] Deliverables

{{< deliverables  "Projects are due on Wednesday, 02 March." >}}

- A `Unit 02 Games Project: Planning Document` 
- A `project-game-story` repository will include some if not all the following files:
    - `game.py` 
    - `view.py`
    - `story_setup.py`
    - `story.py`
    - `node.py`
    - `README.md` - a brief description of your game


---

**🗓️ Timeline**

**You have 5 in class days to complete this project.**

- begins on Monday, 24 April 
- due on Monday, 08 May 

---

{{< code-action "Push your work to Github:" >}}
- `git status`
- `git add game.py`
    - you can add all of the changed files with: `git add -A`
- `git status`
- `git commit -m "your message goes here"`
    - be sure to customize this message, do not copy and paste this line
- `git push`
{{< /deliverables >}}

---

## [4] Resources


👾 **If you need inspiration, explore these narrative games.** As you play, consider the different genres and what's possible with this structure. 
- [Harry Potter - Sorting Hat](https://unfold.studio/stories/303/)
- [Oregon Trail 1971](https://unfold.studio/stories/10782/)
- [City Exploration](https://unfold.studio/stories/2649/)
- [Store front Example, variables](https://unfold.studio/stories/1065/)

---

✏️ **AI Tools.** If you need help writing the text, feel free to use an AI service. Just be sure to cite your transcript in the Planning Doc.
- [poe](https://poe.com/)
- [rytr](https://rytr.me/)
- [composeai](https://www.compose.ai/#:~:text=Compose%20AI%20is%20a%20free,some%20of%20our%20personalization%20features.)

---

👀 **Readability.** Here are a few resources that may help improve readability.
- [Emojis](https://www.emojicopy.com/)
- [InquirerPy](https://inquirerpy.readthedocs.io/en/latest/)
    - This is the package that controls the menu

---

🔉 **Play Sound.** If you are interested in including sounds in your game, follow along with these steps.

(0) **Install the playsound library:** `pip3 install playsound`

(1) **Add a sound file to your repository.** *e.g. .mp3, .m4a, .wav file.*
> If will have multiple sounds, be sure to consider how you will organize your repostiory.

(2) **Incorporate the sound into your game.** If this is your feature, I highly planning how you will incorporate this into the `Node()`, `Story()` and/or `game.py`.

```python
from playsound import playsound

playsound('test_sound.m4a')
```

---

🌄 **Open Image.**  If you are interested in including images in your game, follow along with these steps. It will open the image in your computer's default image viewer *(e.g. Preview)*.

(0) **Install the playsound library:** `poetry add pil`

(1) **Add a image file to your repository.** *e.g. .png, .jpg file*
> If will have multiple images, be sure to consider how you will organize your repostiory.

(2) **Incorporate the image into your game.** If this is your feature, I highly planning how you will incorporate this into the `Node()`, `Story()` and/or `game.py`.


```python
from PIL import Image

image1 = Image.open(r"test_img.png") 
image1.show()
```

---

🌄 **ASCII Art.**  ASCII Art is low-fi art that will print directly in the Terminal. For example...

```
 |\    o
    |  \    o
|\ /    .\ o
| |       (
|/ \     /
    |  /
     |/
```

💻 **The code for this looks like:**
```python
print("""\
     |\    o
    |  \    o
|\ /    .\ o
| |       (
|/ \     /
    |  /
     |/
""")
```
> *Note the `"""\` at the start and the `"""` and the end of the print statement*

🌐 **Here are a few links to find and create your own ascii art.** Just be sure to site what you use in your `README.md`
- [asciiart.eu/](https://www.asciiart.eu/)
- [ascii art text](https://patorjk.com/software/taag/#p=display&f=Epic&t=Hello)