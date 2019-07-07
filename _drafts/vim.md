---
layout: post
title:  "Vim"
date:   2015-01-01 18:00:00
categories: wiki
tags: [linux,vim]
lang: en
ref: vim
description: Bits about Vim
img:
---

[Vim](vim) is a text editor strong based into keyboard shortcuts and modes. It was designed for shell only interface, but it also have some gui version. It has some stepper learning curve. It took me a couple hours to get used with most of the basics commands. But once you learn it does provide a very fast way to perform all the common typing operations. You can customize as much you want with plugins and vim programming language. If you start to use, be certain: you will never stop to learn new features. This post is just a collection of some of cool features thay I learned. If want learn more check Vim Wikia.

## Insert Text from file at Cursor position

It very stratfoward just type

```
:r secretSauce.txt
```

## Search and Replace

Probably the thing that I use most is its search powered by [Regex](regex). The sintax is very similar to [sed](sed) witch is also a Regex based editor.

```
:%s/badWord/betterWord/g
```

