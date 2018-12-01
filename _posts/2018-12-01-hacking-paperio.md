---
layout: post
title:  "Hacking Paper.io"
date:   2015-01-01 18:00:00
categories: journal
tags: [jekyll]
lang: en
ref: magic-post
description: Estudo feito em cima do jogo Paper.io
img:
---

# Paper.io

[Paper.io](https://paper.io) é um jogo com uma mêcanica parecida com clássico snake. No entanto ao invés de se buscar alimento o objetivo é marcar a maior área possível no mapa com uma cor. Para tal é controlado um bloco colorido que se move no papa deixando um rastro de cor. Caso o ponto de início e final do rastro estejam conectados

## Movimentação básica

O controle do jogo é feito através da setinha direcionais indicando qual direção em relação a tela seguir. No entanto o bloco sempre está se movendo com velocidade constante de modo que este comando é traduzido nas seguintes possibilidades:

 * Continar no mesmo caminho
 * Virar para a direita
 * Virar para a esquerda

Não sendo possível parar o bloco.

## Regras básicas

A eliminação ocorre quando há uma colisão entre o jogador e algum obstáculo. O jogador pode ser eliminado sozinho da arena quando:

 * Colide com a parede
 * Colide com um rastro próprio

 Ou pode ser eliminado por outro jogador quando

  * Colide com o jogador dentro da área dele
  * O jogador colide com o rastro deixado

# Estratégias

## Crescimento irregular

Procure crescer de forma irregular ao redor da área dos outros jogadores sem passar por cima. Isto reduz a chance de um ataque dos outros jogadores E facilita a colonização de grande áreas uma vez que basta ligar dois pontos quaisquer de sua área.

Desta forma também são criados vários espaços vazios nas fronteira de área conquistada que são trabalhosos para serem conquistados por outros jogadores sem invadir sua áre.

## Evite Suicídio

A partir do momento que se conquista uma larga vantágem de área, dificulta imensamente o ataque de outros jogadores e aumenta a chance de morrer por suicídio. Assim é bom sempre estar atento ao tentar coisas ousadas como movimentos pequenos ou andar perto demais de paredes.

## Avanço rápido

Para crescer rápidamente é só verificar a distância máxima que pode ser percorrida sem que o adversário mais próximo ataque. A regra geral é considerar 1/3 da distância entre a fronteira de saída e o oponente mais perto.

## Detector de Humanos

Jogadores Humanos tendem a perder a atenção quando têm outros jogadores perto representando uma ameaça. Por isto basta que jogue de maneira defensiva que voluntáriamente cada jogador vai cometer algum deslise e vai ser eliminado.

# Automação - Usando Bots

É possível usar bots a partir deste [código em javascript](https://niccokunzmann.github.io/paper-io-bot/) feito por [Nicco Kunzmann](https://github.com/niccokunzmann) e programar uma estratégia usando [Blockly](https://developers.google.com/blockly/) para ser reproduzida de maneira automática.

## Bots Estocásticos

O chato de um bot é que o comportamento é muito previsível e vira presa fácil para jogadores humanos. Assim para aumentar a resilência resolvi testar o uso de um pouco de aleatoriedade.

### 1.0 Random Player

Para evitar a colisão com o próprio caminho e previnir resolvi começar com um bot conservador que move fazendo pequenos retângulos com tamanho variável, fazendo as fronteiras seja expandidas gradualmente.

Assim o bot acionava as teclas direcionais em sequência repetindo cada tecla em uma quantidade de vezes aleatória que variava de um número mínimo ao um número máximo. Quanto maior o número maior o número, maior a velocidade de expansão em relação ao ponto de referência inicial.

O que ao final gerou um comportamento interessante: com valores fixos, a área crescia rapidamente no inicio e depois lentamente pois o robô acabava ficando a maior parte do tempo dentro da região conquistada.
