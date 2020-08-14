# Navigating the Code Tree

The previous chapter was a quick introduction to give you a taste for DM
programming.  This and the next few chapters will cover the same basic ideas
in greater detail.

A DM program begins at the root of the tree and descends along multiple
branches.  Each branching point (or node) is given a name to distinguish it
from the other branches at the same level.  Names are case-sensitive (so
apple and Apple are different).  They may be any length and may contain any
combination of letters, numbers, and underscores as long as they do not
start with a number.

Consider the following code:

	turf
	   trap
	      pit
	      quicksand
	      glue

Several types of traps are defined (though no instructions have been
included to actually make them work).  Here, each type of object is on a
line by itself and indentation is used to define the relationships between
them.  The three siblings pit, quicksand, and glue are all children of trap,
which is in turn derived from turf, the map terrain object.
