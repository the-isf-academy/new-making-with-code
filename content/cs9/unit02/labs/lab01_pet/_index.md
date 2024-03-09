---
title: 1. Pet Lab
draft: true
---

# Pet Lab


- move checkpoint qs to form
- change to VScode 
- add nap() and play()
- create a family of pets v. interface


👀 **In this lab, you will learn about object oriented programming.** You will create the backend of a pet simulator game.

📖 **Here is more information on how to create a class:** [12.5 Constructors](http://programarcadegames.com/index.php?chapter=introduction_to_classes&lang=en#section_12_5)


---

## [0] Setup
{{< code-action "Start by going into your" >}} `cs9/unit02_games` **folder.**
```shell
cd ~/desktop/making_with_code/cs9/unit_02
```

{{< code-action "Then, clone your starter code." >}} Be sure to change `YOUR-GITHUB-USERNAME` to your actual Github username.
```shell
git clone https://github.com/the-isf-academy/lab_pet_yourgithubusername
cd lab_pet_yourgithubusername
```

{{< code-action "Enter the Poetry shell and install the requirements:" >}}
```shell
poetry shell
poetry install
```

{{< code-action >}} `cd` **into the lab**
```shell
cd lab_pet_yourgithubusername
```


{{< code-action "Enter the Poetry Shell and install the required packages." >}} *Each line should go one at a time.*
```shell
poetry shell
poetry install
```


This lab includes the following files:
- `pet.py`
- `test_pet.py`
- `game_interface.py`
- `helpers.py`

---

## [1] Testing your Pet

{{< code-action  >}} **Open the folder in VSCode**
```shell
code .
```

{{< look-action >}} **First, we will focus on `pet.py` and `test_pet.py`**
- `pet.py` is the definition of a Python class for `Pet`
- `test_pet.py` is simple file just for testing our `Pet`


{{< code-action >}} **Let's start by running `test_pet.py`** 
> *Do not copy `$`, simply type the command after the `$`. It is to distinguish between Terminal commands v. Terminal output.*
```shell
$ python test_pet.py
Peanut
```

The `Pet` has the following properties:
- `name`
- `bored`

and the following methods:
- `introduce()`
- `play()` 

{{< code-action >}} **Test each of the properties and methods in `test_pet.py`.** When you run `python test_pet.py` it should look something like this:
```shell
$ python test_pet.py
Peanut
👋 Hi, I am Peanut!
Wooooo, running!
True
```


---

## [2] What type of animal is your pet?

Now that you've used the `Pet` class, let's delve into the code and make our `Pet` more complex. People can have all different types of pets, so **lets' add a `species` property** to our `Pet`.

{{< aside >}}
This section of the lab walks you through how to write a `class` in Python. Keep a look out for the {{< code-action  >}} to ensure you add all the necessary features. 
{{< /aside >}}

{{< look-action  >}} **Go to `pet.py` in VSCode**

---

### [What's a class?]

In the `test_pet.py`, **you just successfully used an instance of a class!**

{{< look-action >}} If you look in the Pet class, you can see on `line 1` - that we name the class `Pet`. **A class a simply a blueprint for group of data, or information, with specific functionalities.** In this class we are creating a blueprint for storing information about pets. 

```python {linenos=table, hl_lines=["1"],linenostart=1}
class Pet:
    def __init__(self):
        '''This initializes the pet with its properties.'''

        self.name = None        # holds the pet's name
        self.bored = True       # holds the pet's bored level
```

---

### [Adding a new property]

{{< look-action >}} The information associated with a `Pet` is defined on `lines 5-7`. **Information associated with a class is called `property` and is stored in a variable.** Our pet has three properties. Properties are variables that only belong to a specific class.

```python {linenos=table, hl_lines=["5-6"],linenostart=1}
class Pet:
    def __init__(self):
        '''This initializes the pet with its properties.'''

        self.name = None        # holds the pet's name
        self.bored = True       # holds the pet's bored level
```
>The `Pet` currently two properties, `name` and `bored`.


{{< code-action  >}} **Add a `species` property to the `Pet` class that is initially set to `None`.** It will work just like the `name` property.

---

### [Adding a new method]

Now that we've added the `species` property, we need to add a method to set the property.

{{< look-action >}} If you scroll down to lines 9-12, we see an example of a method. **A method is similar to a function. The only difference is that a method belongs to a certain class, like `Pet`.**


```python {linenos=table, linenostart=9}
def set_name(self, name):
    '''This method sets the name property'''

    self.name = name
```
> The `set_name()` method changes the `name` property to whatever the user put as the parameter.
>
> *e.g. `my_pet.set_name('Bob')`*

Just like the `name` property, we need to be able to set the `species` of our pet.

{{< code-action "Add a new method called " >}} **`set_species()`.** This method should change the `species` property of the `Pet` class.

---

### [Testing your changes]

Let's see if the `species` property and `set_species()` method is working by jumping back into `test_pet.py`.

{{< code-action  >}} **Test your changes by using `set_species()` on `pet1`**
```shell
$ python test_pet.py
Peanut
👋 Hi, I am Peanut!
Wooooo, running!
True
Dog
```

---

### [Using the species property]

Right now, the `introduce()` method just has the pet say their name. Let's make it more detailed by including their `species` in the introduction.

```python {linenos=table, linenostart=14}
def introduce(self):
    '''This method introduces the pet with its name.'''

    print("Hi, I'm", self.name)
```
<br>

{{< code-action  >}} **Edit the `introduce()` method so that your pet will also tell you its species.**

{{< code-action  >}} **Test the updated `introduce()` method in `test_pet.py`.** 
```shell
$ python test_pet.py
Peanut
👋 Hi, I am Peanut and I am a dog!
Wooooo, running!
True
Dog
```
---



## [3] Pet Simulator


👾 **Now that you have experienced the backend of the `Pet`, let's play the game!** The `Pet` now has a nice Terminal interface where you can interact with it through a menu system, just like a lo-fi text-based video game.
```shell
python game_interface.py
```

```shell
-----------------------------------
---- Welcome to Pet Simulator ----
----------------------------------- 

What would you like to name your pet?
 > Peanut
-------------------------
Your pet is ready!
-------------------------
> Introduce                                                                                                                
  Quit         
```

---

### [Add play()]

{{< code-action >}} **Edit `game_interface.py` so you can `play()` with your `Pet`!** Start by reading through the code to make sure you understand how it works. Then make small edits to add in `play()`. Be sure to look for:
- how are menu options being displayed? 
- how are the different functions being ran based on the user selection? 

{{< code-action >}} **Play test it!** `python game_interface.py`

---

## [4] Deliverables


{{< deliverables  >}}

**Once you've successfully completed the game be sure to fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSdUQd7aUsxjO1Dlt9XY50NV0ddAq8ki6GZZMRck1uOk9XdwhQ/viewform?usp=sf_link)**.


{{< code-action "Push your work to Github:" >}}
- git status
- git add -A
- git status
- git commit -m "describe your drawing and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push

{{< /deliverables >}}

---

## [5] Extension

{{< aside >}}
If you have your own ideas, build on the `Pet` however you would like! 

But if you're unsure where to start, there are 3 ideas below. 
{{< /aside >}}

### [Add a hunger level]

At this point, you have a working `Pet`, but it's pretty basic. Most pets, get hungry and need to eat. 

**This will require you to add a `hunger` property and `eat()` method.**

**Your `hunger` property should:**
- be an numerical data type
- decreased when it plays 
- increase when it uses `eat()`

{{< code-action >}} **Test your edits with the `python shell`.**  


{{< code-action >}} **Edit `interface.py` to include all of the features the `Pet` has.**

{{< code-action >}} **Play test it:** `python game_interface.py`

---

### [Tamagotchi Features]

This lab was inspired by the Tamagotchi!

{{< figure src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/f2/Tamagotchi_0124_ubt.jpeg/330px-Tamagotchi_0124_ubt.jpeg" width="40%" >}}

{{< code-action >}} **Include as many of the original Tamagotchi features as you can!**
- [Tamagotchi wiki](https://en.wikipedia.org/wiki/Tamagotchi)

---

### [Inheritance]

{{< code-action >}} **Create subclasses of your `Pet` using `inheritance`.** For example, 
what features do dogs have that cats do not have? 

📖 You'll need to learn how to incorporate inheritance: [12.6 Inheritance](http://programarcadegames.com/index.php?chapter=introduction_to_classes&lang=en#section_12_6)