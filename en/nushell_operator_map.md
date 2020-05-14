---
layout: content
title: NuShell operator map
prev: Functional map
next: END
link_prev: /en/nushell_map_functional.html
link_next: /
---

The idea behind this table is to help you understand how NuShell operators relate to other language operators. We've tried to produce a map of all the nushell operators and what their equivalents are in other languages. Contributions are welcome.

Note: this table assumes Nushell 0.13.1 or later.


| NuShell  | SQL      | Python              | .Net LINQ (C#)       | PowerShell             | Bash               |
| -------- | -------- | --------------------| -------------------- | ---------------------- | ------------------ |
| ==       | =        | ==                  | ==                   | -eq, -is               | -eq                |
| !=       | !=, <>   | !=                  | !=                   | -ne, -isnot            | -ne                |
| <        | <        | <                   | <                    | -lt                    | -lt                |
| <=       | <=       | <=                  | <=                   | -le                    | -le                |
| >        | >        | >                   | >                    | -gt                    | -gt                |
| >=       | >=       | >=                  | >=                   | -ge                    | -ge                |
| =~       | like     | re, in, startswith  | Contains, StartsWith | -like, -contains       | =~                 |
| !~       | not like | not in              | Except               | -notlike, -notcontains | ! <str1> =~ <str2> |
| +        | +        | +                   | +                    | +                      | +                  |
| -        | -        | -                   | -                    | -                      | -                  |
| *        | *        | *                   | *                    | *                      | *                  |
| /        | /        | /                   | /                    | /                      | /                  |
| in:      | in       | re, in, startswith  | Contains, StartsWith | -In                    | case in            |
| not-in:  | not in   | not in              | Except               | -NotIn                 |                    |
| &&       | and      | and                 | &&                   | -And                   | -a, &&             |
| \|\|     | or       | or                  | \|\|                 | -Or                    | -o, \|\|           |
