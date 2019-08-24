---
layout: post
title:  "Projetos em Tempo Real no Arduino"
date:   2015-01-01 18:00:00
categories: wiki
tags: [jekyll]
lang: pt
ref: magic-post
description: A new page has been born !
img:
---

# Real Time

[Real Time]() é a garantia de o projeto irá sempre cumprir todos os requisitos de tempos da aplicação. Em outras palavras é a garantia de precisão de acontecimentos de eventos no tempo. Desta forma um sistema em Tempo Real não necessáriamente é um sistema super rápido, mas um sistema que funciona exatamente na hora que deveria funcionar sem atrasos.

## Comparativo velocidade vs exatidão

Para entender melhor, pegue o exemplo de ir ao cinema assistir a um filme que começa às 20h

## Projeto em Real Time

1. Estimar todos as restrições de tempo do projeto
2. Medir todos os tempos envolvidos no projeto
3. Montar uma sistema que garanta repetibilidade

# Garantias de tempo em microcontroladores

## Atuação vs Representação da Informação

O papel do microcontrolador é gerenciar a informação . Para traduzir esta informação

## Tempo de Execução de Instrução vs Frequência

## Medindo Tempo de execução via Ociloscópio

# Estratégias de Temporização

## Delay

# Breve Comentário sobre Real Time em Computadores

Computadores são sistemas bem mais complexos voltados para aplicações genéricas. Tipicamente em um computador várias atividades são sempre executadas de forma concorrente para garantir fácil acesso as diversas interfaces como o teclado, mouse, impressora, internet, etc... Desta forma, mesmo que computadores ofereçam uma quantidade de recursos computacional muito maior que os microcontroladores, para garantir que não existam atrasos na aplicação é um pouco mais complicado. Pois ao invés de ter somente um código em execução como em micro-controladores, cada programa escrito divide a prioridade de execução com todo o resto em execução do computador.

## Agendamento

Em um sistema computacional, nenhuma tarefa é executada de imediato. Cada tarefa é passada para uma lista de execução que é processada uma a uma pelo processador.

## Multi Task

Como forma de permitir a realização de várias tarefas, o computador realiza pequenos porções de cada tarefa e assim vai alternando entre várias.

## Multi Thread

