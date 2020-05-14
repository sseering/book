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
| binaryview(`*`)        | \"{:x}\".format               | Integer.toHexString                                  |                                            |                                                 |
| calc, = math           | math operators                | math operators                                       | math operators                             | math operators                                  |
| cd                     |                               |                                                      |                                            |                                                 |
| clear                  |                               |                                                      |                                            |                                                 |
| clip                   |                               |                                                      |                                            |                                                 |
| compact                |                               |                                                      |                                            |                                                 |
| config                 |                               |                                                      |                                            |                                                 |
| count                  | len                           | size, length                                         | length                                     | len                                             |
| cp                     | shutil.copy                   |                                                      |                                            |                                                 |
| date                   | datetime.date.today           | java.time.LocalDate.now                              |                                            |                                                 |
| debug                  |                               |                                                      |                                            |                                                 |
| = dec                  | x -= 1                        |  x--                                                 | x--                                        | x -= 1                                          |
| default                |                               |                                                      |                                            |                                                 |
| drop                   |                               |                                                      |                                            |                                                 |
| du                     | shutil.disk_usage             |                                                      |                                            |                                                 |
| each                   | for                           | for                                                  | for                                        | for                                             |
| echo                   | print                         | println                                              | printf                                     | println!                                        |
| enter                  |                               |                                                      |                                            |                                                 |
| evaluate_by            |                               |                                                      |                                            |                                                 |
| exit                   | exit                          | System.exit, kotlin.system.exitProcess               | exit                                       | exit                                            |
| fetch(`*`)             | urllib.request.urlopen        |                                                      |                                            |                                                 |
| first                  | list[0]                       | List[0], peek                                        | vector[0], top                             | vec[0]                                          |
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
| get                    | dict[\"key\"]                 | Map[\"key\"]                                         | map[\"key\"]                               |                                                 |
| grep                   | filter                        | filter                                               | filter                                     | filter                                          |
| group_by               | itertools.groupby             |                                                      |                                            |                                                 |
| headers                |                               |                                                      |                                            |                                                 |
| help                   | help                          |                                                      |                                            |                                                 |
| histogram              |                               |                                                      |                                            |                                                 |
| history                |                               |                                                      |                                            |                                                 |
| inc(`*`)               | x += 1                        | x++                                                  | x++                                        | += 1                                            |
| insert                 | list.insert                   |                                                      |                                            |                                                 |
| is_empty               | is None                       | isEmpty                                              | empty                                      |                                                 |
| keep                   | list[:x]                      |                                                      |                                            | head                                            |
| keep_until             |                               |                                                      |                                            |                                                 |
| keep_while             | itertools.takewhile           |                                                      |                                            |                                                 |
| kill                   | os.kill                       |                                                      |                                            |                                                 |
| last                   | list[-1]                      |                                                      |                                            |                                                 |
| lines                  | split, splitlines             | split                                                | views::split                               |                                                 |
| ls                     | os.listdir                    | N/A                                                  | Get-ChildItem, dir, ls                     | ls                                              |
| map_max_by             |                               |                                                      |                                            |                                                 |
| match(`*`)             | re                            | RegEx                                                | [regex]                                    |                                                 |
| merge                  |                               |                                                      |                                            |                                                 |
| mkdir                  | os.mkdir                      | N/A                                                  | mkdir, md                                  | mkdir                                           |
| mv                     | shutil.move                   | N/A                                                  | Move-Item, mv, move, mi                    | mv                                              |
| next                   |                               |                                                      |                                            |                                                 |
| nth                    | list[x]                       | ElemantAt(x)                                         | [x], indexing operator, ElementAt(x)       |                                                 |
| open                   | open                          |                                                      | Get-Content, gc, cat, type                 | cat                                             |
| parse                  |                               |                                                      |                                            |                                                 |
| pivot                  | zip(*matrix)                  | N/A                                                  |                                            |                                                 |
| post(`*`)              | urllib.request.urlopen        |                                                      |                                            |                                                 |
| prepend                | deque.appendleft              |                                                      |                                            |                                                 |
| prev                   |                               |                                                      |                                            |                                                 |
| ps(`*`)                | os.listdir('/proc')           |                                                      |                                            |                                                 |
| pwd                    | os.getcwd                     | N/A                                                  | Get-Location, pwd                          | pwd                                             |
| range                  | range                         | Range                                                | 1..10, 'a'..'f'                            |                                                 |
| reduce_by              | functools.reduce              |                                                      |                                            |                                                 |
| reject                 |                               |                                                      |                                            |                                                 |
| rename                 | shutil.move                   | N/A                                                  | Rename-Item, ren, rni                      | mv                                             |
| reverse                | reversed, list.reverse        | Reverse                                              | [Array]::Reverse($var)                     |                                                 |
| rm                     | os.remove                     | N/A                                                  | Remove-Item, del, erase, rd, ri, rm, rmdir | rm                                              |
| save                   | io.TextIOWrapper.write        | N/A                                                  | Write-Output, Out-File                     | > foo.txt                                       |
| select(`***`)          | {k:dict[k] for k in keylist}  | Select                                               | Select-Object, select                      |                                                 |
| shells                 |                               |                                                      |                                            |                                                 |
| shuffle                | random.shuffle                | Random                                               | $var                                       | Sort-Object {Get-Random}                        |
| size                   | len                           | size, length                                         | Measure-Object, measure                    | wc                                              |
| skip                   | list[x:]                      | Skip                                                 | Select-Object -Skip                        |                                                 |
| skip_until             |                               |                                                      |                                            |                                                 |
| skip_while             | itertools.dropwhile           | SkipWhile                                            |                                            |                                                 |
| sort-by                | sorted, list.sort             | sortedBy                                             | sort                                       | sort                                            |
| split_by               | re.split                      | String.Split()                                       | String.Split()                             |                                                 |
| split_column           |                               | N/A                                                  |                                            |                                                 |
| split_row              |                               | N/A                                                  |                                            |                                                 |
| str(`*`)               | str functions                 | String class                                         | String class                               |                                                 |
| sum                    | sum                           | Sum()                                                | Measure-Object, measure                    |                                                 |
| sys(`*`)               | sys                           | N/A                                                  | Get-ComputerInfo                           | uname, lshw, lsblk, lscpu, lsusb, hdparam, free |
| table                  |                               |                                                      | Format-Table, ft, Format-List, fl          |                                                 |
| tags                   |                               | N/A                                                  | N/A                                        |                                                 |
| textview(`*`)          |                               | N/A                                                  | Get-Content, cat                           |                                                 |
| tree(`*`)              |                               | N/A                                                  | tree                                       |                                                 |
| to bson                |                               | N/A                                                  | N/A                                        |                                                 |
| to csv                 |                               | N/A                                                  | Export-Csv, ConvertTo-Csv                  |                                                 |
| to html                |                               | N/A                                                  | ConvertTo-Html                             |                                                 |
| to json                |                               | N/A                                                  | ConvertTo-Json                             |                                                 |
| to md                  |                               | N/A                                                  | N/A                                        |                                                 |
| to sqlite              |                               | N/A                                                  | N/A                                        |                                                 |
| to toml                |                               | N/A                                                  | N/A                                        |                                                 |
| to tsv                 |                               | N/A                                                  | N/A                                        |                                                 |
| to url                 |                               | N/A                                                  | N/A                                        |                                                 |
| to yaml                |                               | N/A                                                  | N/A                                        |                                                 |
| touch                  | open(path, 'a').close()       | N/A                                                  | Set-Content                                | touch                                           |
| trim                   | strip, rstrip, lstrip         | String.Trim()                                        | String.Trim()                              |                                                 |
| uniq                   | set                           | Distinct                                             | Get-Unique, gu                             | uniq                                            |
| update(`**`)           |                               | N/A                                                  |                                            |                                                 |
| version                | sys.version, sys.version_info | N/A                                                  | $PSVersionTable                            |                                                 |
| with_env               | os.environ                    | N/A                                                  | $env:FOO = 'bar'                           | export foo = "bar"                              |
| what                   |                               |                                                      |                                            |                                                 |
| where                  | filter                        | filter                                               | filter                                     | filter                                          |
| which                  | shutil.which                  | N/A                                                  | N/A                                        | which                                           |
| wrap                   |                               |                                                      |                                            |                                                 |

* `*` - these commands are part of the standard plugins
* `**` - renamed from `edit` to `update` in 0.13.1
* `***` - renamed from `pick` to `select` in 0.13.1
