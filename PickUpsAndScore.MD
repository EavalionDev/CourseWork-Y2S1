# Pick Ups And Score

This is the fourth and final tutorial in the series, this will focus on creating two scripts, one to allow pick up items to function
when the player touches them, the other to have a score system displayed in game that increases with the pick up items. The way this 
will work is by checking for collisions from the pick up prefab and if it detects the "Player" object then it increase a score system,
play a sound and finally destroy the pick up item.

## Setting Up The Canvas

This tutorial will require the use of the Unity Canvas system to set up the score system that will be displayed on screen. To start
select create inside the Heirarchy > UI > Text. This will automatically create a canvas as well as a Text UI object within that canvas, 
name the new Text object "Score". Select the "Score" object in the Heierarchy and then while having your mouse anywhere within the scene 
view panel press the "F" key which will adjust your scene view to show the new Text object inside the canvas. While still having the object 
selected press "W" to select the transform move tool and move the object around the screen to wherever you prefer, you can also adjust  the 
size, colour, font etc inside the Inspector window, do not forget to increase the width and height of the rect transform component if you 
increase the size of the text so it still displays on screen. Create a script and name it "Score", then drag and drop the script on to the
canvas.

## Score Script

### Using UnityEngine.UI

Open the "Score" script up in Microsoft Visula Studio. This script will not be very long but will provide the neccessary tools to get a functioning
score system, to start we will need to add to collection of systems that is used within this script at the very top. Standard unity C# scripts do not
come with the UI system so we will have to add it in, to do this underneath "using UnityEngine;" type "using UnityEngine.UI;", this will give us access
to UI class based methods, functions etc. If done correctly it should look something like this:

```
using System.Collections;
using System.Collections.Generic;
using UnityEngine.UI;
using UnityEngine;

public class Score : MonoBehaviour
```
### Declaring Variables
