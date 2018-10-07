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
