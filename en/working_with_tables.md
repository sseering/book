# Working with tables

One of the common ways of seeing data in Nu is through a table. Nu comes with a number of commands for working with tables to make it convenient to find what you're looking for, and for narrowing the data to just what you need.

To start off, let's get a table that we can use:

```
> ls
---+---------------+------+----------+---------+------------+------------
 # | name          | type | readonly | size    | accessed   | modified 
---+---------------+------+----------+---------+------------+------------
 0 | add.rs        | File |          | 2.7 KB  | 2 days ago | 2 days ago 
 1 | sum.rs        | File |          | 3.0 KB  | 2 days ago | 2 days ago 
 2 | inc.rs        | File |          | 11.8 KB | 2 days ago | 2 days ago 
 3 | str.rs        | File |          | 21.4 KB | 2 days ago | 2 days ago 
 4 | skip.rs       | File |          | 1.7 KB  | 2 days ago | 2 days ago 
 5 | textview.rs   | File |          | 9.4 KB  | 2 days ago | 2 days ago 
 6 | binaryview.rs | File |          | 13.0 KB | a day ago  | a day ago 
 7 | edit.rs       | File |          | 2.7 KB  | 2 days ago | 2 days ago 
 8 | tree.rs       | File |          | 3.0 KB  | 2 days ago | 2 days ago 
 9 | sys.rs        | File |          | 9.2 KB  | 2 days ago | 2 days ago 
---+---------------+------+----------+---------+------------+------------
```

## Sorting the data

We can sort a table by calling the `sort-by` command and telling it which columns we want to use in the sort. Let's say we wanted to sort our table by the size of the file:

```
> ls | sort-by size
---+---------------+------+----------+---------+------------+------------
 # | name          | type | readonly | size    | accessed   | modified 
---+---------------+------+----------+---------+------------+------------
 0 | skip.rs       | File |          | 1.7 KB  | 2 days ago | 2 days ago 
 1 | add.rs        | File |          | 2.7 KB  | 2 days ago | 2 days ago 
 2 | edit.rs       | File |          | 2.7 KB  | 2 days ago | 2 days ago 
 3 | sum.rs        | File |          | 3.0 KB  | 2 days ago | 2 days ago 
 4 | tree.rs       | File |          | 3.0 KB  | 2 days ago | 2 days ago 
 5 | sys.rs        | File |          | 9.2 KB  | 2 days ago | 2 days ago 
 6 | textview.rs   | File |          | 9.4 KB  | 2 days ago | 2 days ago 
 7 | inc.rs        | File |          | 11.8 KB | 2 days ago | 2 days ago 
 8 | binaryview.rs | File |          | 13.0 KB | a day ago  | a day ago 
 9 | str.rs        | File |          | 21.4 KB | 2 days ago | 2 days ago 
---+---------------+------+----------+---------+------------+------------
```

We can sort a table by any column that can be compared. For example, we could also have sorted the above using the "name", "accessed", or "modified" columns.

## Selecting the data you want

We can select data from a table by choosing to select specific columns or specific rows.  Let's pick a few columns from our table to use:

```
> ls | pick name size
---+---------------+---------
 # | name          | size 
---+---------------+---------
 0 | add.rs        | 2.7 KB 
 1 | sum.rs        | 3.0 KB 
 2 | inc.rs        | 11.8 KB 
 3 | str.rs        | 21.4 KB 
 4 | skip.rs       | 1.7 KB 
 5 | textview.rs   | 9.4 KB 
 6 | binaryview.rs | 13.0 KB 
 7 | edit.rs       | 2.7 KB 
 8 | tree.rs       | 3.0 KB 
 9 | sys.rs        | 9.2 KB 
---+---------------+---------
```

This helps to create a table that's more focused on what we need.  Next, let's say we want to only look at the 5 smallest files in this directory:

```
> ls | sort-by size | first 5
---+---------+------+----------+--------+------------+------------
 # | name    | type | readonly | size   | accessed   | modified 
---+---------+------+----------+--------+------------+------------
 0 | skip.rs | File |          | 1.7 KB | 2 days ago | 2 days ago 
 1 | add.rs  | File |          | 2.7 KB | 2 days ago | 2 days ago 
 2 | edit.rs | File |          | 2.7 KB | 2 days ago | 2 days ago 
 3 | sum.rs  | File |          | 3.0 KB | 2 days ago | 2 days ago 
 4 | tree.rs | File |          | 3.0 KB | 2 days ago | 2 days ago 
---+---------+------+----------+--------+------------+------------
```

You'll notice we first sort the table by size to get to the smallest file, and then we use the `first 5` to return the first 5 rows of the table.

You can also `skip` rows that you don't want.  Let's skip the first two of the 5 rows we returned above:

```
> ls | sort-by size | first 5 | skip 2
---+---------+------+----------+--------+------------+------------
 # | name    | type | readonly | size   | accessed   | modified 
---+---------+------+----------+--------+------------+------------
 0 | edit.rs | File |          | 2.7 KB | 2 days ago | 2 days ago 
 1 | sum.rs  | File |          | 3.0 KB | 2 days ago | 2 days ago 
 2 | tree.rs | File |          | 3.0 KB | 2 days ago | 2 days ago 
---+---------+------+----------+--------+------------+------------
```

We've narrowed it to three rows we care about.

Let's look look at a few other commands for selecting data.  You may have wondered why the rows of the table are numbers. This acts as a handy way to get to a single row.  Let's sort our table by the file name and then pick one of the rows with the `n-th` command using its row number:

```
> ls | sort-by name
---+---------------+------+----------+---------+------------+------------
 # | name          | type | readonly | size    | accessed   | modified 
---+---------------+------+----------+---------+------------+------------
 0 | add.rs        | File |          | 2.7 KB  | 2 days ago | 2 days ago 
 1 | binaryview.rs | File |          | 13.0 KB | a day ago  | a day ago 
 2 | edit.rs       | File |          | 2.7 KB  | 2 days ago | 2 days ago 
 3 | inc.rs        | File |          | 11.8 KB | 2 days ago | 2 days ago 
 4 | skip.rs       | File |          | 1.7 KB  | 2 days ago | 2 days ago 
 5 | str.rs        | File |          | 21.4 KB | 2 days ago | 2 days ago 
 6 | sum.rs        | File |          | 3.0 KB  | 2 days ago | 2 days ago 
 7 | sys.rs        | File |          | 9.2 KB  | 2 days ago | 2 days ago 
 8 | textview.rs   | File |          | 9.4 KB  | 2 days ago | 2 days ago 
 9 | tree.rs       | File |          | 3.0 KB  | 2 days ago | 2 days ago 
---+---------------+------+----------+---------+------------+------------

> ls | sort-by name | nth 5
--------+------+----------+---------+------------+------------
 name   | type | readonly | size    | accessed   | modified 
--------+------+----------+---------+------------+------------
 str.rs | File |          | 21.4 KB | 2 days ago | 2 days ago 
--------+------+----------+---------+------------+------------
```

## Getting data out of a table

So far, we've worked with tables by trimming the table down to only what we need. Sometimes we may want to go a step further and only look at the values in the cells themselves rather than taking a whole column. Let's say, for example, we wanted to only get a list of the names of the files. For this, we use the `get` command:

```
> ls | get name
---+---------------
 # | value 
---+---------------
 0 | add.rs 
 1 | sum.rs 
 2 | inc.rs 
 3 | str.rs 
 4 | skip.rs 
 5 | textview.rs 
 6 | binaryview.rs 
 7 | edit.rs 
 8 | tree.rs 
 9 | sys.rs 
---+---------------
```

We now have the values for each of the filenames.

This might look like the `pick` command we saw earlier, so let's put that here as well to compare the two:

```
> ls | pick name
---+---------------
 # | name 
---+---------------
 0 | add.rs 
 1 | sum.rs 
 2 | inc.rs 
 3 | str.rs 
 4 | skip.rs 
 5 | textview.rs 
 6 | binaryview.rs 
 7 | edit.rs 
 8 | tree.rs 
 9 | sys.rs 
---+---------------
```

These look very similar! Let's see if we can spell out the difference between these two commands to make it clear:

* `pick` - creates a new table which includes only the columns specified
* `get` - returns the values inside the column specified

The one way to tell these apart looking at the table is the characteristic `value` column name, which lets us know that this is going to be a list of values we can work with.

The `get` command can go one step further and take a path to data deeper in the table. This simplifies working with more complex data, like the structures you might find in a .json file.

## Changing data in a table

In addition to selecting data from a table, we can also update what the table has. We may want to add new columns, or edit the contents of a cell. In Nu, rather than editing in place, each of the commands in the section will return a new table in the pipeline.

### Adding a new column

We can use the `add` command to add a new column to the table. Let's look at an example:

```
> open rustfmt.toml
---------
 edition 
---------
 2018 
---------
```

Let's add an column called "next_edition" with the value 2021:

```
> open rustfmt.toml | add next_edition 2021
---------+--------------
 edition | next_edition 
---------+--------------
 2018    | 2021 
---------+--------------
```

Notice that we if open the original file, the contents have stayed the same:

```
> open rustfmt.toml
---------
 edition 
---------
 2018 
---------
```

Changes in Nu are functional changes, meaning that they work on the values themselves rather than trying to cause a permanent change. This lets us do many different types of work in our 
pipeline until we're ready to write out the result with any changes we'd like if we choose to. Here we could write out the result using the `save` command:

```
> open rustfmt.toml | add next_edition 2021 | save rustfmt2.toml
/home/jonathan/Source/nushell(master)> open rustfmt2.toml
---------+--------------
 edition | next_edition 
---------+--------------
 2018    | 2021 
---------+--------------
```

### Editing a column

Similarly to the `add` command, we can also use the `edit` command to change the contents of a column to a new value. To see it in action let's open the same file:

```
open rustfmt.toml
---------
 edition 
---------
 2018 
---------
```

And now, let's update the edition to point at the next edition we hope to support:

```
> open rustfmt.toml | edit edition 2021
---------
 edition 
---------
 2021 
---------
```

### Incrementing values

There's one more command that Nu supports that will help us work with numbers and versions: `inc`. 

```
> open rustfmt.toml
---------
 edition 
---------
 2018 
---------
> open rustfmt.toml | inc edition
---------
 edition 
---------
 2019 
---------
```

Because the value in "edition" is a number, we can use `inc` to update it.  Where `inc` really shines is working with versions:

```
> open Cargo.toml | get package.version
0.1.3
> open Cargo.toml | inc package.version --minor | get package.version
0.2.0
```

When working with versions, we can use the flag to say how to increment the version:

* **--major** - increment the major version (0.1.3 -> 1.0.0)
* **--minor** - increment the minor version (0.1.3 -> 0.2.0)
* **--patch** - increment the patch version (0.1.3 -> 0.1.4)
