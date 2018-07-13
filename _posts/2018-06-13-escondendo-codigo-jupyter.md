---
layout: post
title:  "Como esconder a células de código no Jupyter"
date:   2018-07-13 12:00:00
categories: wiki
tags: [python,jupyter]
lang: pt
ref: hide-button-jupyter
description: Tutorial sobre como esconder as células de código no jupyter
img: https://images.unsplash.com/photo-1485939551351-bc1a4ad5ce5a?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=b600388136de0637b30389df42784860&auto=format&fit=crop&w=1350&q=80
---

Para esconder as células de código podemos usar um truque bem simples combinando Javascript, CSS e uma célula de markdown usando o seguinte código:

<script src="https://gist.github.com/akafael/864448313128236e95a4c10dabbfd043.js"></script>

## Como funciona?

Cada célula no Jupyter gera uma div com uma classe definida pelo tipo da célula. Em particular as células de código são todas da classe *input*. Assim basta usar Javascript para mudar as propriedades de todas as div da classe para ocultas.

Depois podemos colocar isto dentro de uma função e associar esta função a um botão disponível na página para permitir que o usuário veja também o código caso deseje. Para dar o efeito de ligar/desligar é criado um variável que global para sinalizar se tudo está oculto e associar isto a um condicional dentro da função e pronto!

Crédito:
[Imagem de Capa](https://unsplash.com/photos/wny6Y4MbyhA) de [@nxvision](https://unsplash.com/@nxvision)
