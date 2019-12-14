---
layout: content
title: Escapando para o sistema
prev: Shells
next: Plugins
link_prev: /pt-BR/shells_em_shells.html
link_next: /pt-BR/plugins.html
---

O Nu fornece um conjunto de comandos que você pode usar entre diferentes SOs e contar com essa consistência é útil. Às vezes, porém, você quer executar comando que tem o mesmo nome que um dos comandos do Nu. Para executar os comandos locais `ls` ou `date`, por exemplo, use o comando circunflexo (^).

Comando Nu:

```shell
> ls
```

Escapando para o comando local:

```shell
> ^ls
```
