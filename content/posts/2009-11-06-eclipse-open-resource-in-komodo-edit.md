---
title: Eclipse's "Open Resource" in Komodo Edit
date: 2009-11-06T04:09:32+00:00
---

The thing I like about Eclipse is its "Open Resource" shortcut. As an IDE, it's always felt... heavy. I can't seem to get Mint/Eclipse/PHP Developer Tools to play nice, so I'm trying out this new IDE, Komodo Edit. This doesn't work so well with CakePHP, but at least there is code completion.

Now, on to the good stuff. You can duplicate "Open Resource" by creating a project and defining a shortcut:

File -> New -> New Project

Save the file in the root of your project directory. This allows the entire file listing to show up in:

File -> Open -> Go to File...

Finally, define the Ctrl+Shift+R shortcut for it:

Edit -> Preferences -> Key Binding Schemes -> New...

I call mine "Eclipse". OK, that's probably a bad name.

So anyway, the command you want is "Fast Open: Go to File...".

To test if it works, restart the editor, reopen your project, and hit Ctrl+Shift+R.
