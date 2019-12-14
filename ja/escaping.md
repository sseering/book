---
layout: content
title: エスケープ
prev: シェル
next: プラグイン
link_prev: /ja/shells_in_shells.html
link_next: /ja/plugins.html
---

Nuは様々なOSで使用できる一連のコマンドを提供します。このような一貫性があると便利です。ただし、ときにはNuコマンドと同じ名前のコマンドを実行したいときがあります。例えば、ローカルの`ls`や`date`コマンドなどです。このような場合にはキャレット(^)コマンドを使用します。

Nuのコマンド:

```
> ls
```

ローカルコマンドへのエスケープ:

```
> ^ls
```
