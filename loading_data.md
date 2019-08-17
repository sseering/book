# Loading data

Earlier we saw how you can use commands like `ls`, `ps`, `date`, and `sys` to load information about your files, processes, time of date, and the system itself. Each command gives us a table of information that we can explore. There are other ways we can load in a table of data to work with.

## Opening files

One of Nu's most powerful assets in working with data is the `open` command. It is a multi-tool that can work with a number of different data formats. To see what this means, let's try opening a json file:

```
> open lark/editors/vscode/package.json
------+----------+----------+---------+---------+----------+----------+----------+----------+----------+----------+----------+----------+----------+----------
 name | descript | author   | license | version | reposito | publishe | categori | keywords | engines  | activati | main     | contribu | scripts  | devDepen 
      | ion      |          |         |         | ry       | r        | es       |          |          | onEvents |          | tes      |          | dencies 
------+----------+----------+---------+---------+----------+----------+----------+----------+----------+----------+----------+----------+----------+----------
 lark | Lark     | Lark     | MIT     | 1.0.0   | [object] | vscode   | [0       | [1 item] | [object] | [1 item] | ./out/ex | [object] | [object] | [object] 
      | support  | develope |         |         |          |          | items]   |          |          |          | tension  |          |          |  
      | for VS   | rs       |         |         |          |          |          |          |          |          |          |          |          |  
      | Code     |          |         |         |          |          |          |          |          |          |          |          |          |  
------+----------+----------+---------+---------+----------+----------+----------+----------+----------+----------+----------+----------+----------+----------
```

## Opening URLs

## Working with external commands


