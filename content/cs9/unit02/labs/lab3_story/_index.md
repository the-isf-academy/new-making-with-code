---
title: 4. Story Lab
resources:
- name: Uno
  src: images/courses/cs9/unit02/02_01_uno.jpg
draft: true
---

# Story Lab

In this lab, you are introduced to the structure for writing a branching story. You will use this in your unit project.

{{< figure src="https://img.atlasobscura.com/qekI2cE_2gpQX77Q_jmEcoroTvzMZsTjW4fE6_jlgGk/rt:fit/w:1280/q:81/sm:1/scp:1/ar:1/aHR0cHM6Ly9hdGxh/cy1kZXYuczMuYW1h/em9uYXdzLmNvbS91/cGxvYWRzL2Fzc2V0/cy9kZTE5MWMzZWY5/ODRmMjZiNzdfZWIz/MWJkNzA1M2VjYTA5/M2JjX1RhdHRvbyBN/YXAtMSBjb3B5Lmpw/Zw.jpg" width="75%" >}}



---



## [0] Setup

{{< code-action "Start by going into your" >}} `cs9/unit02_games` **folder.**
```shell
cd ~/desktop/making_with_code/cs9/unit02_games
```

{{< code-action "Clone your starter code." >}} Be sure to change `yourgithubusername` to your actual Github username.
```shell
git clone https://github.com/the-isf-academy/lab_story_example_yourgithubusername
```


{{< code-action "Enter the Poetry shell and install the requirements:" >}}
```shell
poetry shell
poetry install
```

This repo includes the following files:
- `game.py`
- `story_setup.py`
- `view.py`
- `node.py`
- `story.py`

---

## [2] How do you write a story? 

**Stories are made up of connected connected `Node()` objects.**

---

### [Node]

{{< look-action >}} Let's start by looking at the `Node` constructor:

```python
class Node():
  def __init__(self, id, option_title, description):
      self.id = id
      self.children = []   
      self.option_title = option_title                    
      self.description = description  
```
- `id`: a unique id *(`str`, `float`, or `integer`)*
- `children`: a list of `Node()` objects 
- `option_title`: the text for the display in the menu *(`str`)*
- `description`:  the additional text for when a user selects an option *(`str`)*

It has the following methods:
- `__str__`: defines how a `Node` is printed
- `add_child(child_node)`: this  adds `child_node` to its `children`
  - this is how the story pieces are connected to each other.
- `find(id)` - searches through the nodes to return the node with the `id`
  

---

### [Story]

**Now, let's look at the `Story()` constructor.** This is the primary class you will be interacting with when writing your story. 
```python
class Story():
  def __init__(self, title, start_id, start_option_title, start_description):
      self.title = title
      self.current_node = Node(start_id, start_option_title, start_description)
      self.first_node = self.current_node

```
- `title`: the title of your story *(`str)*
- `current_node`: the current `Node` of your story, at the start of the story it is the same as `first_node`
- `first_node`: the first `Node` of your story


**A `Story()` has 4 main methods.**

```python
def add_new_child(self, parent_id, child_id, child_option_title, child_description):
  parent_node = self.current_node.find(parent_id)

  new_child_node = Node(
      id = child_id,
      option_title = child_option_title,
      description= child_description
  )

  parent_node.add_child(new_child_node)

def get_current_children(self):
  return self.current_node.children

def set_current_node(self,chosen_node):
  self.current_node = chosen_node

def is_finished(self):
  return len(self.current_node.children) == 0
```
- `add_new_child()`: adds a new child node to a parent node  
- `get_current_children()`:returns a list of the children of the current node
- `set_current_node(chosen_node)`: sets the `current_node` to the `chosen_node` 
- `is_finished()`: returns True or False based on if the current node has children

---

## [3] Building your first story

{{< look-action >}} **Let's start taking a look at `story_setup.py`** As you can see, the current story has only has 4 unique `Node()` objects and it call `.add_new_child()` to build the story.

{{< expand "story_setup.py" >}}
```python
from story import Story


main_story = Story(
    title='Lunch.',
    start_id = 'lunch',
    start_option_title = "It's lunch time.",
    start_description= "Where will you go?"
)

main_story.add_new_child(
    parent_id = 'lunch', 
    child_id = 'cyberport',
    child_option_title='Walk to cyberport.',
    child_description="It's a nice day, better to go for a short walk."
    )

main_story.add_new_child(
    parent_id = 'lunch', 
    child_id = 'isf_ablock_cafe',
    child_option_title='Elevator down to A Block Cafeteria.',
    child_description="You're short on time, better to grab something quick downstairs."
    )

main_story.add_new_child(
    parent_id = 'isf_ablock_cafe', 
    child_id = 'optionA',
    child_option_title='Char Siu Rice',
    child_description="Yum, pork!"
    )
```
{{< /expand>}}

{{< code-action >}} **Try to play through the short story in by running:** `python game.py`

```shell
$ python game.py

==================================================
Title: Lunch.

It's lunch time.
Where will you go?
==================================================

[what will you do?]
❯ Walk to cyberport.
  Elevator down to A Block Cafeteria.
```


🧐 *Hmmmmm.... it works, but it the story does not continue with your choice.*

---

### [Finish game.py]

{{< code-action >}} **Finish `game.py` so it properly plays through the story.** It should:

0. loop through the given chosen options 
0. display the description of each chosen node
0. end when there are no more options for the chosen node

🧐 *Consider...:*
- *What methods exist in the `View()` and `Story()` that you could use?*
- *how do you loop until a condition is met?*

👾 **Be sure to play test the game to ensure it works as expected:** `python game.py`


{{< expand "Example play through" >}}

```

$ python game.py

==================================================
Title: Lunch.

It's lunch time.
Where will you go?
==================================================

[what will you do?] Walk to cyberport.
It's a nice day, better to go for a short walk.

[what will you do?] Go to fusion.
It's a grocery store day! What should I get?


==================================================
End of Story
==================================================

```

{{< /expand >}}

---

### [Continue the Story]

Now that you've gotten a working `game.py`, let's build out the story. 

Come up with your own options to continue the story! We'll share out at the end of class. 

{{< code-action >}} **"Continue the story, add at least 3 unique `Node()` objects.** Some ideas...
- add additional lunch options in ISF A Block Cafeteria
- add lunch options in Fusion 
- add other locations to purchase lunch in Cyberport 

👾 **Be sure to play test the game to ensure your story additions work as expected:** `python game.py`

---

## [5] Deliverables

{{< deliverables  >}}

**Once you've successfully completed the game be sure to fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSdt-1ot7m6E6rP01LmJTt9uvIrdOnLvfGw_Zhl5RFdkPN3XYg/viewform?usp=sf_link)**.


{{< code-action "Push your work to Github:" >}}
- git status
- git add -A
- git status
- git commit -m "describe your drawing and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push

{{< /deliverables >}}


---


## [6] Extension:

For your project, you will need to build out **one** additional feature to this `Story` framework. Here are a few suggested features:
- looping stories with the ability to set an Node as a current Node's child 
  - *e.g. player can go back to a previous area*
- a `Player` class with unique properties 
  - *e.g. hunger, money, health*
- variable messaging in the story
  - *e.g. `"you have visited this store 5 times"`*
- a special `Node` child-class that gives items or status effects
  - *e.g. a locked door where you need to first collect the key in a certain room.*


{{< code-action >}} **Use this time to experiment with of these features! If you have your own ideas, feel free to experiment with that!**


<!-- ---

## [0] Choose your own Adventure

👾 **Let's start by playing a couple of example choose your own adventure games.** As you play, consider the different genres and what's possible with this structure. 
- [Harry Potter - Sorting Hat](https://unfold.studio/stories/303/)
- [Oregon Trail 1971](https://unfold.studio/stories/10782/)
- [City Exploration](https://unfold.studio/stories/2649/)
- [Store front Example, variables](https://unfold.studio/stories/1065/)

--- -->