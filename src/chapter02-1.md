# Formatting Code

DM provides some flexibility in the way code is formatted.  For example,
blank lines may be inserted between other lines without effect.  This may
help code from getting too dense and unreadable.

To compress code that is overly spread out, a semicolon may be used in place
of a newline.  In this way, several children may reside on the same line.
To put a parent and child on the same line, a slash is used.  It is
equivalent to a newline followed by an additional level of indentation.

The following code is equivalent to the previous example:


	turf/trap
	   pit; quicksand; glue

In addition, braces may be used to mark the beginning and ending of a node's
children.  C, C++, and Java programmers may feel more at home using this
style.  With the compiler checking both braces and indentation, it is hard
for simple mistakes to slip through unnoticed.  Sometimes it is the simple
spelling and typesetting errors which are the hardest to see.

Here is yet another encoding of the same objects, this time using braces:


	turf/trap
	{
	   pit
	   quicksand
	   glue
	}

You may use either tabs or spaces in any number to indent your code.  The
only requirement is that you be consistent.  Each block of code must use the
same type of indentation throughout.  In general, DM provides enough freedom
to format your code the way you like without so much freedom that mistakes
are likely to slip through unnoticed.
