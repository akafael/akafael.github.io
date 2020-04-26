---
layout: post
title:  "Taskjuggler"
date:   2020-04-14 18:00:00
categories: journal
tags: []
lang: pt
ref: taskjuggler
description: Gestão de Projetos por arquivos de texto
img: https://source.unsplash.com/_pc8aMbI9UQ
img-ref: https://unsplash.com/photos/_pc8aMbI9UQ
---

[Taskjuggler](https://taskjuggler.org) é uma ferramenta para gestão de projetos baseada em arquivos de texto.

É conhecida pela capacidade de gerar diagramas de gant tal este abaixo. Esta forma de representação permite facilitar facilmente o efeito em cascata de adiantar ou atrasar alguma etapa de um projeto.

<iframe src="https://akafael.github.io/taskjuggler-sandbox/gant.html"></iframe>

## Sintaxe

Todo o projeto é descrito usando arquivos de texto formatado em uma sintaxe próxima a do C composta por palavras chave e blocos delimitados por `{ }` .

Como toda a informação é traduzida em arquivos de texto é bastante simples de integrar o taskjuggler com um fluxo de desenvolvimento de software usual. Para facilitar montei a seguinte estrutura seguindo o padrão GNU e adaptei para permitir gerar o relatório como uma [gitpage](https://pages.github.com). O relatório final gerado está disponível aqui. E código fonte está disponível no github.

Pensando na facilidade de manutenção, o arquivo de template foi separado em várias partes comforme o uso. Assim cada tipo de informação fica agrupada em um arquivo diferente. Para isto basta usar o comando `include "filename.tji"` com o endereço relativo dos arquivos desejados.

### Definição do Projeto

<script src="https://gist-it.appspot.com/github/akafael/taskjuggler-sandbox/blob/master/src/main.tjp"></script>

### Definição de Cronograma

<script src="https://gist-it.appspot.com/github/akafael/taskjuggler-sandbox/blob/master/src/project-plan.tji"></script>

### Alocação de Recursos

<script src="https://gist-it.appspot.com/github/akafael/taskjuggler-sandbox/blob/master/src/resources.tji"></script>

### Diagrama de gantt

O diagrama mostrado foi gerado usando o seguinte código:

<script src="https://gist-it.appspot.com/github/akafael/taskjuggler-sandbox/blob/master/src/reportgant.tji"></script>

### Relatório do projeto

Os relatório final gerado em html deste projeto está públicado neste [link](https://akafael.github.io/taskjuggler-sandbox/). Para mais detalhes sobre o código fonte completo basta ir no repositório [taskjugler-sandbox no github](https://github.com/akafael/taskjuggler-sandbox)


