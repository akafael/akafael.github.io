---
layout: post
title:  "Integração Continua"
date:   2015-01-01 18:00:00
categories: journal
tags: [jekyll]
lang: en
ref: magic-post
description: A new page has been born !
img: https://images.unsplash.com/photo-1497271679421-ce9c3d6a31da?ixlib=rb-0.3.5&s=fb2bf45324ffdbe8780fc90bb813a35e&auto=format&fit=crop&w=1051&q=80
img-ref:
---

Um grande problema na área de tecnologia é confundirmos a técnica com a tecnologia. Em outras palavras no vício de acreditar que para usar determinada técnica é extritamente necessário o uso de uma ferramenta em particular associada. Muito embora tecnologia seja uma forma de consolidar e tornar alguma técnica acessível, na maioria dos casos o uso desta ou aquela ferramenta pode ser completamente independente da técnica usada.

Integração Contínua é a prática de agregar funcionalidades em uma linha de desenvolvimento de um projeto de forma contínua ao longo do dia. Em outras palavras é transformar o arranjo de produção de um processo linear composto por uma série de etapas dispostas em sequência para um arranjo focado no produto em que todos contribuem de forma paralela e concorrente para o desenvolvimento de um produto. Pode parecer meio caótico de se pensar ao imaginarmos um monte de mãos mexendo no mesmo no mesmo produto porém podem ser utilizadas diversas técnicas para moderar esta interação e garantir o melhor resultado no final.

## Comparação com modelos tradicionais

Enquanto no arranjo linear a falha de um agente em uma etapa pode gerar o bloqueio das etapas seguintes, no arranjo posicional cada a falha de um agente pode ser imediatamente corrigida ou substituida por qualquer outro disponível. Aléms disto, por não ser um arranjo fixo de atribuições, a quantidade de pessoas alocadas para cada parte do processo pode variar de de forma dinâmica.

A principal mudança é que ao invés ter pessoas especializadas em apenas uma atividade para produzirem o melhor produto depois de um longo preparo temos diversos agentes com diversas aptidões trabalhando de forma iterativa e a verificação da qualidade adequada sendo feita de forma automática.

## Como implementar

Em primeiro lugar é necessário ter um lugar comum em que todos possam contribuir e cada modificação possa ser avaliada e identificada. Isto pode ser feito utilizando ferramentas de controle de versão como o git. Depois é integrado alguma forma de verificação da qualidade do produto a medida que cada alteração está sendo adicionada. Como a idéia é aumentar o fluxo da produção, a verificação da qualidade e de possíveis erros necessita ser feita de forma automática, deixando assim o trabalho repetitivo para as máquinas e o trabalho criativo para as pessoas. O interessante é que para adicionar e manter novos requisitos de qualidade basta adicionar novas ferramentas de verificação. Desta forma é garantida a melhoria continua do produto e do processo.


## Estudo sobre requisitos de qualidade

### Texto

 1. Verificação Ortográfica: Palavras escritas adequadamente?
 2. Verificação Sintática: Sentenças escritas adequandamente?
 3. Verificação Semântica: Olha dos termos adequada?
 4. Verificação de Estilo: Termos utilizados adequados ao público? Algum termo com muita repetição?

### Desenvolvimento de Software

 1. Análise Estática: Guia de Estilos, legibilidade do código
 2. Compilação (Compiladores): Código escrito sem erros
 3. Funcionalidade (TDD): Código funciona como esperado?
 4. Desempenho: Métricas do código em execução


