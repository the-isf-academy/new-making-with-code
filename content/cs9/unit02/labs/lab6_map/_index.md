---
title: 6. Map Making
# draft: True
---

# Map Making

In this lab you explore the map making with [Tiled](https://doc.mapeditor.org/en/stable/). 

{{< figure src="https://www.mapeditor.org/img/screenshot-front.png" width="100%" >}}


--- 

## [0] Setup

{{< code-action >}} **First, download Tiled: [Mac](https://drive.google.com/file/d/1UbyM-hp0IEe4ryz03N5qSaWJkhXb7rJs/view?usp=sharing) or [Windows - requires vpn](https://thorbjorn.itch.io/tiled/download/eyJleHBpcmVzIjoxNjg0MTM1MTMyLCJpZCI6Mjg3Njh9.Q%2bpKwG4sifdwcTmqeuAbCdodS%2b0%3d)**

> For Mac
>   - Download the `.zip` file 
>   - Double click the file
>   - Drag the `Tiled` app into your `Applications` folder

{{< code-action "Then go into your" >}} `cs9/unit02_games` **folder.**
```shell
cd ~/desktop/making_with_code/cs9/unit02_games
```

{{< code-action "Clone your starter code." >}} Be sure to change `yourgithubusername` to your actual Github username.
```shell
git clone https://github.com/the-isf-academy/lab_map_example_yourgithubusername
```


{{< code-action "Enter the Poetry shell and install the requirements:" >}}
```shell
poetry shell
poetry install
```

This repo includes the following files:
- `game_platformer.py`
- `/assets`
    - `/map`
        - `forest_assets.png` - original asset png 
        - `forest_tileset.tsx` - assets in tileset format
        - `forest_map.tmx` - Tiled file
        - `forest_map.tmj` - exported Tiled file for Python file
    - `/sprites`
        - `slime.png` - player image



---


## [1] Game Scaling
👾 **Play the simple platformer game!** You can use the arrow keys to move around the level. Pressing `esc` will end the game. 

```shell
python game_platformer.py 
```

{{< figure src="images/courses/cs9/unit02/arcade02.png" width="25%" >}}

{{< code-action >}} **Althought the game works, the scaling is totally off!** At the top of the file, adjust the following settings until it looks just right:
- `TILE_SCALING`
- `PLAYER_SCALING`
- `SCREEN_WIDTH`
- `SCREEN_HEIGHT`

{{< figure src="images/courses/cs9/unit02/arcade03.png" width="75%" >}}

🤔 **When you make your game, you'll need to pay close attention to these settings!** Slight change in numbers affect the appearance of your game.

---


## [2] Exploring Tiled

**Now, let's expand and build out the level.**

{{< code-action >}} **Open this repo in Finder:** `open .`

{{< code-action >}} **Open the `assets/map` folder.** It has the following files:

- `forest_assets.png` - original asset png 
- `forest_tileset.tsx` - assets in tileset format
- `forest_map.tmx` - Tiled file
- `forest_map.tmj` - exported Tiled file for Python file

{{< code-action >}} **Double click the `forest_map.tmx` file to open the map in `Tiled`**

{{< figure src="images/courses/cs9/unit02/arcade04.png" width="75%" >}}


{{< look-action >}} **Look at each layer on the right hand side.** Use the `eye` tool to hide and show layers.
- Coins
- Walls
- End
- Background

{{< figure src="images/courses/cs9/unit02/arcade05.png" width="50%" >}}

{{< look-action >}} **This map is made up of tiles in the bottom right area of the screen.**

{{< figure src="images/courses/cs9/unit02/arcade06.png" width="50%" >}}

---

### [Adding to the map]

🎨 **Start by adding more coins to the map!** Double check you editing the the `Coins` layer. 

{{< figure src="images/courses/cs9/unit02/arcade_coin_example.gif" width="75%" >}}

{{< code-action >}} **Save & Export your changes.**
> If you do not *Export As*, you will not see your map changes when you play the game.
0. Save: `command + s`
0. Export As: `command + shift + e` or `File > Export As`
    - Select `JSON map files (*.tmj *.json)`

👾 **Play the game and test your changes:** `python game_platformer.py`. You should see the coins you added! If they do not disapear when your player collides with them, you most likely edited the incorrect map layer. 

---

🎨 **Now, go off and create your own level!** You can change any of the layers
- `Coins` - are tiles the player can collect
- `Walls` - are tiles the player can stand on
- `End` - are the tiles that end the game when the player collides them
- `Background` - are tiles thare are decorative and have no player effects
 
{{< aside "Export As!" >}}
☑️ Don't forget to `Export As` every time you make edits to the map. 

1. `command + shift + e` or `File > Export As`
2. Save As Select `JSON map files (*.tmj *.json)`
{{< /aside >}}

👾 **We will play test each other's levels at the end of class!**
> Feel free to edit `game_platformer.py` to experiment with map or game features. A few feature ideas: 
> - A new map layer of spikes that end the game
> - A new map layer that transports the player to another area of the map 
> - A new map layer with an item that boots your movement speed
>
> *These will all require editing the code and the map*  

---

## [3] Deliverables


{{< deliverables  >}}

**Once you've explored both games, fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSd5uRd-Ehmvu4x6LemzjVBFEIGiYmluTMxSPLDK6AruqbXMhg/viewform?usp=sf_link)**.

- Which game are you more interested in exploring?
- Are you interested in working in a group? If so, who would you like to work with?



{{< code-action "Push your work to Github:" >}}
- git status
- git add -A
- git status
- git commit -m "describe your drawing and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push



{{< /deliverables >}}