---
layout: post
title:  "Integração contínua"
date:   2019-05-03 18:00:00
categories: wiki
tags: [travis,makefile]
lang: pt
ref: ci-makefile-travis
description: A new page has been born !
img: https://images.unsplash.com/photo-1497271679421-ce9c3d6a31da?ixlib=rb-0.3.5&s=fb2bf45324ffdbe8780fc90bb813a35e&auto=format&fit=crop&w=1051&q=80
---

[Travis]() é uma excelente ferramenta para Integração Contínua. No entanto o script utilizado para construir e verificar a compilação pode não refletir os comandos usado durante o desenvolvimento e não permitir o teste efetivo da compilação. Ainda podem ocorrer o uso de outros sistemas para integração contínua.

Para resolver estes problemas podemos utilizar um bom e velho Makefile para automatizar algumas das partes do processo. A idea básica é definir uma regra para cada cada etapa do travis, assim tanto na verificação feita pelo travis como na hora ao baixar o repositório bastará executar uma regra e todos os comandos e dependências estarão implícitos dentro do Makefile.

## Makefile

Assumindo que o repositório já está baixado é necessário apenas instalar as dependências:

```
all: program

program: program.c program.h
   gcc -o 

install:
   sudo apt-get install gcc
```

## Travis

Dentro do travis basta então executar as regras do makefile. Assim, os comandos usados para o desenvolvimento podem ser sempre testados em uma máquina virtual completamente nova garantindo a independência do funcionamento em relação a configuração do ambiente de desenvolvimento.

```
language: generic
matrix:
  include:
  - name: "Xenial kinetic"
    dist: xenial

install:
 - make install

script:
 - make
 - make tests
```

## Suporte a multipla plataformas

Obviamente esta solução acaba restringindo o tipo de plataforma. Mas tal pode ser resolvido usando variáveis dentro do makefile ou ainda usando CMake.
