---
layout: single
title: "Winter's Return"
date: 2020-03-01 17:17:50 -0600
categories: projects
read_time: true
---
{% include figure image_path="/assets/images/sq_game.PNG" alt="Screenshot of Winter's Return" %}

A Unity 2D game developed in 48 hours for [UT Game Jam 2019](https://itch.io/jam/ut-game-jam-2019).
Check out the full credits and download the game [here](https://schwizzlers.itch.io/winters-return).

Special thanks for out mentor Kurt Williams from Twisted Pixel Games! He helped to create many of the game's key art assets.


## Inspiration

<figure style="float: right; padding-left: 10px; width:35%;">	
	<img src="/assets/images/sq_irl.jpg"/>
	<figcaption>
	Just one of the many squirrels at UT
	</figcaption>
</figure>
The theme of the 2019 UT Game Jam was *"Return"*. Inspred by the numerous squirrels on campus,
our team eventaully settled on the idea of a squirrel trying to return nuts to its home. Additionally, 
the *return* of winter would give a sense of urgency and force the player to act fast.

At first, we wanted to create a 3D game with blockly characters (Think *Crossy Road* or even *Minecraft*).
However, we soon realised that creating a 3D game in 48 hours won't be easy, so we settled on 2D instead.


## Running out of Time
<img style="float: right; padding-left: 10px;" src="/assets/images/sq_seasons.PNG" width="55%" />
On the the more interesting things that I worked on was the system for telling the player how much time they had left.
We decided aganist having a timer until the last moment (becase squirrels don't have stopwatches). Instead the player would have to look
for changes in the game enviroment to guess how much time they had left. Each level lasted 60 seconds. 

At 40 seconds left, the trees would
begin to turn orange, siginifying the arrival of fall. To do this, the sprite for the trees are actually white. The game would then dynamically apply
a tint to the tree (green at first, then orange) to smoothly fade the color.

At 30 seconds, a light snow would begin to fall, and graudally intesnifying. Finally at 10 seconds,
the trees would start to be covered by the snow, and the final countdown would start. I liked this system because it creates tension without having to
rely upon an intrusive timer.

## Ha Ha I'm In Danger
<img style="float: right; padding-left: 10px;" src="/assets/images/sq_cat.PNG" width="55%" />
Being a squirrel certainly is not easy. In addition to starving and freezing there are many other threats as well. The first of these is a rather fat cat.
The cat's AI is as simple as it gets, pointing toward you and accelerating. This caused the cat's motion to be rather drifty, and combined with the sprite, made the
cat seem very chubby indeed.

The second obstalce was a road that players had to cross. Due to human activity, most of the nut trees on the starting side of the road have been cut down. This forces
the player to cross the highway and dodge cars to access the nuts on the other side. Compared to the cats, cars are more predicatable, but impossible to stop.

We decided that getting eatten or run over resulting in an instant game over was too punishing. Instead, you would drop all your nuts and respawn at the home tree
after a certainly delay. Getting hit was still bad, as it caused you to lose valuable time and possibly drop your nuts into a dangerous location.

## Dark Souls, but With Squirrels
Our team did play test the game, but only internally. Because we were familar with game mechanics, we thought it wasn't that bad.

When it was time for the showcase, we realised that the game was actually *really* hard. Out of the dozens of people who played the game, only two or three
managed to clear all the levels. Most players could juke the cat, but the fat feline combined with automobiles was too much. A difficulty option to slow down the
speed of obstalces and increase the time limit would certainly be a good feature to add.

If you think you can survive the winter, you can download and play the game for free from [itch.io](https://schwizzlers.itch.io/winters-return).