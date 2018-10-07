# Setting up data to be portable

What we mean by &ldquo;portable&rdquo; here is creating a data organization
scheme that can be used on the workstation in your lab, on your laptop, and
on a cluster that will enable you to write analysis scripts that can be
used on all of those systems with the least modification.

Every time you modify a script (or any other file), it is an opportunity to
introduce an error.  So, we think that it is good practice to set up your
data and your scripts so that, when a change is needed, the least amount
of text is changed, and that the text that changes is in as few places as
possible.

## How this relates to data organization

Directory (or folder, they are synonyms) organization differs from system
to system.  Suppose that your login name is `grundoon`.  If you have an
account on a Mac OS X computer, your home directory is probably
`/Users/grundoon`, whereas if you have an account on a Linux machine, it
is probably `/home/grundoon`.  If you put your data into your home
directory on your Mac, then write a bunch of scripts using `/Users/grundoon`,
when you need to run it on the Linux machine, you have to change every
instance of `/Users/grundoon` in all your scripts to `/home/grundoon`.

What we propose is to use _symbolic links_ to create a pseudo-directory
that can be used when writing your scripts than can be set up easily on
any computer that supports them, which would include at least Linux,
OS X, and Cygwin.  To understand how this works, and why it is useful,
you need to understand what a symbolic link is and how it works.

### How symbolic links work

Normally, when you ask a program to open a file, it finds the file in
the directory table, which provides the program with a disk location,
the program then requests access to that location, and once that is
granted, it reads the file.

A symbolic link is a special kind of file that adds an additional step
to the process outlined above.  The contents of the symbolic link is
the name of a file.  When a program asks to open a file that is a 
symbolic link, the operating system doesn't open the link, but instead
reads the file name contained in the symbolic link, looks that up
in the directory table for whatever file it is, and then continues
with the process above.

### Why this is useful

We can use a combination of directories and symbolic links to create
a data organization that is the same on many computers regardless of
which folders the data really live in, and we can do this by using the
symbolic links in our programs and changing the contents of the
symbolic links to point to where on each particular system the data
really lives; that is, the system-specific directories.

To move your analysis from one system to another, you copy the data
to the new system, create the directories that contain the symbolic
links, and put the data directory names for the new system into the
new symbolic links.  An example will help you see what this means.

