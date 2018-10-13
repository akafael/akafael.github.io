---
layout: post
title:  "Apresentações super rápidas com Pandoc e Markdown"
date:   2018-03-01 18:00:00
categories: wiki
tags: [linux,markdown]
lang: pt
ref: markdown-beamer
img: https://images.unsplash.com/photo-1524069498954-2904a43d203f?ixlib=rb-0.3.5&s=49afc7975baa0017be5da4d1e5b86d5c&auto=format&fit=crop&w=1347&q=80
---

Para montar uma apresentação ultra profissional em 15 min no Linux você vai precisar do pdflatex, beamer, pandoc e seu editor de texto favorito.

## 1. Escreva um resumo em markdown

Para tal usaremos a sintaxe do markdown pandoc

```
% My Badass title
% My Awesome Name
% today

# My first slide

 * Some Awesome topic introduction

# Important things

## Firsts things First

 1. Numbered
 2. Lists
 3. Allowed

## Else

 * Some item list
 * other itens

# Epic slide with Picture

![Epic Picture](path/to/epicPic.png)

```

## 2. Coloque todas as imagens num pasta

"Uma imagem vale mais que mil palavras." Uma vez que o esqueleto da apresentação está pronto pode buscar imagens que ajudem a dar uma dinâmica maior.

Para colocar a imagem no slide basta escrever uma linha com indicando o endereço da imagem no computador.

## 3. Converta usando Pandoc

O conteúdo da apresentação está completo, agora é a fase de fazer polimento. Para tal basta usar o Pandoc para converter para o formato que irá usar. São suportados diversos formatos incluindo: beamer, reveal.js, pptx, ...

### Apresentação em LaTeX usando o Beamer

Pode gerar o arquivo fonte em TeX

```
pandoc -t beamer meuScriptApresentacao.md -o apresentacao.tex
```

Ou ainda gerar logo o PDF direto para coisas mais simples

```
pandoc -t beamer meuScriptApresentacao.md -o apresentacao.pdf
```

## 4. Polimento

Agora que gerou o arquivo editável em tex, html ou pptx e pode focar em fazer apenas os ajustes menores em termos de tamanho das figuras ou adicionar algum template para formatar.
