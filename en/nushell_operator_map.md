---
layout: content
title: NuShell Operator Map
prev: NuShell Map To Other Languages
next: END
link_prev: /en/nushell_map.html
link_next: /
---

The idea behind this table is to help you understand how NuShell operators relate to other language operators. We've tried to produce a map of all the nushell operators and what their equivalents are in other languages. Contributions are welcome.

Note: this table assumes Nushell 0.13.1 or later.


| NuShell  | SQL      | .Net LINQ (C#)       | PowerShell             | Bash               |
| -------- | -------- | -------------------- | ---------------------- | ------------------ |
| =        | =        | ==                   | -eq, -is               | -eq                |
| !=       | !=, <>   | !=                   | -ne, -isnot            | -ne                |
| <        | <        | <                    | -lt                    | -lt                |
| <=       | <=       | <=                   | -le                    | -le                |
| >        | >        | >                    | -gt                    | -gt                |
| >=       | >=       | >=                   | -ge                    | -ge                |
| =~       | like     | Contains, StartsWith | -like, -contains       | =~                 |
| !~       | not like | Except               | -notlike, -notcontains | ! <str1> =~ <str2> |
| +        | +        | +                    | +                      | +                  |
| -        | -        | -                    | -                      | -                  |
| *        | *        | *                    | *                      | *                  |
| /        | /        | /                    | /                      | /                  |
| in:      | in       | Contains, StartsWith | -In                    | case in            |
| not-in:  | not in   | Except               | -NotIn                 |                    |
| &&       | and      | &&                   | -And                   | -a, &&             |
| \|\|     | or       | \|\|                 | -Or                    | -o, \|\|           |
