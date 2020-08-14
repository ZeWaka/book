# Paths in the Tree

You have already seen how to use a slash to make code more compact.  It is
used to separate a parent and a child node, for example `turf/trap`.
This notation is known as a **path** because it tells the compiler how to
get from the current position in the tree to some other point by enumerating
the branches to take along the way.  If a given branch doesn't exist, it
will be created.

Paths have several uses.  Sometimes indentation can get so deep that it
becomes hard to read.  You can use paths instead to get deep down inside the
tree without indenting so much to get there.  Another time to use a path is
when you want to branch off of existing objects from somewhere else in the
code.

The following example adds some variation to the basic pit that was already
defined.

	turf/trap/pit
	   tar
	   lava
	   bottomless
You could place this code at the bottom (or even the top) of the same file or
in another file.  (You will see how to use multiple files in chapter

Finally, there are a few rare cases in which you may want to use an absolute
path--that is, a path starting with a slash.  This allows you to derive
something from the root even if you are not currently at the root.  Now does
not happen to be one of those rare cases; using an absolute path would only
make the code more confusing.

If you think you know how things work, take a look at this:
	turf {
	   trap {pit; /turf/trap/quicksand}
	   /turf/trap/glue
	}
If you guessed that this is yet another encoding of the same three traps,
you have passed obfuscation level one.
