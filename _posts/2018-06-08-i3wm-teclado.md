---
layout: post
title:  "Configurando Teclado no I3"
date:   2018-06-08 18:00:00
categories: wiki
tags: [linux,i3wm]
lang: pt
ref: i3-keyboard
description: Guia de configuração de atalhos para alternar entre dois layouts diferentes.
img: https://images.unsplash.com/photo-1525651561332-f1382d2bb6c4?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=9b6d0f1a104efa0aa053982a38fb6cf4&auto=format&fit=crop&w=1050&q=80
---

No [gerênciador de janelas I3]({{ site.baseurl }}{% link _posts/2018-06-01-i3wm.md %}) não existe uma opção para alternar entre diferentes layouts de teclado. Mas tal pode ser resolvido acrescentando o seguinte trecho no [arquivo de configuração do i3](https://i3wm.org/docs/userguide.html#configuring):

<script src="https://gist.github.com/akafael/8b3d306af35df2a5ec9a679221050d80.js"></script>

## Como funciona ?

Para mudar de layout o podemos usar o [setxkbmap](https://wiki.archlinux.org/index.php/Keyboard_configuration_in_Xorg) com código do idioma do teclado.

```
setxkbmap -layout en
```

Para nosso comando mágico, primeiro consultamos o layout atual a partir da opção *-query*:

```
setxkbmap -query
```

depois pesquisamos no resultado pelo código de um dos layout que será usado usando o comando [grep](https://pt.wikipedia.org/wiki/Grep) com o [pipe](https://www.vivaolinux.com.br/dica/Usando-o-pipe)

```
setxkbmap -query | grep us
```

Agora vem a parte mágica. Caso encontre o layout do outro idioma desejado o grep retorna que deu tudo certo então podemos associar uma comando para ser executando usando [operador lógico E do Linux](https://www.vivaolinux.com.br/dica/Principais-comandos-do-Linux):

```
setxkbmap -query | grep us && setxkbmap -layout br
```

Então basta acrescentar o [operador lógico OU](https://www.vivaolinux.com.br/dica/Principais-comandos-do-Linux) para executar o comando para o outro layout quando o grep não achar o layout

```
setxkbmap -query | grep us && setxkbmap -layout br || setxkbmap -layout us
```

Por fim associamos este comando a um [atalho de dentro do i3 config](https://i3wm.org/docs/userguide.html#keybindings)

```
bindsym $mod+space "exec setxkbmap -query | grep us && setxkbmap -layout br || setxkbmap -layout us"
```
