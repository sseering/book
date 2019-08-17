# Shells in shells

## Working in multiple directories

While it's common to work in one directory, it can be handy to work in multiple places at the same time. For this, Nu offers the concept of "shells". As the name implies, they're a way of running multiple shells in one, allowing you to quickly jump between working directories and more.

To get started, let's enter a directory. 

```
> enter ../lark
/home/jonathan/Source/lark(master)> ls
----+----------------+-----------+----------+---------+---------------+---------------
 #  | name           | type      | readonly | size    | accessed      | modified 
----+----------------+-----------+----------+---------+---------------+---------------
 0  | Cargo.toml     | File      |          | 2.2 KB  | 6 months ago  | 6 months ago 
 1  | target         | Directory |          | 4.1 KB  | 10 months ago | 6 months ago 
 2  | notes          | Directory |          | 4.1 KB  | 10 months ago | 6 months ago
```

Entering is similar to changing directories (as we saw with the `cd` command). This allows you to jump into a directory to work in it. Instead of changing the directory, we now are in two directories. To see this more clearly, we can use the `shells` command to list the current directories we have active:

```
> shells
---+---+------------+-------------------------------
 # |   | name       | path 
---+---+------------+-------------------------------
 0 |   | filesystem | /home/jonathan/Source/nushell 
 1 | X | filesystem | /home/jonathan/Source/lark 
---+---+------------+-------------------------------
```

The `shells` command shows use there are two shells currently active: our original "nushell" source directory and now this new "lark" directory.

We can jump between these shells with the `n` and `p` shortcuts, short for "next" and "previous":

```
/home/jonathan/Source/lark(master)> n
/home/jonathan/Source/nushell(master)> p
/home/jonathan/Source/lark(master)>
```

We can see the directory changing, but we're always able to get back to a previous directory we were working on. This allows us to work in multiple directories in the same session.

## Exiting the shell

You can leave a shell you have `enter`ed using the `exit` command. If this is the last open shell, Nu will quit.

You can always quit Nu, even if multiple shells are active, using the `exit --now` command.

## Going beyond directories

Nu can also create shells from other things aside from paths in a filesystem. Let's say, for example, you're working with a large data set and don't want to lose your place inside of it.

To see how this works, let's `enter` a file instead of a directory:

```
> enter Cargo.toml
/> ls
------------+--------------+------------------+----------+----------
 bin        | dependencies | dev-dependencies | lib      | package 
------------+--------------+------------------+----------+----------
 [11 items] | [object]     | [object]         | [object] | [object] 
------------+--------------+------------------+----------+----------
```

What we're looking for might be inside of the "bin" column. So let's go into there:

```
> cd bin
/bin> ls
----+----------------------+---------------------------
 #  | name                 | path 
----+----------------------+---------------------------
 0  | nu_plugin_inc        | src/plugins/inc.rs 
 1  | nu_plugin_sum        | src/plugins/sum.rs 
 2  | nu_plugin_add        | src/plugins/add.rs 
 3  | nu_plugin_edit       | src/plugins/edit.rs 
 4  | nu_plugin_str        | src/plugins/str.rs 
 5  | nu_plugin_skip       | src/plugins/skip.rs 
 6  | nu_plugin_sys        | src/plugins/sys.rs 
 7  | nu_plugin_tree       | src/plugins/tree.rs 
 8  | nu_plugin_binaryview | src/plugins/binaryview.rs 
 9  | nu_plugin_textview   | src/plugins/textview.rs 
 10 | nu                   | src/main.rs 
----+----------------------+---------------------------
```

From here, we can always jump back to the directory we were working in before using `p` (for previous). Let's track down those plugins:

```
> cd src/plugins/
/home/jonathan/Source/nushell/src/plugins(master)> ls
----+---------------+------+----------+---------+------------+------------
 #  | name          | type | readonly | size    | accessed   | modified 
----+---------------+------+----------+---------+------------+------------
 0  | sum.rs        | File |          | 3.0 KB  | a week ago | a week ago 
 1  | inc.rs        | File |          | 11.8 KB | a week ago | a week ago 
 2  | sys.rs        | File |          | 9.2 KB  | 2 days ago | 2 days ago 
 3  | edit.rs       | File |          | 2.7 KB  | a week ago | a week ago 
 4  | str.rs        | File |          | 21.4 KB | 5 days ago | 5 days ago 
 5  | secret.rs     | File |          | 1.8 KB  | 2 days ago | 2 days ago 
 6  | skip.rs       | File |          | 1.7 KB  | a week ago | a week ago 
 7  | binaryview.rs | File |          | 13.0 KB | a week ago | a week ago 
 8  | tree.rs       | File |          | 3.0 KB  | a week ago | a week ago 
 9  | add.rs        | File |          | 2.7 KB  | a week ago | a week ago 
 10 | textview.rs   | File |          | 9.4 KB  | 5 days ago | 5 days ago 
----+---------------+------+----------+---------+------------+------------
```

We can now compare the two to see if there are any missing or additional plugins we need to add to our file.
