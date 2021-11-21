# Assignment: Cross-Modality UI and Something Fun

In this assignment, you will implement a "fun interactive 3D world" that needs to satisfy a few constraints. As with A2 and A3, you may implement this using any of the 3 environments from Assignment 1 (Babylon.js, Playcanvas Editor, or Playcanvas Engine).  You may reuse any of your code from previous assignments. This template is empty (except for a .gitignore file and this README.md);  you should fill in the project with something similar to 1(a), 1(b), or 1(c) and follow the corresponding instructions for submission.

The goals of the assignment are to 
- implement a simple UI that works reasonably in both desktop 3D and VR (details below),
- implement the VR menu so it "lazily" follows the user's view when visible (details below), and
- have the UI change the scene contents/behaviors and how the user interacts (details below).

What the scene is, how it behaves, and what the user can do in it are up to you.  There are some guidelines and constraints you should satisfy (laid out below and in the rubric) but you are encouraged to do something you find interesting.

## Due: Sunday  11:59pm (midnight)

## Name and GT user-id

Name: 
User ID:
Playcanvas Username (if appropriate): 

## Instructions for Use and Credits

(Fill in a description of you application, how to use it and see what you have created)

(Provide pointers to all resources you used, both for code and models and sounds.  You are allowed to use code from the Playcanvas and Babylon examples and public projects and integrate it into your project, if you document what you got where.)

## Additional Details 

There are two parts to consider: the menu, and the scene.

### Menu Behavior

All of the 2D UI for this application should fit within a single 2D panel.  In both the 2D view and the VR view, it should be possible to summon and dismiss the menu.

*2D View.*  When the web page loads in the browser in 2D, a small button labeled "Menu" should be on the top edge of the screen, horizontally in the middle of the screen. Clicking it causes the menu to appear in the middle of the screen.  Clicking it again dismisses the menu.  When the window is resized, the button's position and the menu position should be adjusted appropriately (to remain in the middle).  You should be able to interact with the menu appropriately.  The menu should be in the 2D screen menu area that Playcanvas and Babylon support.

*VR View.*  When in VR, the menu should be bound to one of the buttons on one of the controllers (Y on the Quest, the left small menu button on Windows MR).  When the button is pressed, the menu should appear in the middle of the screen;  when the menu is visible, pressing the button will hide it.  The challenge of this part of the assignment is that when the menu is visible, if the user looks away from it such that it goes off screen, it should slide into view again, smoothly rotating around the user.  An example of this behavior is the Windows MR system menu, shown here:

![Windows MR system menu](resources/WindowsMR-menu.gif)

In this example, notice that the menu stays in the same pace when the user looks a small amount to the left right, up and down.  But when the user looks further, such that the menu starts to go off screen, the menu rotates around the user back to the center of the screen.

Using this video as a starting point, you should implement this behavior as follows:
- when you press the button to make the menu appear, it can simply appear in the center of the screen, it does not need to slide in from the bottom.
- you can decide how soon you want the menu to move.  The behavior here is probably the soonest you should move it; as soon as the menu hits the edge of the screen, it slides back on. You may wait until the menu is further off screen, and you can also wait a slightly longer time before moving it back.  The tradeoff is stability of the menu, and the ability for the user to look away briefly before the menu moves.
- the menu panel should be sized such that it takes up a reasonable amount of the screen, when positioned a meter or two in front of the user. It should be positioned along the ray from the user's head at that distance, looking at the user (oriented such that "up" is reasonable).
- once the menu is positioned, if it stays visible because the user keeps looking at it, it rotates to face the user as the user moves around (e.g., the look-at orientation is recomputed each frame).
- when the the menu is moved, you should compute it's new target position, and animate it's position and orientation to the new position and orientation smoothly over a short time.  You do not want to have to change it's target position until it stops moving, so this animation should be short.
- you could use the built in methods of Babylon and Playcanvas to see if the object is within the view frustum, but it is probably simpler to just look at the angle between the current view vector and the vector to the center of the panel to decide if it's "out of view". 
- you do not need to worry about if the menu is obscured by the ground or other objects; assume the user will look a different direction if the menu is obscured.

### Application Content

Your application should implement some experience or toy or application you find interesting.  It can be relatively simple, and could include a wide variety of content and interactions, at your discretion.

At a minimum, you should be able to create at least two kinds of content, and have at least one manipulation of existing content.  Your scene should be completely immersive;  it should cover the full visual field (skybox if the sky is visible, ground, objects, lights, background sounds if appropriate).

Examples of what you might do:
- create a holiday scene for one of the upcoming holidays (Thanksgiving, Christmas, Channuka, etc.).  A Christmas scene might include falling snowflakes, Christmas music, a snow-covered outdoor scene or a traditional indoor scene.  Interactions could include throwing snowballs that explode into bursts of particles when they hit something, placing snowmen outside or presents inside, etc.  
- create a celebration of your favorite times at GT, with GT-themed objects, music, and scenery.  The Architecture school has models of parts of campus that could be used. Interactions could interacting with slideshows and videos, or other meaningful objects.

The menu should contain buttons to change the actions you perform (e.g., switching between what objects you are placing if appropriate, erase all placed objects, restart slide shows, etc).

In Desktop 3D, you can move around with whatever camera you want (either staying on the ground, or flying in any direction) and you should be able to interacting with the mouse.  In VR, you can also use whatever movement you prefer, teleporting or sliding with the controller.

Make sure you fill in the description above.  And please note the comment about sources and using other projects as code resources.  You are allowed, in this assignment, to use code that you find in other places to implement the application and any (even elaborate) content and interactions, as long as you document them.  **You should, however, implement the main menu behavior above by yourself.**

## Rubric

Graded out of 100.

1. Your project runs locally using `npm run start` (1)
2. Menu appears and disappears appropriately on the desktop (1)
3. Menu and button reposition appropriately when the window resizes (1)
4. Menu appears in the center of the VR view when you hit the button (1)
5. Menu does not move if it remains on the screen (within a reasonable area) (1)
6. Menu moves smoothly to center of view after being outside of the central area for some amount of time (2)
7. Implement a coherent, consistently themed, application (3)
8. Have 1 interesting interaction that can be performed by the user (1)
9. Have 2 kinds of content the user can create (2)
10. Can move and interact in both desktop and VR modes (2)

Up to 2 bonus points will be awarded for particularly compelling applications and content.

# Collaboration

You are free to discuss technical questions and issues in the Teams channels, but the code you submit should be your own. So, please do not post large chunks of code, but providing pointers to examples or documentation pages or components and methods, along with discussion of how to use them, is fine.  Pointers to resources you are using is fine, too.

# Submission

You will submit your assignment based on the instructions in 1(a), 1(b), or 1(c) (depending on if you used Babylon, Playcanvas Editor, or Playcanvas Engine, respectively.)

## License

<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">Material for 3D User Interfaces Fall 2020</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="https://github.blairmacintyre.me/3dui-class-f20" property="cc:attributionName" rel="cc:attributionURL">Blair MacIntyre</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/">Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License</a>.

The intent of choosing (CC BY-NC-SA 4.0) is to allow individuals and instructors at non-profit entities to use this content.  This includes not-for-profit schools (K-12 and post-secondary). For-profit entities (or people creating courses for those sites) may not use this content without permission (this includes, but is not limited to, for-profit schools and universities and commercial education sites such as Corsera, Udacity, LinkedIn Learning, and other similar sites).   
