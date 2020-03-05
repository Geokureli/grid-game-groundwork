# Grid Game Groundwork for Unity

A Unity project & level editor for making grid-based/block-pushing/Sokoban-like games.  
Made with Unity 2018.x LTS

## Dependencies:
DOTween by Demigiant  
http://dotween.demigiant.com/  
https://assetstore.unity.com/packages/tools/animation/dotween-hotween-v2-27676

## Setting Up Scenes:
- Add the "GameController" prefab to the scene  
See "Example.unity" (here's a GIF of it in action: http://toboggan.work/images/ggg-demo.gif)

## Using the Editor:
The editor window can be found under "Window" -> "Level Editor".
- Assign any number of prefabs to the "Prefabs" dropdown (then collapse it when done)
- After selecting a game object (prefab), set the "Scene" view to "2D"
- Left-click anywhere in the scene to paint in the selected gameObject
- Hold left-click to paint continuously 

_Note: Selecting "Empty" will clear any objects at that position._

## Deeper Dive:

The project assumes plenty about what kind of game you want to make, but there are no rules about friction or win conditions. There are two main object types that you can use in scenes, Wall and Mover.

I typically make objects derive from the Mover class (as the Player class does). Walls and Movers both need child gameObjects (empty ones or not) tagged with "Tile" which will make up and define its shape. See the prefabs "Crate" and "Crate L" for examples of single-tile and multi-tile Movers.

## Class Breakdown:

### Mover:
Things that can move and fall and that should be tracked for the undo system.

### Wall:
Static things you should not be able to move and that should stop you from moving, including the ground.

### Player:
Derives from Mover, handles character movement input. There should only be one Player in the scene.

### Game:
Manages movers, walls and undo/reset input.

### SaveData:
For saving persistent data, like a list of beaten levels by name/string.

### State:
Tracks the undo stack.

### Utils:
General utilities class

### WaitFor:
For caching yield instructions, borrowed from... somewhere on the internet years ago.

### LevelEditor:
The EditorWindow class (see "Using the Editor" above)
