---
title: "01. Terminal Adventure"

# numberHeaders: true
# draft: true

---
# Into the Terminal
This lab will explore one of the most important tools we'll use all year: the Terminal. While it
may seem complicated at first, it will quickly become your go-to tool for computer science class.
The Terminal is what we'll use to navigate our filesystem, run code files, install software, and
do all kinds of other tasks.


{{< aside "Windows Users" >}}
Windows users should use Powershell wherever it says Terminal.

You may see more information output than your Mac peers, but all commands should work the same.
{{< /aside >}}


## Terminal Adventure Lab

{{< code-action "Let's start cloning this lab onto your laptop." >}} This will download a copy of a lab that is hosted on Github onto your computer. Think of it like downloading a folder from Google drive.
> *We will run this command `mwc update` every time we start a new lab.*
```shell
mwc update
```


{{< code-action "Open Terminal and type the following command." >}} This will open the Terminal Adventure Lab in Terminal.

```shell
cd Desktop/making_with_code/cs9/unit_00_drawing/lab_terminal_adventure
```

{{< code-action "We then must enter the Poetry shell." >}} This will ensure all of the correct packages and versions of those packages is being used.
```shell
poetry shell
```
> You should see the following output:
> ```shell
> Creating virtualenv lab-00-terminal-adventure-shGU1wL6-py3.10 in /Users/eqbrown/Library/Caches/pypoetry/virtualenvs
> Spawning shell within /Users/eqbrown/Library/Caches/pypoetry/virtualenvs/lab-00-terminal-adventure-shGU1wL6-py3.10
>bash-5.1$ . /Users/eqbrown/Library/Caches/pypoetry/virtualenvs/lab-00-terminal-adventure-shGU1wL6-py3.10/bin/activate
>(lab-00-terminal-adventure-shGU1wL6-py3.10) bash-5.1$

{{< aside "Exiting the poetry shell" >}}
When you want to exit the shell, you can type `exit` or `^D`
{{< /aside >}}

{{< code-action "Let's have a look at what's in the repository with:" >}}
```shell
ls
```
> You should see the following output:
> ```shell
> adventure	    returnToShip.py  poetry.lock	pyproject.toml
> ```
> `returnToShip.py` is a runnable Python file (you can tell by the `.py` at the end).

{{< code-action "Run it to see what happens:" >}}

```shell
python returnToShip.py

```
> You should see the following output:
> ```shell
>Your adventure has only just begun. You are not yet ready to return
>to the ship. More secrets await you in the ocean's depths.
>```

{{< aside "Your challenge is to see if you can get the treasure, using just the Terminal" >}}

Use Terminal to explore the contents of the `adventure` directory.

{{< /aside >}}

<hr>


{{< code-action "Begin by going into into the" >}}  `adventure` **directory:**
> *Do not type `$`. These are to mark the start of a Terminal command.*

```shell
$ cd adventure
$ ls
seafloor	sinking.txt
```

`sinking.txt` is a text file, so we can read it.

{{< code-action "Try using the " >}} `cat` **command:**

```shell
cat sinking.txt
```
---

### [Treasure]

{{< figure src="https://sealifeart.co.uk/wp-content/uploads/2019/11/treasure-chest-drawing.jpg" width="50%"  >}}

{{< deliverables "You will end this lab by collecting the treasure!" >}}

Continue exploring into the depths of the sea to find it.

Return to the `lab_00_terminal_adventure` directory and run the `returnToShip.py` file to see if you were successful. If you were unable to escape the monster, try again!

**Once you've successfully completed the adventure be sure to fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSc_OBYmQV95aeB96HuDfk9c3bBFzrV9HJBGFm6GVL2tFLQlfw/viewform?usp=sf_link)**.


{{< /deliverables >}}

{{< aside "Exiting the poetry shell" >}}
Remember, when you want to exit the shell, you can type `exit` or `^D`
{{< /aside >}}

---

## Terminal Commands
Below are some Terminal commands which might come in handy on your adventure.


| Command              | What it does                                 |
| --------------       | -------------------------------------------- |
| `ls`                 | List what's in the current directory.        |
| `cd ~`               | Go to your home directory                    |
| `cd somewhere`       | Go to `somewhere`                            |
| `cd ..`              | Go to the parent directory                   |
| `open file.txt`      | Opens `file.txt` with its default program    |
| `cat file.txt`       | Prints out the contents of `file.txt`        |
| `python x.py`        | Runs the Python program `x.py`               |
| `mv old.txt new.txt` | Renames a file from `old.txt` to `new.txt`. Also works for directories. |
| `mv file.txt dir`    | Moves a file to directory `dir`.             |
| `mv dir1 dir2`       | Moves `dir1` to `dir2` or renames if `dir2` doesn't exist.          |
| `cp old.txt new.txt` | Copy a file from `old.txt` to `new.txt`.     |
| `mkdir bag`          | Creates a new directory called `bag`     |
| `pwd`                | Prints the path to where you are in the filesystem |
| `rm file.txt`        | removes (deletes) the file `file.txt`        |
| `rm -d dir`          | removes (deletes) the directory `dir`        |
| `rm -r dir`          | recursively removes (deletes) the directory `dir` and all subdirectories and files within that directory. **Be careful, this is a powerful tool!** |


### [More terminal commands]
These are just for fun. There's lots more--ask your teachers!

| Command              | What it does                                 |
| --------------       | -------------------------------------------- |
| `say hello`          | Makes the computer say hello (Mac only)      |
| `cat sinking.txt \| say` | Makes the computer read the text file aloud |
| `cal`                | Shows you a monthly calendar                 |
| `banner hello`       | Just try it                                  |
