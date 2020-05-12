---
layout: content
title: Aliases
prev: Configuration
next: Math
link_prev: /en/configuration.html
link_next: /en/math.html
---

Nu's ability to compose long pipelines allow you a lot of control over your data and system, but it comes at the price of a lot of typing. Ideally, you'd be able to save your well-crafted pipelines to use again and again.

This is where aliases come on.

An alias allows you to create a short name for a block of commands.  When the alias is run, it's like you typed that block of commands out.

Example:

```
> alias ls-names [] { ls | select name }
> ls-names
────┬────────────────────
 #  │ name 
────┼────────────────────
  0 │ 404.html 
  1 │ CONTRIBUTING.md 
  2 │ Gemfile 
  3 │ Gemfile.lock 
  4 │ LICENSE 
```

## Parameters

Aliases can also take optional parameters that are passed to the block.  Each of these becomes a new variable in the block.

```
> alias e [msg] { echo $msg }
> e "hello world"
hello world
```

You can have an arbitrary number of these arguments.  When the user doesn't provide a value, the variable in the block will evaluate to Nothing and be removed.

