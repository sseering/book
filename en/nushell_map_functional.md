---
layout: content
title: NuShell map from functional languages
prev: Imperative map 
next: Operator map
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
| = dec                  | dec                           |                                                      | pred                                       |                                                 |
| default                |                               |                                                      |                                            |                                                 |
| drop                   |                               |                                                      |                                            |                                                 |
| du                     |                               |                                                      |                                            |                                                 |
| each                   | map                           | map                                                  | map                                        |                                                 |
| echo                   | println                       |                                                      | putStrLn, print                            |                                                 |
| enter                  |                               |                                                      |                                            |                                                 |
| evaluate_by            |                               |                                                      |                                            |                                                 |
| exit                   | System/exit                   |                                                      |                                            |                                                 |
| fetch(`*`)             |                               |                                                      |                                            |                                                 |
| first                  | first                         |                                                      | head                                       |                                                 |
| format                 | format                        |                                                      | Text.Printf.printf                         |                                                 |
| from bson              |                               |                                                      |                                            |                                                 |
| from csv               |                               |                                                      |                                            |                                                 |
| from eml               |                               |                                                      |                                            |                                                 |
| from ics               |                               |                                                      |                                            |                                                 |
| from ini               |                               |                                                      |                                            |                                                 |
| from json              |                               |                                                      |                                            |                                                 |
| from ods               |                               |                                                      |                                            |                                                 |
| from sqlite            |                               |                                                      |                                            |                                                 |
| from ssv               |                               |                                                      |                                            |                                                 |
| from toml              |                               |                                                      |                                            |                                                 |
| from tsv               |                               |                                                      |                                            |                                                 |
| from url               |                               |                                                      |                                            |                                                 |
| from vcf               |                               |                                                      |                                            |                                                 |
| from xlsx              |                               |                                                      |                                            |                                                 |
| from xml               |                               |                                                      |                                            |                                                 |
| from yaml              |                               |                                                      |                                            |                                                 |
| get                    |                               |                                                      | (cmd).column                               |                                                 |
| grep                   | filter                        |                                                      | filter                                     |                                                 |
| group_by               | group-by                      |                                                      |                                            |                                                 |
| headers                |                               |                                                      |                                            |                                                 |
| help                   | sp_help                       |                                                      | Get-Help, help, man                        | man                                             |
| histogram              | N/A                           |                                                      |                                            |                                                 |
| history                | N/A                           |                                                      | Get-History, history                       | history                                         |
| inc(`*`)               | inc                           |                                                      | succ                                       | N/A                                             |
| insert                 |                               |                                                      | Add-Member                                 |                                                 |
| is_empty               | empty?                        |                                                      | String.InNullOrEmpty()                     |                                                 |
| keep                   | take, drop-last, pop          |                                                      | init, take                                 | head                                            |
| keep_until             |                               |                                                      |                                            |                                                 |
| keep_while             |                               |                                                      |                                            |                                                 |
| kill                   | N/A                           |                                                      | Stop-Process, kill                         | kill                                            |
| last                   | last, peek                    |                                                      | last                                       |                                                 |
| lines                  | N/A                           |                                                      | lines, words, split-with                   |                                                 |
| ls                     | N/A                           |                                                      | Get-ChildItem, dir, ls                     | ls                                              |
| map_max_by             |                               |                                                      |                                            |                                                 |
| match(`*`)             | case when                     |                                                      | [regex]                                    |                                                 |
| merge                  |                               |                                                      |                                            |                                                 |
| mkdir                  | N/A                           |                                                      | mkdir, md                                  | mkdir                                           |
| mv                     | N/A                           |                                                      | Move-Item, mv, move, mi                    | mv                                              |
| next                   |                               |                                                      |                                            |                                                 |
| nth                    | nth                           |                                                      | [x], indexing operator, ElementAt(x)       |                                                 |
| open                   |                               |                                                      | Get-Content, gc, cat, type                 | cat                                             |
| parse                  |                               |                                                      |                                            |                                                 |
| pivot                  | (apply mapv vector matrix)    |                                                      | transpose                                  |                                                 |
| post(`*`)              | N/A                           |                                                      | Invoke-WebRequest                          |                                                 |
| prepend                | cons                          |                                                      |                                            |                                                 |
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
| select(`***`)          | select-keys                   |                                                      | Select-Object, select                      |                                                 |
| shells                 |                               |                                                      | N/A                                        |                                                 |
| shuffle                | shuffle                       |                                                      | $var                                       | Sort-Object {Get-Random}                        |
| size                   | count                         |                                                      | Measure-Object, measure                    | wc                                              |
| skip                   | rest                          |                                                      | tail                                       |                                                 |
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
| where                  | filter                        |                                                      | filter                                     |                                                 |
| which                  | N/A                           |                                                      | N/A                                        | which                                           |
| wrap                   |                               |                                                      |                                            |                                                 |

* `*` - these commands are part of the standard plugins
* `**` - renamed from `edit` to `update` in 0.13.1
* `***` - renamed from `pick` to `select` in 0.13.1
