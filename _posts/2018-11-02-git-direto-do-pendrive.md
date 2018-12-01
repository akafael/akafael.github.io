---
layout: post
title:  "Usando o Git direto no Pen Drive"
date:   2015-01-01 18:00:00
categories: wiki
tags: [git]
lang: pt
ref: flashdrive-git
description: Magia do Git direto do seu bolso
img:
---

[Git]({{ site.baseurl }}{% link _posts/2018-09-29-git.md %}) é um sistema de versionamento descentralizado, o que significa que pode ser usado diretamente de qualquer lugar inclusive um Pen Drive. Segue alguns formatos interessantes:

## Pen Drive como repositório principal

Todo os arquivos do Git ficam armazenados localmente, assim pode ter toda a parte de controle de versão normalmente. Inclusive com os comandos direto pelo computador assim como faria com qualquer outra pasta local. As alterações podem ser ainda sincronizadas com um servidor online através de push e pull e caso o use em um computador diferente sem git, nada impede que possam ser comparadas depois.

Desta forma pode garantir a integridade dos arquivos dentro do Pen Drive em caso de qualquer alteração acidental.

### Git Portable

Uma outra forma é carregar o arquivo executável do [git portátil](https://git-scm.com/download/win) para poder executar sempre. Desta forma pode garantir a integridade e controle de versão de um repositório ou mesmo do pen drive inteiro em qualquer computador.

## Pen Drive como Remote

Ambas técnicas podem ainda serem combinadas com o uso de remote, para acessar e comparar com algum repositório local armazenado diretamente no computador.

https://en.wikibooks.org/wiki/Git/Repository_on_a_USB_stick
