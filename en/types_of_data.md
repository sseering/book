# Types of data

Traditionally, Unix shell commands have communicated with each others using strings of text. One command would output text via standard out (often abbreviated 'stdout') and the other would read in text via standard in (or 'stdin'). In this way, the two commands could communicate.

We can think of this kind of communication as string-based.

Nu embraces this approach for its commands and grows it to include other kinds of data.  Currently, Nu supports two kinds of data types: simple and structured.

## Simple data

Like many programming languages, Nu models data using a set of simple and structured data types. Simple data types include integers, floats, strings, booleans, dates, and paths. It also includes a special type for filesizes.

### Integers

Integers (or round) numbers. Examples include 1, 5, and 100.

### Floats

Floating point numbers are numbers with some fractional component. Examples include 1.5, 2.0, and 15.333.

### Strings

Strings are the fundamental way of representing text. They are quoted using double quotes. Examples include "Fred", "myname.txt", and "Lynchburg, VA".

Strings in Nu are Unicode aware by default, so you can pass UTF-8 text with ease.

### Booleans

Booleans are the state of being true or false. Rather than writing the value directly, it is often a result of a comparison.

### Dates

Dates and times are held together in the Date value type. Date values used by the system are timezone-aware, and by default use the UTC timezone.

### Paths

Paths are a platform-independent way of representing a filepath in the given OS. Examples include /usr/bin and C:\Users\file.txt.

### Bytes

Filesizes are held in a special integer type called bytes. Examples include 100, 15kb, and 100mb.

## Structured data

Structured data builds from the simple data. For example, instead of a single integer, structured data gives us a way to represent multiple integers in the same value. Here's a list of the currently supported structured data types: objects, binary data, lists, and blocks.

### Objects

The object data type represents what you would see in one row of data in the table. It has different elements of data, and each element of data is given a column name.

### Binary data

Binary data, like the data from an image file, is a group of raw bytes.

### Lists

Lists can hold more than one value. This allows them to be a good container for rows of data in a table.

### Blocks

Blocks represent a block of code in Nu. For example, in the command `where { $it.size > 10kb }` the block is the portion contained in curly braces, `{ $it.size > 10kb }`. Blocks are a useful way of representing code that can be executed on each row of data.

