# Introduction

Hello, and welcome to the Nushell project. The goal of this project is to take the Unix philosophy of shells, where pipes connect simple commands together, and bring it to the modern style of development.

Nu takes cues from a lot of familiar territory: traditional shells like bash, advanced shells like PowerShell, functional programming, systems programming, and more. But rather than trying to be the jack of all trades, Nu focuses its energy on doing a few things well:

* Create a flexible crossplatform shell for the modern, GitHub-era programmer
* Allow you to mix and match commandline applications with a shell that understands the structure of your data
* Have the level of UX polish that modern CLI apps provide

The easiest way to see what Nu can do is to start with some examples, so let's dive in.

The first thing you'll notice when you run a command like `ls` is that instead of a block of text coming back, you get a structured table.

```
> ls
----+------------------+-----------+----------+----------+----------------+----------------
 #  | name             | type      | readonly | size     | accessed       | modified 
----+------------------+-----------+----------+----------+----------------+----------------
 0  | .azure           | Directory |          | 4.1 KB   | 2 months ago   | a week ago 
 1  | IMG_1291.jpg     | File      |          | 115.5 KB | a month ago    | 4 months ago 
 2  | Cargo.toml       | File      |          | 3.1 KB   | 17 minutes ago | 17 minutes ago 
 3  | LICENSE          | File      |          | 1.1 KB   | 2 months ago   | 2 months ago 
 4  | readonly.txt     | File      | readonly | <empty>  | a month ago    | a month ago 
 5  | target           | Directory |          | 4.1 KB   | 2 days ago     | 15 minutes ago
...
```

The table is more than just showing the directory in a different way. Just like tables in a spreadsheet, this table allows us to work with the data more interactively.

The first thing we'll do is to sort our table by the name. To do this, we'll take the output from `ls` and feed it into a command that can sort tables based on the contents of a column.

```
> ls | sort-by name
----+------------------+-----------+----------+----------+----------------+----------------
 #  | name             | type      | readonly | size     | accessed       | modified 
----+------------------+-----------+----------+----------+----------------+----------------
 0  | .azure           | Directory |          | 4.1 KB   | 2 months ago   | a week ago 
 1  | .cargo           | Directory |          | 4.1 KB   | 2 months ago   | 2 months ago 
 2  | .editorconfig    | File      |          | 148 B    | 2 months ago   | 2 months ago 
 3  | .git             | Directory |          | 4.1 KB   | 2 months ago   | 20 minutes ago 
 4  | .gitignore       | File      |          | 58 B     | a week ago     | a week ago 
 5  | .vscode          | Directory |          | 4.1 KB   | a month ago    | a month ago 
...
```

You can see that to make this work we didn't pass commandline arguments to `ls`. Instead, we used the `sort-by` command that Nu provides to do the sorting of the output of the `ls` command.

Nu provides many commands that can work on tables. For example, we could filter the contents of the `ls` table so that it only shows files over 4 kilobytes:

```
> ls | where size > 4kb
----+----------------+------+----------+----------+----------------+----------------
 #  | name           | type | readonly | size     | accessed       | modified 
----+----------------+------+----------+----------+----------------+----------------
 0  | IMG_1291.jpg   | File |          | 115.5 KB | a month ago    | 4 months ago 
 1  | README.md      | File |          | 11.1 KB  | 2 days ago     | 2 days ago 
 2  | IMG_1291.png   | File |          | 589.0 KB | a month ago    | a month ago 
 3  | IMG_1381.jpg   | File |          | 81.0 KB  | a month ago    | 4 months ago 
 4  | butterfly.jpeg | File |          | 4.2 KB   | a month ago    | a month ago 
 5  | Cargo.lock     | File |          | 199.6 KB | 22 minutes ago | 22 minutes ago
```

Just as in the Unix philosophy, being able to have commands talk to each other gives us ways to mix-and-match in many different combinations. Let's look at a different command:

```
> ps
-----+-------+----------+------+--------------------------------------------------------------------------------
 #   | pid   | status   | cpu  | name 
-----+-------+----------+------+--------------------------------------------------------------------------------
 0   | 1003  | Unknown  | 0.00 |  
 1   | 1515  | Sleeping | 0.00 | /usr/lib/gnome-settings-daemon/gsd-screensaver-proxy 
 2   | 2128  | Sleeping | 0.00 | /usr/lib/gnome-settings-daemon/gsd-screensaver-proxy 
 3   | 2285  | Unknown  | 0.00 |  
 4   | 8872  | Sleeping | 0.00 | /usr/lib/gvfs/gvfsd-dnssd--spawner:1.23/org/gtk/gvfs/exec_spaw/4 
 5   | 1594  | Sleeping | 0.00 | /usr/lib/ibus/ibus-engine-simple
```

You may be familiar with the `ps` command if you've used Linux. With it, we can get a list of all the current processes that the system is running, what their status is, and what their name is. We can also see the CPU load for the process.

What if we wanted to show the processes that were actively using the CPU? Just like we did with the `ls` command earlier, we can also work with the table that the `ps` command gives back to us:

```
ps | where cpu > 10
---+-------+----------+-------+-----------------------------
 # | pid   | status   | cpu   | name 
---+-------+----------+-------+-----------------------------
 0 | 1992  | Sleeping | 44.52 | /usr/bin/gnome-shell 
 1 | 1069  | Sleeping | 16.15 |  
 2 | 24116 | Sleeping | 13.70 | /opt/google/chrome/chrome 
 3 | 21976 | Sleeping | 12.67 | /usr/share/discord/Discord
```

So far, we've seen using `ls` and `ps` to list files and processes. Nu also offers other commands that can create tables of useful information. Next, let's explore `date` and `sys`.

Running `date` gives us information about the current day and time:

```
> date
------+-------+-----+------+--------+--------+----------
 year | month | day | hour | minute | second | timezone 
------+-------+-----+------+--------+--------+----------
 2019 | 8     | 17  | 19   | 20     | 50     | +12:00 
------+-------+-----+------+--------+--------+----------
```

Running `sys` gives information about the system that Nu is running on:

```
> sys
----------+----------+-----------+----------+-----------+-----------
 host     | cpu      | disks     | mem      | temp      | net 
----------+----------+-----------+----------+-----------+-----------
 [object] | [object] | [3 items] | [object] | [3 items] | [3 items] 
----------+----------+-----------+----------+-----------+-----------
```

This is a bit different than the tables we saw before. The `sys` command gives us a table that contains structured tables in the cells instead of simple values. To take a look at this data, we need to select the column to view:

```
> sys | get host
-------+------------------+----------+--------+----------+----------
 name  | release          | hostname | arch   | uptime   | users 
-------+------------------+----------+--------+----------+----------
 Linux | 5.0.0-21-generic | pop-os   | x86_64 | [object] | [1 item] 
-------+------------------+----------+--------+----------+----------
```

The `get` command lets us jump into the contents of a column of the table. Here, we're looking into the "host" column, which contains information about the host that Nu is running on. The name of the OS, the hostname, the CPU, and more. Let's get the name of the users on the system:

```
> sys | get host.users
jonathan   
```

Right now, there's just one user on the system named "jonathan". You'll notice that we can pass a path and not just the name of the column. Nu will take the path and go to the corresponding bit of data in the table.

You might have noticed something else that's different. Rather than having a table of data, we have just the single element: the string "jonathan". Nu works with both tables of data as well as strings. String are an important part of working with commands outside of Nu. 

Let's see how strings work outside of Nu in action. We'll take our example from before and run the external `echo` command, which is built into most OSes:

```
> sys | get host.users | echo $it
jonathan
```

If this looks very similar to what we had before, you have a keen eye! It is similar, but with one important different: we've called `echo` with the value we saw earlier. This allows us to pass data out of Nu into `echo` (or any command outside of Nu, like `git` for example)

