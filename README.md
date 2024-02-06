# OKeefe-13933-Pong
Controls to use:
<br>
Left Side Up - W
<br>
Left Side Down - S
<br>
Right Side Up - Arrow Up
<br>
Right Side Down - Arrow Down
<br>
<br>
All levels of work completed.
<br>
<br>
<br>
<br>
<br>
B level work completed includes:

!-Create a multiball game mode. We already know how to make the ball spawner create a new ball, so we can do that at any time. Make it happen when the player hits a certain spot on the board.
<br>
<br>
<br>
A level work completed includes:

!!-Make some obstacles that the ball can destroy, but only if it has passed through a certain part of the board yet, and only once per pass. ( Use a boolean for the ondestroy, if on destroy is true, destroy the thing, and turn the bool back off) Make sure the ball can't destroy the side walls. (Use tags)
<br>
<br>
<br>
<br>
<br>
! - The multiball game mode is a separate world found in Content\Dynamic\Maps\PongMultiballLevel. Every 2 seconds, a 'BP_MultiballSpawn' BLueprint will spawn. When hit by a ball it will be destroyed, and then another ball will be spawned. Each ball counts for a point, but only the original ball will spawn another ball upon scoring, the "multi ball" will not.
This is done by first setting a boolean as to whether there is already a rainbow cube spawned. If there isn't it simply spawns one in,f and if there is, it doesn't. It checks the boolean every two seconds. The boolean is toggled on and off respectively.

!! - Also within the multiball game mode, there are destructable objects. There are also holes in the middle of the top and bottom of the walls. When the ball passes through these holes it is destroyed, a new ball is spawned, and a wall is erected in front of their corresponding scoring fields, making it impossible to score on them until it is hit by a ball, which destroys it on contact.
This is done relatively simply, although it takes a bit of thought. The boxes that check if you get the ball into the top or bottom are the same BP as the ones for left and right, so I separated these into a branch and added tags to the boxes. If the boxes have the 'leftRight' tag they score points, and if they don't, then we move on to the 'top' and 'bottom' (respectively) tagged boxes. If the box has the 'top' tag then it turns on the collision and visiblity of the left cube, and vice versa for if it doesn't have that tag. The cubes then have a simple event hit check that turns the collision and visibility off if they are hit, effectively destroying them.
