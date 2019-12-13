---
layout: content
title: Moving around your system
prev: Introduction
next: Types of data
link_prev: /en/introduction.html
link_next: /en/types_of_data.html
---

Early shells allow you to move around your filesystem and run commands, and modern shells like Nu allow you to do the same. Let's take a look at some of the common commands you might use when interacting with your system.

## Viewing directory contents

```
> ls
```

As we've seen in other chapters, `ls` is a command for viewing the contents of a path. Nu will return the contents as a table that we can use.

The `ls` command also takes an optional argument, to change what you'd like to view.  For example, we can list the files that end in ".txt"

```
> ls *.txt
---+--------------+------+----------+---------+--------------+--------------
 # | name         | type | readonly | size    | accessed     | modified 
---+--------------+------+----------+---------+--------------+--------------
 0 | history.txt  | File |          | 1.3 KB  | 2 months ago | a day ago 
 1 | readonly.txt | File | readonly | <empty> | 2 months ago | 2 months ago 
---+--------------+------+----------+---------+--------------+--------------
```

The asterisk (\*) in the above optional argument "\*.txt" is sometimes called a wildcard or a glob. It lets us match anything. You could read the glob "\*.txt" as "match any filename, so long as it ends with '.txt' "

Nu also uses modern globs as well, which allow you access to deeper directories.

```
> ls **/*.rs
-----+-----------------------------------------------------+------+----------+----------+----------------+----------------
 #   | name                                                | type | readonly | size     | accessed       | modified 
-----+-----------------------------------------------------+------+----------+----------+----------------+----------------
 0   | src/cli.rs                                          | File |          | 19.1 KB  | 15 hours ago   | 15 hours ago 
 1   | src/commands/args.rs                                | File |          | 244 B    | 2 months ago   | 2 months ago 
 2   | src/commands/autoview.rs                            | File |          | 2.5 KB   | 15 hours ago   | 15 hours ago 
 3   | src/commands/cd.rs                                  | File |          | 277 B    | a week ago     | a week ago 
 4   | src/commands/classified.rs                          | File |          | 13.5 KB  | 15 hours ago   | 15 hours ago 
 5   | src/commands/clip.rs                                | File |          | 2.0 KB   | 2 days ago     | 2 days ago
 ```
 
 Here we're looking for any file that ends with ".rs", and the two asterisks further say "in any directory starting from here".

## Changing the current directory

```
> cd new_directory
```

To change from the current directory to a new one, we use the `cd` command. Just as in other shells, we can use either the name of the directory, or if we want to go up a directory we can use the `..` shortcut.

## Filesystem commands

Nu also provides some basic filesystem commands that works cross-platform. 

We can move an item from one place to another using the `mv` command:

```
> mv item location
```

We can copy an item from one location to another:

```
> cp item location
```

We can remove an item:

```
> rm item
```

The three commands also can use the glob capabilities we saw earlier with `ls`.

Finally, we can create a new directory using the `mkdir` command:

```
> mkdir new_directory
```

