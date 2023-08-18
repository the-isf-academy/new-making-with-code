---
title: 5. Arcade Examples
# draft: True
---

# Python Aracde Intro Lab

In this lab you explore the Python Aracde framework through example games.

{{< figure src="https://api.arcade.academy/en/latest/_images/arcade-logo.svg" width="20%" >}}


📖 You can find the offical documentation [HERE](https://api.arcade.academy/en/latest/get_started.html).

--- 

## [0] Setup

You will be running a game from your terminal, so your terminal will need permission to monitor your input.

{{< code-action >}} **Go to Settings > Security &  Privacy > Privacy. Scroll to Input Monitoring and add Terminal.** Terminal to need to restart in order to save this preference.

{{< figure src="images/courses/cs9/unit02/02_02_input_monitoring_permission.png" width="400px" >}}


{{< code-action "Start by going into your" >}} `cs9/unit02_games` **folder.**
```shell
cd ~/desktop/making_with_code/cs9/unit02_games
```

{{< code-action "Clone the repo." >}} Do NOT add your username to the end of the url.
```shell
git clone https://github.com/the-isf-academy/lab_games_sampler
```


{{< code-action "Enter the Poetry shell and install the requirements:" >}}
```shell
poetry shell
poetry install
```

This repo includes the following files:
- `game_platformer.py`
- `game_bullets.py` 


---


## [1] Simple Platformer Game
👾 **Play the simple platformer game!** You can use the arrow keys to move around the level.

```shell
python game_platformer.py 
```

{{< figure src="images/courses/cs9/unit02/arcade00.png" width="400px" >}}

{{< code-action >}} **Experiment with the settings!** A few things to try changing:
- the physics settings at the top of the file
- the keyboard mapping in `on_key_press()` and `on_key_release()`
- the variables in `pan_camera_to_user()`
- the [background color](https://api.arcade.academy/en/latest/arcade.color.html)
- the player sprite image

---


## [2] Simple Bullet Game
👾 **Play the simple platformer game!** You can use the left, right, and up arrows to control the player and the bullets. 

```shell
python game_bullets.py 
```

{{< figure src="images/courses/cs9/unit02/arcade01.png" width="400px" >}}


{{< code-action >}} **Experiment with the settings!** A few things to try changing:
- the bullet speed
- the coin positions
- the keyboard mapping in `on_key_press()` and `on_key_release()`
- the background color or image
- the bullet sprite image


---

## [3] Deliverables


{{< deliverables  >}}

**Once you've explored both games, fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSd5uRd-Ehmvu4x6LemzjVBFEIGiYmluTMxSPLDK6AruqbXMhg/viewform?usp=sf_link)**.

- Which game are you more interested in exploring?
- Who would you like to work with in a group?


{{< /deliverables >}}