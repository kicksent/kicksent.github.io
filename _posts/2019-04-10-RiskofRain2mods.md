---
layout: posts
title: Risk of Rain 2 Mods

#image: /assets/img/cmcBTC2.jpg 

gallery: 
  - url: https://store.steampowered.com/app/632360/Risk_of_Rain_2/
    image_path: https://steamcdn-a.akamaihd.net/steam/apps/632360/ss_d93451e8534c512fcf15e1d8c7a02e2277807aa7.600x338.jpg?t=1554475761
    alt: "ror2 steam"
    title: "ror2 steam"

# gallery2:
#   - url: assets/img/ror2_dnspy_loc.JPG
#     image_path: assets/img/ror2_dnspy_loc.JPG
#     alt: "ror2"
#     title: "ror2"

# gallery3:
#   - url: assets/img/ror2_assembly.JPG
#     image_path: assets/img/ror2_assembly.JPG
#     alt: "ror2"
#     title: "ror2"

gallery4:
  - url: /assets/img/ror2_is_modded.JPG
    image_path: /assets/img/ror2_is_modded.JPG
    alt: "ror2"
    title: "ror2"

gallery5:
  - url: /assets/img/ror2_give_money.JPG
    image_path: /assets/img/ror2_give_money.JPG
    alt: "ror2"
    title: "ror2"

gallery6:
  - url: /assets/img/ror2_increase_interactable.JPG
    image_path: /assets/img/ror2_increase_interactable.JPG
    alt: "ror2"
    title: "ror2"


---
{% include gallery caption="[Risk of Rain 2](https://store.steampowered.com/app/632360/Risk_of_Rain_2/) is a multiplayer roguelike 3D sequel to Risk of Rain." %}

<!-- [Risk of Rain 2](https://store.steampowered.com/app/632360/Risk_of_Rain_2/) is a multiplayer roguelike 3D sequel to Risk of Rain. -->
___

## Prereqs:

1. Download [**dnSpy**](https://github.com/0xd4d/dnSpy/releases). 
  * For 64-bit Windows download **dnSpy-netcore-win64.zip**
  * For 32-bit Windows download **dnSpy-netcore-win32.zip**
2. Open dnSpy: Extract files and locate dnSpy.exe in extracted folder. Local path: dnSpy-netcore-win64/dnSpy.exe 

3. Locate your Assembly-CSharp.dll in Steam Library. Mine was in C:\SteamLibrary\steamapps\common\Risk of Rain 2\Risk of Rain 2_Data\Managed\Assembly-CSharp.dll 


4. Open Assembly.dll in dnSpy
5. Select one of the mods:

## Mods:

  * [Set the game as modded (please do this one)](#setting-the-game-as-modded)
  * [100x money from all sources](#increase-money-given-from-all-sources-by-100x)
  * [Change the number of chests, shrines, printers, etc.](#change-the-number-of-interactable-items)

___

### Setting the game as modded:
ROR2 devs message : "We don't officially support modding at this time but if you're going to mod the game please change this value to true if you're modding the game. This will disable some things like Prismatic Trials and put players into a separate matchmaking queue from vanilla users to protect their game experience."

**TL;DR** - Do this so that others arent forced to play your mods in online play. 

{% include gallery id="gallery4" caption="" %}
#### Steps:
* Open Assembly-CSharp.dll in dnSpy (See [Prereqs](#prereqs) section)
* Search **isModded** and double click the first result
* Find line 411: `public static bool isModded = false;`
* Right click -> **Edit Method (C#)...**
* Change line to: `public static bool isModded = true;`
* Click **Compile**
* File -> **Save Module...** or **Save All...** -> **OK**

___

### Increase money given from all sources by 100x
Money turns into experience in RoR, this mod setting is very fun without one small change!

{% include gallery id="gallery5" caption="" %}
#### Steps:
* Open Assembly-CSharp.dll in dnSpy (See [Prereqs](#prereqs) section)
* Search **GiveMoney** and double click first result
* Right click -> **Edit Method (C#)...** or **Edit Class(C#)...**
* Add a new line on line 189 inside of the function GiveMoney and write `amount *= 100u;`
* Click **Compile**
* **File** -> **Save Module...** or **Save All...** -> **OK**

___

### Change the number of interactable items
Increase the number of chests, shrines, money capsules, printers, etc.

{% include gallery id="gallery6" caption="" %}
#### Steps:
* Open Assembly-CSharp.dll in dnSpy (See [Prereqs](#prereqs) section)
* Search **SceneDirector** and double click first result
* Right click -> **Edit Method (C#)...** or **Edit Class(C#)...**
* End of line 29 add `* 3` to triple the spawns like this: `this.interactableCredit = (int)((float)component.sceneDirectorInteractibleCredits * num) * 3;` 
* Click **Compile**
* **File** -> **Save Module...** or **Save All...** -> **OK**


