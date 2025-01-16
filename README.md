# MDV_Illumination

The goal of this project is to create a complete level in Unreal Engine, with special emphasis on terrain, materials and lighting. The project consists of a large map with a smaller building. Inside the building, there's a power up that unlocks singposts that guide the player towards an objective, which ends the game.

I have chosen to create an island, with a haunted house as the building. Inside the house, the player must pick up a magic book in order to progress. 

## Landscape

![Island Photo]()

To create the Landscape, I used a Blender project with Perlin noise to generate a heightmap. The map was imported and slightly adjusted using Unreal's landscape tools.

The material for the landscape consists of four layers: a baseline layer of soil, sand for the coastline, snow for the mountaintops and finally gravel for the path guiding the player. The layers were generated using functions to modify the scale based on distance and add random noise, to reduce the tiling effect.

![Generic Material Function]()

![Specific Material Functions]()

![Landscape Material]()

The forest was generated using Unreal's foliage tool. For the sea, I used the experimental Water plugin, with an Ocean Water Body.

The landscape is lit using a directional light along with a Sky Light and Sky Atmosphere. There's also a Volumetric Cloud and an Exponential Height Fog. There's a boundless Post-Processing Volume to make the color temperature slightly warmer and add bloom and lens flares.

![Fork]()

The path in the forest has several forks; once the player has picked up the book inside the house, several signs will appear, pointing the way towards the goal at every intersection.

![Goal]()

Finally, the goal itself is a cyllinder with a glass material. Once the player overlaps with it, the game ends.

## House

![House Exterior]()

The house was generated using Unreal's modelling tools. I deformed it slightly with the displace tool to give the appearance of worn-down wood.

![First Floor]

The house is divided into two floors. On the first floor, there's a table with some props, demonstrating Lumen's indirect reflections. The room is lit with a point light on top of the candle. There's a Post-Processing volume just for this room, greatly increasing the bloom and warming the colors. On the right, there are some stairs, which are lit with another point light coming from the second room.

On the second room, there's another Post-Processing volume, which heavily alters the lighting to make it seem otherworldly. There's a mirror with another light behind it with shadows disabled, to give it a haunted look. In front of the mirror, there's a book with a very small light attached to it. This is the item the player must pick up to unlock the signs guiding the way to the goal.

## Mechanics

The player character and controller is imported from an existing project, using Unreal's free Paragon models. The blueprints have been altered for the game's level; here we'll show only the alterations.

There are four blueprints used for this project: for the player, the haunted book, the signs pointing towards the goal, and the goal itself.

![Countess Blueprint]()

In the player character blueprint, there's an action for picking up the book. The book's blueprint has a larger collider, allowing for the player to overlap with it and interact with the book from nearby. There's also a method for ending the game upon reaching the goal.

![PowerUpBlueprint]()

The Power Up has a simple blueprint that makes it invisible upon activating it and calls an event on each sign making it visible again.

![SignBlueprint]()

The sign starts invisible, and turns visible upon collecting the book.

![GoalBlueprint]()

The goal simply activates the event to end the game when the player overlaps with it.


