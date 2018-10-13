---
layout: post
title:  "Como estimar nota para aprovação em concursos"
date:   2018-09-22 8:00:00
categories: journal
tags: [R]
lang: pt
ref: score-estimation
description:
img: https://images.unsplash.com/photo-1494389945381-0fe114b8ea4b?ixlib=rb-0.3.5&s=aed8811d6451e4cb0d16c5145344b76f&auto=format&fit=crop&w=1350&q=80
---

Com base em um pouco de conhecimento de estatística dá para estimar a nota mínima para passar em um concurso antes mesmo de fazer a prova. Magia Negra? Nada! Apenas estatística!

## Princípio

A distribuição das notas em uma prova composta por questões objetiva pode ser aproximada por uma distribuição normal. Bastando identificar a média e a variância de acordo com o grupo. Em grupo grande a média tende a ficar no meio, ou deslocar para cima para uma prova fácil ou para baixo para uma prova mais dificil.

**Em termos estatísticos:** Se ordenarmos as pessoas pelas notas, e tomamos uma porção fixa a partir da pessoas que melhor despenho podemos transformar a informação da concorrência em um percentil e assim verificar qual a nota correspondente através de da distribuição acumulada da normal.

## Passo a passo

Não entendeu nada? Não lembra as formúlas? Não se preocupe! Utilizando a [linguagem de programação R](https://pt.wikipedia.org/wiki/R_(linguagem_de_programação)) tudo fica super fácil, basta seguir os seguintes passos:

### 1. Obter a concorrência por vaga da etapa em questão

```
numCandidatos = 10000
numVagas = 20
```

Pode ser de concursos anteriores também, caso ainda não tenha saido.

### 2. Calcular o percentual de vagas pela quantidade de candidatos

```
porcentagemAprovadosEtapa = numVagas/numCandidatos;
```

### 3. Gerar notas aleatórias usando uma distribuição normal

Primeira estimativa
```
mediaEstimada = 50 # Metade da nota
varianciaEstimada = 25 # 1/4 da nota
notas = rnorm(numCandidatos,mediaEstimada,varianciaEstimada);
```

A média e a variância podem ser ajustadas de acordo com informações de concursos anteriores. Em minha experiência, este é um bom primeiro chute.

### 4. Verificar a posição correspodente a aquela porcentagem

```
# Somente aprovados
quantile(notas,(1-porcentagemAprovadosEtapa))

# Valores comuns para concursos
quantile(notas,c(.5,.7,.9,.99))
```

### 5. Efeito de critério de correção

Algumas bancas adotam critério de correção, como o caso de uma errada anula uma certa como forma de previnir o chute. Porém o processo de estimativa é similar bastando corrigir a média e a variância.

Com o critério uma errada anula uma certa a nota passa a variar de -100% até 100%. Porém chutar na metade do intervalo já não faz tanto sentido pois errar errar tudo é tão pouco provável como acertar tudo. De modo que podemos deslocar a média um pouco para a esquerda.

```
mediaEstimada = 25 # 1/4 da nota
varianciaEstimada = 25 # 1/4 da nota
notas = rnorm(numCandidatos,mediaEstimada,varianciaEstimada);
```

A média e a variância podem ser ajustadas de acordo com informações de concursos anteriores. Em minha experiência, este é um bom primeiro chute.

## Alguns resultados interessantes

### Notas para algumas porcentagens de vagas por número de candidatos

 * **50%** Metade dos candidatos têm uma nota acima da média das notas ( nenhuma novidade =P )
 * **60%** 30% dos candidatos com uma nota acima de 60%
 * **70%** 10% dos candidatos com uma nota acima de 70%
 * **82%** 1% dos candidatos com uma nota acima 82%

 Não precisa gabaritar tudo para passar. Ajuda muito mas não precisa, pois a relação entre as notas e quantidade de vagas não é linear. Um pouco de estudo direcionado já te põe muito a frente. Chutar que a metade vai acertar a metade é um chute pessimista, na maioria dos concurso a média é menor que isto.

 ### Quantidade de candidatos importa?

 O que importa é a relação entre a quantidade de vagas e quantidade de candidatos. Mesmo um concurso com muitas vagas pode exigir notas altas por ter também muitos candidatos. Logo olhar somente a quantidade não ajuda muito, afinal metade destes já vai ser eliminada logo de início.

 ## Vá além

 * [Tutorial de Programação em R](http://www.r-tutor.com/r-introduction)
 * [Cálculo de percentil no R](http://www.r-tutor.com/elementary-statistics/numerical-measures/percentile)
