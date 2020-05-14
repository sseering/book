---
layout: content
title: NuShell map from functional languages
prev: NuShell map from imperative languages 
next: NuShell operator map
link_prev: /en/nushell_map_imperative.html
link_next: /en/nushell_operator_map.html 
---

The idea behind this table is to help you understand how NuShell built-ins and plug-ins relate to functional languages. We've tried to produce a map of all the nushell commands and what their equivalents are in other languages. Contributions are welcome.

Note: this table assumes Nushell 0.13.1 or later.


| NuShell                | Clojure                       | Tablecloth (Ocaml / Elm)                             | Haskell                                    |
| ---------------------- | ----------------------------- | ---------------------------------------------------- | ------------------------------------------ | ----------------------------------------------- |
| alias                  |                               |                                                      |                                            |                                                 |
| append                 | conj                          |                                                      | (++)                                       |                                                 |
| args                   |                               |                                                      |                                            |                                                 |
| autoview               |                               |                                                      |                                            |                                                 |
| average(`*`)           |                               |                                                      |                                            |                                                 |
| binaryview(`*`)        | Integer/toHexString           |                                                      | showHex                                    |                                                 |
| calc, = math           | math operators                |                                                      |                                            |                                                 |
| cd                     |                               |                                                      |                                            |                                                 |
| clear                  |                               |                                                      |                                            |                                                 |
| clip                   |                               |                                                      |                                            |                                                 |
| compact                |                               |                                                      |                                            |                                                 |
| config                 |                               |                                                      |                                            |                                                 |
| count                  | count                         | length                                               | length                                     |                                                 |
| cp                     |                               |                                                      |                                            |                                                 |
| date                   | java.time.LocalDate/now       |                                                      | Get-Date                                   |                                                 |
| debug                  |                               |                                                      |                                            |                                                 |
| default                |                               |                                                      |                                            |                                                 |
| drop                   |                               |                                                      |                                            |                                                 |
| du                     |                               |                                                      |                                            |                                                 |
| each                   | map                           | map                                                  | map                                        |                                                 |
| echo                   | println                       |                                                      | putStrLn, print                            |                                                 |
| enter                  |                               |                                                      |                                            |                                                 |
| evaluate_by            |                               |                                                      |                                            |                                                 |
| exit                   | N/A                           |                                                      | exit                                       | exit                                            |
| fetch(`*`)             | N/A                           |                                                      | Invoke-WebRequest                          | wget                                            |
| first                  | first                         |                                                      | head                                       |                                                 |
| format                 | format                        |                                                      | String.Format()                            |                                                 |
| from bson              | N/A                           |                                                      | N/A                                        |                                                 |
| from csv               | import flatfile               |                                                      | Import-Csv, ConvertFrom-Csv                |                                                 |
| from eml               | N/A                           |                                                      | N/A                                        |                                                 |
| from ics               | N/A                           |                                                      | N/A                                        |                                                 |
| from ini               | N/A                           |                                                      | N/A                                        |                                                 |
| from json              | openjson                      |                                                      | ConvertFrom-Json                           |                                                 |
| from ods               | N/A                           |                                                      | N/A                                        |                                                 |
| from sqlite            | N/A                           |                                                      | N/A                                        |                                                 |
| from ssv               | import flatfile               |                                                      | N/A                                        |                                                 |
| from toml              | N/A                           |                                                      | N/A                                        |                                                 |
| from tsv               | import flatfile               |                                                      | N/A                                        |                                                 |
| from url               | N/A                           |                                                      | N/A                                        |                                                 |
| from vcf               | N/A                           |                                                      | N/A                                        |                                                 |
| from xlsx              | import                        |                                                      | N/A                                        |                                                 |
| from xml               | cast(variable as xml)         |                                                      | ConvertFrom-Xml                            |                                                 |
| from yaml              | N/A                           |                                                      | N/A                                        |                                                 |
| get                    |                               |                                                      | (cmd).column                               |                                                 |
| grep                   | filter                        |                                                      | filter                                     |                                                 |
| group_by               | group by                      |                                                      | Group-Object, group                        |                                                 |
| headers                |                               |                                                      |                                            |                                                 |
| help                   | sp_help                       |                                                      | Get-Help, help, man                        | man                                             |
| histogram              | N/A                           |                                                      |                                            |                                                 |
| history                | N/A                           |                                                      | Get-History, history                       | history                                         |
| inc(`*`)               | N/A                           |                                                      | N/A                                        | N/A                                             |
| insert                 |                               |                                                      | Add-Member                                 |                                                 |
| is_empty               | is null                       |                                                      | String.InNullOrEmpty()                     |                                                 |
| keep                   | take                          |                                                      | Select-Object -First                       | head                                            |
| keep_until             |                               |                                                      |                                            |                                                 |
| keep_while             |                               |                                                      |                                            |                                                 |
| kill                   | N/A                           |                                                      | Stop-Process, kill                         | kill                                            |
| last                   | last                          |                                                      | last                                       |                                                 |
| lines                  | N/A                           |                                                      | File.ReadAllLines()                        |                                                 |
| ls                     | N/A                           |                                                      | Get-ChildItem, dir, ls                     | ls                                              |
| map_max_by             |                               |                                                      |                                            |                                                 |
| match(`*`)             | case when                     |                                                      | [regex]                                    |                                                 |
| merge                  |                               |                                                      |                                            |                                                 |
| mkdir                  | N/A                           |                                                      | mkdir, md                                  | mkdir                                           |
| mv                     | N/A                           |                                                      | Move-Item, mv, move, mi                    | mv                                              |
| next                   |                               |                                                      |                                            |                                                 |
| nth                    | limit x offset y, rownumber = |                                                      | [x], indexing operator, ElementAt(x)       |                                                 |
| open                   |                               |                                                      | Get-Content, gc, cat, type                 | cat                                             |
| parse                  |                               |                                                      |                                            |                                                 |
| pivot                  | pivot                         |                                                      |                                            |                                                 |
| post(`*`)              | N/A                           |                                                      | Invoke-WebRequest                          |                                                 |
| prepend                |                               |                                                      |                                            |                                                 |
| prev                   |                               |                                                      |                                            |                                                 |
| ps(`*`)                | N/A                           |                                                      | Get-Process, ps, gps                       | ps                                              |
| pwd                    | N/A                           |                                                      | Get-Location, pwd                          | pwd                                             |
| range                  |                               |                                                      | 1..10, 'a'..'f'                            |                                                 |
| reduce_by              |                               |                                                      |                                            |                                                 |
| reject                 |                               |                                                      |                                            |                                                 |
| rename                 | N/A                           |                                                      | Rename-Item, ren, rni                      | mv?                                             |
| reverse                |                               |                                                      | [Array]::Reverse($var)                     |                                                 |
| rm                     | N/A                           |                                                      | Remove-Item, del, erase, rd, ri, rm, rmdir | rm                                              |
| save                   | N/A                           |                                                      | Write-Output, Out-File                     | > foo.txt                                       |
| select(`***`)          | select                        |                                                      | Select-Object, select                      |                                                 |
| shells                 | N/A                           |                                                      | N/A                                        |                                                 |
| shuffle                |                               |                                                      | $var                                       | Sort-Object {Get-Random}                        |
| size                   |                               |                                                      | Measure-Object, measure                    | wc                                              |
| skip                   | where row_number()            |                                                      | Select-Object -Skip                        |                                                 |
| skip_until             |                               |                                                      |                                            |                                                 |
| skip_while             |                               |                                                      |                                            |                                                 |
| sort-by                | order by                      |                                                      | Sort-Object, sort                          |                                                 |
| split_by               |                               |                                                      | String.Split()                             |                                                 |
| split_column           |                               |                                                      |                                            |                                                 |
| split_row              |                               |                                                      |                                            |                                                 |
| str(`*`)               | string functions              |                                                      | String class                               |                                                 |
| sum                    | sum                           |                                                      | Measure-Object, measure                    |                                                 |
| sys(`*`)               | N/A                           |                                                      | Get-ComputerInfo                           | uname, lshw, lsblk, lscpu, lsusb, hdparam, free |
| table                  |                               |                                                      | Format-Table, ft, Format-List, fl          |                                                 |
| tags                   | N/A                           |                                                      | N/A                                        |                                                 |
| textview(`*`)          | N/A                           |                                                      | Get-Content, cat                           |                                                 |
| tree(`*`)              | N/A                           |                                                      | tree                                       |                                                 |
| to bson                | N/A                           |                                                      | N/A                                        |                                                 |
| to csv                 | N/A                           |                                                      | Export-Csv, ConvertTo-Csv                  |                                                 |
| to html                | N/A                           |                                                      | ConvertTo-Html                             |                                                 |
| to json                | N/A                           |                                                      | ConvertTo-Json                             |                                                 |
| to md                  | N/A                           |                                                      | N/A                                        |                                                 |
| to sqlite              | N/A                           |                                                      | N/A                                        |                                                 |
| to toml                | N/A                           |                                                      | N/A                                        |                                                 |
| to tsv                 | N/A                           |                                                      | N/A                                        |                                                 |
| to url                 | N/A                           |                                                      | N/A                                        |                                                 |
| to yaml                | N/A                           |                                                      | N/A                                        |                                                 |
| touch                  | N/A                           |                                                      | Set-Content                                | touch                                           |
| trim                   | rtrim,ltrim                   |                                                      | String.Trim()                              |                                                 |
| uniq                   | distinct                      |                                                      | Get-Unique, gu                             | uniq                                            |
| update(`**`)           | As                            |                                                      |                                            |                                                 |
| version                | select @@version              |                                                      | $PSVersionTable                            |                                                 |
| with_env               | N/A                           |                                                      | $env:FOO = 'bar'                           | export foo = "bar"                              |
| what                   |                               |                                                      |                                            |                                                 |
| where                  | where                         |                                                      | Where-Object, where, "?" operator          |                                                 |
| which                  | N/A                           |                                                      | N/A                                        | which                                           |
| wrap                   |                               |                                                      |                                            |                                                 |

* `*` - these commands are part of the standard plugins
* `**` - renamed from `edit` to `update` in 0.13.1
* `***` - renamed from `pick` to `select` in 0.13.1
