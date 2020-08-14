# Meet the Dream Maker
DM is a programming language for the creation of multi-user worlds.  By
`world' I mean a virtual multi-media environment where people assume personae
through which they interact with one another and computer-controlled
objects.  This could take the form of a competitive game, a role-playing
adventure, a discussion board, or something we haven't even imagined.

Frequently, the terminology of a role-playing game is most suitable: humans
are PCs (playing characters) and computer-controlled personalities are NPCs
(non-playing characters).  The virtual embodiment of a player is often
called an **avatar**.  The game rules are written in DM and faithfully
carried out by the computer.  These define what actions players may instruct
their avatar to perform, what effect these will have in the game, and any
other events that may happen as time progresses.

To understand the mechanics of the system fully, it is helpful to know a few
simple terms.  Computer programs that operate over a network are often
divided into two parts: a client and a server.  In this case, the client is
the program that players use to enter commands and see what happens as a
result.  In other words, the client handles input and output.  The server is
the program that runs the game, carrying out the rules defined in the DM
language.  The game designer writes these rules in a third program called
the compiler.  This reads the DM program (known as the **source code** by
programmers), checks it for grammatical errors, and generates a more compact,
computer friendly, file known as the **byte code** or **binary**.  It
is this file which the server reads to see how to run the game.

So there are three main programs: the client, server, and compiler.  We call
these Dream Seeker, Dream Daemon, and Dream Maker, respectively.  <small>(The word **daemon** is just another (more fantastical) word for server.)</small>  
As a whole, we refer to this collection of software as BYOND, which stands
for Build Your Own Net Dream--an apt description of its purpose and also of
how far it has wandered **beyond** our original plans.  But that is
another story!


Every introduction to a programming language must begin with the same
example.  Call it destiny, inevitability, or pure chance; it is rather
uncanny that the name of the universal introductory example is **hello
world**.  Spooky, no?  That's exactly what happens in this example--we say
hello to the world.


In DM you write it like this:




    mob
        Login()
            world << "Hello, world!"

If you have any prior programming experience, the last line probably looks
vaguely sensible.  It outputs the text inside the double quotes to the
whole world.  But what on earth is a **mob** and why is each line indented
like stair-steps?  All in good time.  For now, simply understand that the
player's avatar in the game is a **mob**.  When a player logs in, the
server is instructed to output the message "Hello, world" to everybody.


Compile and run this program (see figure <a href="#HelloInterlude">1.1</a>).  If all goes
according to plan, you should see the words, "Hello, world" magically
appear on Dream Seeker's output screen.  Voila!  You have created your first
BYOND world.


Now you know the basic steps for designing worlds.  You write some DM code,
compile it, and run it.  But this world didn't have anything for the player
to do.  That's next.
