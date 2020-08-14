# The Amazing Mapper

For most programs, adding graphic support is a massive chore.  The
facilities in Dream Maker, however, make this task quite simple.  For our
example, we'll just draw a couple of icons and put them on a map.

<ol>


1. Create a project called `maze` through the **New
Environment...** option.

2. Create the main `maze.dm` file, and enter the following code:


	turf
	  floor
	    icon = 'floor.dmi' 
	  wall
	    icon = 'wall.dmi'
	    density = 1
	mob
	  icon = 'player.dmi'

3. Build the `floor.dmi` icon.  Do this by selecting **New
File...** and choosing **Icon File** for the type.  This will bring up a
new window, with the option to build pixmaps (static, directionless, icons)
and movies (animated or directional icons).  Choose **New Pixmap...**
from the **Graphic** menu and show off your artistic flair by drawing a
picture of a floor.  Repeat this step for the `wall.dmi` and
`player.dmi` icons.

4. With the three icons in place, the project should compile.  Test this
by selecting the **Compile** option.  If it is successful, you should
be able to see your icons in the object tree tab on the left-hand side of
the screen.  This tree illustrates the objects defined in your world.

5. You can run the world now, but you won't see any icons because you
haven't put any objects on the map yet.  To build a map, again select
**New File...** and choose **Map File**.  You can name it whatever
you'd like; the `.dmm` extension will be appended, indicating that
this file is a map.

6. Now for the fun part!  Create the map by selecting objects from the
tree and placing them with the various functions.  For example, to add a row
of walls, select the **Add** function on the map pane, click on the
`wall` tile in the tree (it's underneath `turf`), and draw them on
the map by left-clicking the mouse.  You can remove tiles by
right-clicking.  The map editor has considerable functionality; you can
learn about it by reading the included documentation.

7. Compile the new, graphical project and run it with Dream Seeker.  If
all goes well, you should see your creation on screen.  Your avatar can roam
the floors and bump into the walls.  Not too bad for a couple minutes of
work!

***

The reason we did not have to set the density of the floor to 0 is that the
default density of a turf is 0.  Since the floor is derived from a turf, it
inherits all the default properties of one.  This sort of inheritance of
characteristics is one of the important elements of object-oriented
languages like DM.  Ultimately, it is just a compact way of describing
closely related things.
Before you test this example, you will need to design the icons and the maze
itself.  Fortunately, this process is a natural part of Dream Maker's
functionality.

When you are done making the map, you can compile and test the world.  When
you log in, you should be able to walk around in the maze you designed by
using the arrow keys.  Amazing!

Of course there are always small details that one doesn't think about until
after the fact.  For example, where is the starting point in the maze?  We
never specified, so players are just dumped onto the map in the first
available spot.  Here is one way to do it:

	turf
	   floor
	      icon = 'floor.dmi'
	   start
	      icon = 'start.dmi'
	   wall
	      icon = 'wall.dmi'
	      density = 1
	mob
	   icon = 'player.dmi'
	   Login()
	      loc = locate(/turf/start)

You will have to make a new icon for the `start` turf and then edit the
map to mark the starting position with it.

The code that makes the initial placement of the mob is in the
`Login` proc.  It sets the location of the mob (`loc`) to the
position of the start turf.  This is done by using the `locate()`
instruction--one of the many built-in procedures in DM. It computes the position of an object type (in this
case, the `start` turf).

Notice how the object type `/turf/start` is specified.  This notation is
called a **type path** because of the way you specify the path (starting
from the root) down to the specific type of object you want.

Now suppose you forgot to put a start turf on the map.  What would happen?
The `locate()` instruction would fail and the player would not get
placed on the map and therefore wouldn't even be able to see the maze after
logging in.  A total disaster!  Wouldn't it be nice to fall back on the
default behavior of at least putting the mob somewhere on the map?  In other
words, we have to somehow run the default `Login` proc as well as the
one we defined, just in case there is no start turf.  Here is how to do it:

	mob
	   Login()
	      loc = locate(/turf/start)
	      ..()

The final line does the job.  It invokes a procedure with a strange name:
just two dots.  That is the name DM uses for the default procedure, more
generally known as the parent or super procedure.  In the case of
`Login`, the default proc checks to see if the mob is somewhere
already.  If not, it finds a vacant spot on the map, which is just what we
wanted.

Now you can begin to see the general flavor of DM programming.  There are a
number of events (`Login` being one) which are handled by
procedures.  When necessary, you can override the default procedure with one
of your own to make things work exactly how you want.

This is another important component of object oriented programming.  Each
type of object can respond to events differently.  The way in which they
respond is inherited from their parents by default, but can be redefined
and augmented as needed.

This introduction has just scratched the surface of DM.  You should begin to
see some interesting possibilities.  At the same time, you should have a lot
of unanswered questions.  Keep both of those in mind; they will be your
guide through the more detailed exploration of the language that follows.
