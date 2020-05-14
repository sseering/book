---
layout: content
title: NuShell map from imperative languages
prev: Shells/DSL map
next: Functional map
link_prev: /en/nushell_map.html
link_next: /en/nushell_map_functional.html
---

The idea behind this table is to help you understand how NuShell built-ins and plug-ins relate to imperative languages. We've tried to produce a map of all the nushell commands and what their equivalents are in other languages. Contributions are welcome.

Note: this table assumes Nushell 0.13.1 or later.


| NuShell                | Python                        | Kotlin (Java)                                        | C++                                        | Rust                                            |
| ---------------------- | ----------------------------- | ---------------------------------------------------- | ------------------------------------------ | ----------------------------------------------- |
| alias                  |                               |                                                      |                                            |                                                 |
| append                 | list.append, set.add          | add                                                  | push_back, emplace_back                    | push, push_back                                 |
| args                   |                               |                                                      |                                            |                                                 |
| autoview               |                               |                                                      |                                            |                                                 |
| average(`*`)           | statistics.mean               |                                                      |                                            |                                                 |
| binaryview(`*`)        | "{:x}".format                 | Integer.toHexString                                  |                                            |                                                 |
| calc, = math           | math operators                | math operators                                       | math operators                             | math operators                                  |
| cd                     |                               |                                                      |                                            |                                                 |
| clear                  |                               |                                                      |                                            |                                                 |
| clip                   |                               |                                                      |                                            |                                                 |
| compact                |                               |                                                      |                                            |                                                 |
| config                 |                               |                                                      |                                            |                                                 |
| count                  | len                           | Collection.size, String.length                       | length                                     | len                                             |
| cp                     | shutil.copy                   |                                                      |                                            |                                                 |
| date                   | datetime.date.today           | java.time.LocalDate.now                              |                                            |                                                 |
| debug                  |                               |                                                      |                                            |                                                 |
| default                |                               |                                                      |                                            |                                                 |
| drop                   |                               |                                                      |                                            |                                                 |
| du                     | shutil.disk_usage             | N/A                                                  |                                            |                                                 |
| each                   | for                           | for                                                  | for                                        | for                                             |
| echo                   | print                         | println                                              | printf                                     | println!                                        |
| enter                  |                               |                                                      |                                            |                                                 |
| evaluate_by            |                               |                                                      |                                            |                                                 |
| exit                   | exit                          | System.exit, kotlin.system.exitProcess               | exit                                       | exit                                            |
| fetch(`*`)             | urllib.request.urlopen        |                                                      |                                            |                                                 |
| first                  | list[0]                       | List[0]                                              | vector[0]                                  | vec[0]                                          |
| format                 | format                        |                                                      |                                            |                                                 |
| from bson              |                               |                                                      |                                            |                                                 |
| from csv               | csv                           |                                                      |                                            |                                                 |
| from eml               |                               |                                                      |                                            |                                                 |
| from ics               |                               |                                                      |                                            |                                                 |
| from ini               |                               |                                                      |                                            |                                                 |
| from json              | json                          |                                                      |                                            |                                                 |
| from ods               |                               |                                                      |                                            |                                                 |
| from sqlite            | sqlite3                       |                                                      |                                            |                                                 |
| from ssv               |                               |                                                      |                                            |                                                 |
| from toml              |                               |                                                      |                                            |                                                 |
| from tsv               |                               |                                                      |                                            |                                                 |
| from url               |                               |                                                      |                                            |                                                 |
| from vcf               |                               |                                                      |                                            |                                                 |
| from xlsx              |                               |                                                      |                                            |                                                 |
| from xml               |                               |                                                      |                                            |                                                 |
| from yaml              |                               |                                                      |                                            |                                                 |
| get                    |                               | Select                                               | (cmd).column                               |                                                 |
| grep                   | filter                        | filter                                               | filter                                     | filter                                          |
| group_by               | group by                      | GroupBy, group                                       | Group-Object, group                        |                                                 |
| headers                |                               |                                                      |                                            |                                                 |
| help                   | help                          |                                                      |                                            |                                                 |
| histogram              |                               |                                                      |                                            |                                                 |
| history                |                               |                                                      |                                            |                                                 |
| inc(`*`)               | N/A                           |                                                      | N/A                                        | N/A                                             |
| insert                 |                               |                                                      | Add-Member                                 |                                                 |
| is_empty               | is null                       | String.InNullOrEmpty()                               | String.InNullOrEmpty()                     |                                                 |
| keep                   | list[:x]                      |                                                      |                                            | head                                            |
| keep_until             | itertools.dropwhile           |                                                      |                                            |                                                 |
| keep_while             | itertools.takewhile           |                                                      |                                            |                                                 |
| kill                   | os.kill                       |                                                      |                                            |                                                 |
| last                   | list[-1]                      |                                                      |                                            |                                                 |
| lines                  | N/A                           | N/A                                                  | File.ReadAllLines()                        |                                                 |
| ls                     | N/A                           | N/A                                                  | Get-ChildItem, dir, ls                     | ls                                              |
| map_max_by             |                               |                                                      |                                            |                                                 |
| match(`*`)             | case when                     | RegEx                                                | [regex]                                    |                                                 |
| merge                  |                               |                                                      |                                            |                                                 |
| mkdir                  | N/A                           | N/A                                                  | mkdir, md                                  | mkdir                                           |
| mv                     | N/A                           | N/A                                                  | Move-Item, mv, move, mi                    | mv                                              |
| next                   |                               |                                                      |                                            |                                                 |
| nth                    | limit x offset y, rownumber = | ElemantAt(x)                                         | [x], indexing operator, ElementAt(x)       |                                                 |
| open                   |                               |                                                      | Get-Content, gc, cat, type                 | cat                                             |
| parse                  |                               |                                                      |                                            |                                                 |
| pivot                  | pivot                         | N/A                                                  |                                            |                                                 |
| post(`*`)              | N/A                           | HttpClient,WebClient, HttpWebRequest/Response        | Invoke-WebRequest                          |                                                 |
| prepend                |                               |                                                      |                                            |                                                 |
| prev                   |                               |                                                      |                                            |                                                 |
| ps(`*`)                | N/A                           | N/A                                                  | Get-Process, ps, gps                       | ps                                              |
| pwd                    | N/A                           | N/A                                                  | Get-Location, pwd                          | pwd                                             |
| range                  |                               | Range                                                | 1..10, 'a'..'f'                            |                                                 |
| reduce_by              |                               |                                                      |                                            |                                                 |
| reject                 |                               |                                                      |                                            |                                                 |
| rename                 | N/A                           | N/A                                                  | Rename-Item, ren, rni                      | mv?                                             |
| reverse                |                               | Reverse                                              | [Array]::Reverse($var)                     |                                                 |
| rm                     | N/A                           | N/A                                                  | Remove-Item, del, erase, rd, ri, rm, rmdir | rm                                              |
| save                   | N/A                           | N/A                                                  | Write-Output, Out-File                     | > foo.txt                                       |
| select(`***`)          | select                        | Select                                               | Select-Object, select                      |                                                 |
| shells                 | N/A                           | N/A                                                  | N/A                                        |                                                 |
| shuffle                |                               | Random                                               | $var                                       | Sort-Object {Get-Random}                        |
| size                   |                               |                                                      | Measure-Object, measure                    | wc                                              |
| skip                   | where row_number()            | Skip                                                 | Select-Object -Skip                        |                                                 |
| skip_until             |                               |                                                      |                                            |                                                 |
| skip_while             |                               | SkipWhile                                            |                                            |                                                 |
| sort-by                | sorted, list.sort             | sortedBy                                             | sort                                       | sort                                            |
| split_by               |                               | String.Split()                                       | String.Split()                             |                                                 |
| split_column           |                               | N/A                                                  |                                            |                                                 |
| split_row              |                               | N/A                                                  |                                            |                                                 |
| str(`*`)               | string functions              | String class                                         | String class                               |                                                 |
| sum                    | sum                           | Sum()                                                | Measure-Object, measure                    |                                                 |
| sys(`*`)               | N/A                           | N/A                                                  | Get-ComputerInfo                           | uname, lshw, lsblk, lscpu, lsusb, hdparam, free |
| table                  |                               |                                                      | Format-Table, ft, Format-List, fl          |                                                 |
| tags                   | N/A                           | N/A                                                  | N/A                                        |                                                 |
| textview(`*`)          | N/A                           | N/A                                                  | Get-Content, cat                           |                                                 |
| tree(`*`)              | N/A                           | N/A                                                  | tree                                       |                                                 |
| to bson                | N/A                           | N/A                                                  | N/A                                        |                                                 |
| to csv                 | N/A                           | N/A                                                  | Export-Csv, ConvertTo-Csv                  |                                                 |
| to html                | N/A                           | N/A                                                  | ConvertTo-Html                             |                                                 |
| to json                | N/A                           | N/A                                                  | ConvertTo-Json                             |                                                 |
| to md                  | N/A                           | N/A                                                  | N/A                                        |                                                 |
| to sqlite              | N/A                           | N/A                                                  | N/A                                        |                                                 |
| to toml                | N/A                           | N/A                                                  | N/A                                        |                                                 |
| to tsv                 | N/A                           | N/A                                                  | N/A                                        |                                                 |
| to url                 | N/A                           | N/A                                                  | N/A                                        |                                                 |
| to yaml                | N/A                           | N/A                                                  | N/A                                        |                                                 |
| touch                  | N/A                           | N/A                                                  | Set-Content                                | touch                                           |
| trim                   | rtrim,ltrim                   | String.Trim()                                        | String.Trim()                              |                                                 |
| uniq                   | distinct                      | Distinct                                             | Get-Unique, gu                             | uniq                                            |
| update(`**`)           | As                            | N/A                                                  |                                            |                                                 |
| version                | select @@version              | N/A                                                  | $PSVersionTable                            |                                                 |
| with_env               | N/A                           | N/A                                                  | $env:FOO = 'bar'                           | export foo = "bar"                              |
| what                   |                               |                                                      |                                            |                                                 |
| where                  | where                         | Where                                                | Where-Object, where, "?" operator          |                                                 |
| which                  | N/A                           | N/A                                                  | N/A                                        | which                                           |
| wrap                   |                               |                                                      |                                            |                                                 |

* `*` - these commands are part of the standard plugins
* `**` - renamed from `edit` to `update` in 0.13.1
* `***` - renamed from `pick` to `select` in 0.13.1
