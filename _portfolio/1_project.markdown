---
layout: post
title: Localization in Godot
description: a project with a background image
img: /img/12.jpg
---


# Localizing in the Godot game engine - 'Evol' and the Challenges of JSON files

### Introduction

For my final project for my Software and Games Localization course, two of my colleagues and I worked together and chose to try something new and localize a game in an engine we did not learn about in class.
 
### Background - The Godot Engine and Evol

<div class="img_row">
  <img class="col three" src="/img/godot_01.png">
</div>
<div class="col three caption">
Screenshot of the game localized into Japanese
</div>
For our project, we chose to localize a game called [Evol](https://rustymonky.itch.io/evol), a name which can be interpreted two ways: one is that it is short for "evolution", and the second interpretation is it can be pronounced similar to 'evil', indicative of what your character must to do in order to survive. The general gist of the game is similar to Pokemon, in which your character travels around a field looking for monsters to fight and consume in order to become stronger and eventually evolve. Previously, we learned one method to localize in the Unity game engine; however, Evol was created using the [Godot game engine](http://godotengine.org/).

Although Evol was created in a game engine we had not learned before, what drew me to go for it and to try learning the engine was that Godot has built-inlocalization functions. Additionally, Godot is open source and works on Windows, Mac, *and* even Linux! Thus, although we would have to learn how to navigate a new software, we assumed at least the localization process would be relatively straight-forward. This was a naive assumption to make.
 
### The Process - Localization
For our project, we decided to localize the game into Japanese and Spanish. The general process for localizing in Godot consists of taking strings and labels and buttons and replacing them with **Keys**, which are then entered into a CSV along with all the languages you would like to localize your game into, including the 'default' language. For a more detailed breakdown of how this works, I suggest looking at the [Godot documentation](https://docs.godotengine.org/en/3.0/tutorials/i18n/internationalizing_games.html), or taking a look at our presentation video at the end of this post.

At first glance, this seems pretty simple: we added a CSV with keys corresponding to various strings throughout the game and the on-screen text would pull the correct strings depending on what locale we were playing in.

<div class="img_row">
  <img class="col three" src="/img/godot_02.png">
</div>
<div class = "col three caption">
A screenshot of our CSV setup
</div>

However, this only accounted for perhaps one-third of the strings in the game. From our initial few playthroughs and searching, we found that there were 3 main file types that contained all the strings: GD, TSCN, and JSON files. GD and TSCN files are both unique to the Godot engine. For GD and TSCN files, replacing the strings with a key and adding that key and corresponding strings to the CSV worked, but JSON files were another matter.

Firstly, JSON files and the strings they housed were not visible in the game engine editor. We used a text editor to search for many of the strings that we saw on-screen but didn't find in either GD or TSCN files, which led us to the JSON files. There were three JSON files, each containing the data for the monsters, items, and moves, respectively. However, we had to first find how and where exactly in the code these JSON files were being pulled; we did not want to detrimentally edit the game code and break the game.
 
### The Solution - JSON File Localization

Again, by utilizing a text editor, we found the function where all three JSON files were pulled, and by looking for instances in other parts of the game that called the function, we were able to understand how the JSON files and their data fit into the game. The original code can be seen below.

<div class="img_row">
  <img class="col three" src="/img/godot_03.png">
</div>

Unfortunately, what we determined was the simplest thing to do also made the data somewhat messier. We decided to insert some code that would call the locale and set it to a variable that could be used to call different versions of the three JSON files. The final code can be seen below.

<div class="img_row">
  <img class="col three" src="/img/godot_04.png">
</div>

The final folder with all the localized JSON files looked like this:

<div class="img_row">
  <img class="col three" src="/img/godot_05.png">
</div>

Although we were aware that multilingual JSON files are possible, the game was not created with internationalization in mind. In order to create multilingual JSON files that worked with the game, we would have had to rewrite some of the core game code itself, which was outside the scope of this project. Of course, if this game were to be localized into 9+ languages, our method would not be best practices, since it would mean 3 JSON files for *each* locale. Keeping each JSON file consistent and up-to-date would be a nightmare.
 
### Other Challenges - Incomplete Game, Internationalization, Incompatible Font

We had many other challenges in the process of localizing this game. Our main obstacles included: Evol being an incomplete game, lack of internationalization considerations, and an incompatible font.

Evol was created for the Github 2017 GameOff, and as such was not a full, finished game. We ran into issues while playtesting that were not immediately apparent as game errors and not errors created from localization.

We also had to change how many of the strings were formed, as there was rampant concatenation in the source code. Understandably, the creator of Evol had not thought to make this game internationalization-friendly when he created it. This was immediately apparent to us because we were localizing the game from English into Japanese, which has a very different grammar structure than English.

Lastly, the font used in-game was also not compatible with CJK texts. We had to find a new CJK-friendly font that was similar to the game font and figure out how to load the font in correctly.

For more information about these challenges, please see my colleague [Hanna Nowicki's post](https://sites.miis.edu/hnowicki/2018/12/12/game-localization-in-godot/), or you can watch our presentation linked below.
 
Our presentation video: [here](https://drive.google.com/file/d/1gVtlONpEEFVIKs4OwzXFYvkY-QHGEQeI/view?usp=sharing)
Our finalized project files: [here](https://drive.google.com/open?id=140iWacdczgqKfvckQXuixx-TTd4fOuBs)
Evol's original game files: [here](https://github.com/RustyMonky/Evol)

