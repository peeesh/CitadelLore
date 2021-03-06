---
title: Guide to Spriting
permalink: wiki/Guide_to_Spriting/
layout: wiki
tags:
 - Guides
---

This is not a technical guide on how to do sprites in a graphical
program, this is a guide intended for people who know how to sprite, but
need to know what exactly is needed when people want sprites done for
them. Most sprites are 32x32 pixels. They use 32b colors (24b + alpha
channel).

Object overview
---------------

There are 4 types of objects in the game:

-   **Area** - we won't be interested in these as you can't see it
    ingame and wip graphics are sufficient,
-   **Mob** - humans, monkeys, cyborgs, aliens and other living
    creatures on the station,
-   **Objects** - machines, doors, items and anything else in the game,
-   **Turf** - walls, floors and space

The DMI file format
-------------------

Sprites in SS13 are packaged in .dmi files. To make a new dmi file, open
up dream maker, select file &gt; new and choose icon file (dmi) from the
drop-down menu. Write a file path for it and hit ok.

A new window will open with a blank file. in the upper-right are two
spaces for sprite dimensions. Most sprites are 32x32 pixels in size. One
dmi file cannot hold sprites of different sizes, unfortunately.

Now right-click somewhere in the whiteness. There are two types of
sprite: pixmap and movie. A pixmap is static while a movie can be
animated and face multiple directions, that's all the difference. Let's
make a movie sprite. (New movie)

A window opens with four directional arrows and 3 frames for each of
them, all of them gray. Byond understands 8 directions. You can choose
how many you wish to use below the sprites themselves: 1, 4 or 8. You
can also select how many frames you wish the animation to have. If
you're making a multi-directional static sprite, make a movie with 1
frame, so no animation, but with 4 or 8 directions, depending how many
you need. If you wish to have the sprite animated it may also interest
you that you can set the delay in 1/10 of a second above the particular
frame. Okay, hopefully you'll know what to do from here. The built-in
sprite editing tool is very primitive and the only thing worth
mentioning in it is how to apply the alpha filter. If you double-click
any image you'll get to the sprite editor, and at the right of it is a
vertical slider, which controls the alpha channel. Also worth mentioning
is that copying from the editor can behave a bit strange, by making full
backgrounds despite the alpha filter being set. Just 'flood' the
background with a color with an alpha value of 0 or use 'import', which
works fine.

Now let's assume we've made your sprites sprites, go back to the dmi
file (the screen which showed up when you first made the file). Assuming
you've made a sprite, you'll see it in the list there. Double-click just
below the actual sprite and a rename window should open, alternatively
select the sprite and hit F2 on your keyboard. Give a name to your
sprite. This name is often referred as an icon\_state, as that's the
variable name which defines it in code.

Also note that you can import and export image files of different sorts
by selecting the files you wish to export in the editor (hold ctrl to
select multiple) and right clicking and selecting export, or right
clicking anywhere and selecting import to import. DMI is similar to PNG,
so if you rename a DMI's extension to PNG it should work in all
graphical editing software. It usually works in reverse too. This makes
recoloring quicker.

Now, hopefully that's all the information you need to sprite and make
dmi files.

Required sprites by object category
-----------------------------------

Now to tell you what sprites different types of items need:

### Mobs

-   Mobs require sprites in 4 directions. If you want them to be able to
    wear clothes, hold items, wear gloves, glasses, etc. then the part
    which you'd like to keep needs to be in the same place as on the
    human sprite in all 4 directions. Yeah, this limits you a lot.

### Turfs

-   Floors are in icons/turf/floors.dmi - Check the file for examples
-   Walls are in icons/turf/walls.dmi - Check the file for examples
-   And some other stuff is in other files in icons/turf/
-   I think these are pretty self explanatory

### Objects

-   Items: Stuff that you can pick up and use: Generally require an item
    sprite and an in-hand sprite. The item sprite can be put in
    icons/obj/items.dmi or other dmi files, while the in-hand sprite
    needs to be in icons/mob/items\_lefthand.dmi and
    icons/mob/items\_righthand.dmi
-   Clothing: Stuff that you can wear: Generally requires an item sprite
    in the appropriate dmi file in icons/obj/clothing/ , an in-hand
    sprite in icons/mob/items\_lefthand.dmi and items\_righthand.dmi, as
    well as the on-mob sprite in the appropriate file in icons/mob/
-   Machinery: Usually either just one sprite or separate on-off
    sprites. It tends to differ from machine to machine

Locating sprites
----------------

For most objects if you double-click them in the object tree (on the
left side of the dream maker window) you will be taken to their
definition in code. In the variables below what is highlighted you will
often see:

` icon = 'abc.dmi'`  
` icon_state = "sprite_name"`

The icon variable defines the file which contains the sprites and the
icon\_state defines the name of the sprite in the specified file.
Sometimes the icon or even icon\_state variable will not be set under
the definition. This means they're set on a parent level. If you're
looking for /obj/item/weapon/storage/belt/full and can't see it, try
looking at /obj/item/weapon/storage/belt. If it isn't there try looking
for /obj/item/weapon/storage and so on.

Note that sometimes double-clicking an object in the object tree will
not bring you to the object definition. You will know this by the
highlighted line not being the same as the path to the object you
double-clicked in the object browser. Searching for the definition in
such cases can be a bit hard, so I've prepared a list of the most
commonly used dmi files for certain objects:

**/obj/machinery**  
icon = 'stationobjs.dmi'  
definition in:
[code/game/machinery](https://github.com/Baystation12/Baystation12/tree/master/code/game/machinery)

**/obj/item/weapon/storage**  
icon = 'storage.dmi'  
definition in:
[code/game/objects/items/weapons/storage](https://github.com/Baystation12/Baystation12/tree/master/code/game/objects/items/weapons/storage)

**/obj/item/weapon**  
icon = 'weapons.dmi'  
definition in:
[code/game/objects/items/weapons/](https://github.com/Baystation12/Baystation12/tree/master/code/game/objects/items/weapons)

**/obj/item**  
icon = 'items.dmi'  
definition in:
[code/game/objects/items/](https://github.com/Baystation12/Baystation12/tree/master/code/game/objects/items)

Contributing sprites and finding sprite requests
------------------------------------------------

See here to submit sprite:
<http://baystation12.net/forums/viewtopic.php?f=44&t=5251>

Other useful links

<http://baystation12.net/forums/viewforum.php?f=44> - General Sprite
Sub-forum

<http://baystation12.net/forums/viewtopic.php?f=44&t=4294> - General
Sprite Request Thread

Tips
----

-   Not able to get the color right? Try double-clicking on the color
    preview box or in the color pallete for more options.
-   You are capable of using the left and right mouse buttons for
    different colors. Left is the circle and right is the square.
-   Make a small mistake? Click on the original color in the used colors
    section. This is called mask and will work like an eraser.
-   Get a template: try right-clicking on the desired sprite and select
    copy. You can copy and paste whole sprites to ease editing.

[Category:Game Resources](/wiki/Category:Game_Resources "wikilink")
