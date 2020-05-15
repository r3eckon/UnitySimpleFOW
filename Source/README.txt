SimpleFOW by Revision3

# Introduction

SimpleFOW is a shader based static 2D fog of war rendering system intended for use with large scale RTS games.

# Getting started

1 - Load the SampleScene scene file located in the SimpleFOW folder.
2 - Hit Play then click on the dark square to place points revealing the background.

This process confirms that the shader is working as expected.

# Usage

To use the shader from scratch : 

1 - Create a new 2D quad mesh and add the fog of war material. You can remove the collider.
2 - Rotate it 180 degrees on the Z axis to make sure UVs are bottom left 0,0 and top right 1,1
3 - Add the FogOfWarShaderControl.cs script component to the object.
4 - Link the game camera that will render the fog of war to the added component.
5 - Specify a maximum amount of reveal points, up to 2047. ( maximum amount of shader array values supported in unity ).

You are now ready to use the FogOfWarShaderControl functions in your own game scripts.
Begin by creating a public variable slot with the FogOfWarShaderControl type, then link your quad to this slot.

Then, for instance, when your game is handling the action of a player building a new map revealing structure : 

1 - Use the AddPoint() function with the world position of the structure to add a map revealing point to the list.
2 - Use the SendPoints() funciton next to send the changes to the shader.

Same thing goes for removing a structure by calling RemovePoint() first then SendPoints().
Remember to pass in WORLD positions, not LOCAL positions. 
Use built in Unity utility functions to turn screen to world coords if needed, like the test code in the update function uses.

You can also change the Range and Scale shader values with SendRange() and SendScale()

Make sure to turn off test mode when using the shader in a project.

The Range and Scale values are used to control the sharpness and look of revealed areas.
A high Range value will force you to use a higher Range value to reveal the same area, but the revealed area will look sharper.

It's possible to add a texture to the fog of war. There is no tiling so you must add a texture that is high resolution enough.

# Support

If you have any issues with this asset feel free to send me an email :

r3eckon@gmail.com