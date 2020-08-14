# Hello World!

This first world serves not only as an introduction to the DM language,
but to the Dream Maker editor/compiler as well.  Fortunately, the system
has been designed to be quite simple to use, and with just a few steps you
should be on your way to BYOND programming wizardry!

Dream Maker refers to the collection of files comprising the project as the
world **environment**.  When you make a new project, you create a single
environment file, which has the name `[worldname].dme`.  This
file may contain source code, but in general it will only be comprised of
automatically generated references to other files in the project.  This is
best seen by example, so let's stop talking, and get coding!

1. Create the "hello" project by selecting **New Environment...**
from the **File** menu.  This prompts for a directory in which your
project will be stored.  Enter `hello` as the desired
directory.  This creates a new directory called `hello`,
which now contains the `hello.dme` environment file.  Notice that
`hello.dme` also appears in the file tree displayed on the left side
of the screen.  All files in the environment directory are listed there.

2. Let's put the code for this project in a separate file.  Select
**New File...** from the **File** menu.  Choose **Code File**
for the type, and enter `hello` for the name.  This creates a file
called `hello.dm` in the environment directory, and a
corresponding listing in the file tree.  The checkbox next to it indicates
that the code in `hello.dm` will be included in this project.

3. The `hello.dm` file is now ready for editing.  Type the
following code.  (Make sure the first line is not indented, the second is
indented once, and the third is indented twice.  It is easiest to use tabs
for the purpose.)

    mob
        Login()
            world << "Hello, world!"

4. Compile the code by selecting **Compile** from the **Build**
menu.  If there are problems, they will appear in the output box at the
bottom of the screen.  But unless you indented incorrectly, all should
proceed smoothly.

5. Run the compiled world by selecting **Run** from the
**Build** menu.  This launches Dream Seeker, which should subsequently
welcome the world!
***
Consider the Hello World example again.  The DM code says that when a player
logs in, a message should be displayed.  We can do a similar thing for other
types of actions.  For example, if the player types a command, a message
could be displayed.

In DM, commands are called **verbs**.  A verb is defined in the following
example:


	mob
	   verb
	      smile()
		 world << "[usr] grins."

Notice the funny stair-step indentation again!  That will be explained in a
little bit.  For now, read this example from top to bottom.  Once again we
are defining a property of a **mob** (the player's avatar).  In this case
we are adding a **verb**, an action that the player can instruct the mob
to perform.  The name of the verb is **smile**.  The final line displays a
message when the mob smiles.  Notice the `[usr]` in the message; as you
may have guessed, that is not displayed literally but is replaced by the
name of the user, the player who initiates the command.

Run this example.  Once you have logged in, try typing **smile** and
pressing enter.  You should see the grinning message with your login name
substituted into it.  Amazing!  Fantastic!  But playing god is a serious
business.  Don't let anyone catch you grinning.

For variety, you could add some more verbs.  Here are a few:


    mob
        verb
            smile()
                world << "[usr] grins."
            giggle()
                world << "[usr] giggles."
            cry()
                world << "[usr] cries \his heart out."

Now the stair-step pattern has been broken because all three verbs
**smile**, **giggle**, and **cry** are at the same level of
indentation.  In DM, indentation at the beginning of a line serves to group
things together.  Here, **smile**, **giggle**, and **cry** are
all grouped together as verbs belonging to **mob**.  Each of these verbs
has it's own contents indented beneath it.



Notice the use of `\his` in the **cry** verb.  This
macro is replaced by the appropriate possessive pronoun.  It could be
**his**, **her**, **its**, or **their**, depending on the
gender.  DM provides a few other useful macros like this one to make life
easy.



So far nothing has been said (because you never asked) about the empty
parentheses after the verb names in the above examples.  They were in the
first example after `Login` too.  These are the mark of a procedure
definition.  The verbs and `Login` are all examples of procedures,
which are a sequence of instructions to be carried out.  In the examples so
far each procedure consisted of only one line--an instruction to display
some text.  They can, of course, become much more complicated than that.



There are two general categories of procedures: those that show up as player
commands and those that do not.  These are called **verbs** and
**procs** respectively.  By that definition, `Login` in the
**Hello World** example was a proc.



The parentheses after a procedure name are more than decorative.  They can
be used to define procedure parameters.  This allows for providing additional
information to the procedure.  The information is stored in a variable, that
is, a piece of memory with a name.  To confuse matters, a programmer will
often call such variables, which serve as the parameters to procedures,
**arguments**.  Why?  Well, just for the sake of argument.

Here is an example of a verb that takes a parameter--in this case a short
message to be broadcast to the world.


    mob
        verb
            say(msg as text)
                world << "[usr] says, [msg]"

In these few short lines are the bare bones of a chat world.  Users can log
in and start gabbing using the **say** verb.  Try it out.  Your session
might look something like the following:


> say "hello world!"
> Dan says, hello world!

The main point of interest in the DM code is inside the parentheses where
the parameter `msg` is defined.  It could have been called anything; the
variable name is arbitrary.  The statement `as text` indicates that a
short message supplied by the user will be stored in the variable.  This
message is then inserted into the final output at the position marked by the
expression `[msg]`.

So far I have casually introduced mobs, verbs, procs, and arguments.  Now
it is time for a formal (tediously exciting) description of the DM syntax.
It may take several multi-clausal sentences to get through this, so don't
hold your breath.



DM code is structured like a tree.  The top of the tree is called the root.
The various types of virtual objects (mobs being one) branch off of the root
and may in turn give rise to additional strains that branch down from them.

If you haven't noticed, the code tree terminology is upside down.  Of
course, so is the file-system on your hard-drive, and every other
informational tree in existence.  It is quite possible that the vast
majority of computer scientists have never actually seen a real tree.  The
sheer weight of their ignorance keeps the jargon from flipping right side
up, and we are stuck with trees having a root at the top and leaf nodules at
the bottom.  Or it might just be standard obfuscation.  That's why I do it.

It is time for an example.  One particularly interesting type of virtual
object is a `turf`.  It is a building block used to make graphical
maps that players can walk around on.  Suppose we wanted to make a maze.
That would require two types of turfs: floors and walls.  Here's how you
would define them:


    turf
        floor
        wall



All we did was branch two new types of objects off of the basic turf.  One
is called `floor` and the other `wall`.  The terminology of a family
tree is often used to describe the relationship of the various objects
defined here.  Turf is the parent of floor and wall.  The two children are
siblings of each other.  A child inherits all the properties of its parent
and adds some of its own to distinguish it from its siblings.  Both floor
and wall are turfs because they are derived from the turf object type.

To make a maze, we need to specify a few properties of floors and walls:
what they look like and whether you can walk through them.  While we're at
it, the appearance of a player should be defined too.  This is how it is
done:

    turf
        floor
            icon = 'floor.dmi'
        wall
            icon = 'wall.dmi'
            density = 1
    mob
        icon = 'player.dmi'

Several assignments have been made.  These take the form of a variable on
the left-hand side and a value on the right.  In the case of the icons, the
value is the name of an icon file inside single quotes.  In the case of
density, the value should be 1 or 0 to indicate if it is dense or not.  A
dense turf will not allow other dense objects (like mobs) to walk through
them.

