---
layout: post
title:  "Integração continua usando Travis e Makefile"
date:   2019-05-03 18:00:00
categories: wiki
tags: [travis,makefile]
lang: pt
ref: ci-makefile-travis
description: A new page has been born !
img: https://images.unsplash.com/photo-1497271679421-ce9c3d6a31da?ixlib=rb-0.3.5&s=fb2bf45324ffdbe8780fc90bb813a35e&auto=format&fit=crop&w=1051&q=80
---

[Travis-CI](https://travis-ci.org) é uma excelente ferramenta de integração contínua para garantir a qualidade de projetos open source. É muito comum achar projetos de código aberto com dependências escondidas que compilavam somente na máquina do primeiro desenvolvedor. O que acaba demandando um longo tempo para preparação toda vez que é necessário preparar o ambiente para um desenvolvedor novo.

Com o Travis, o projeto pode ser compilado, testado e o que mais precisar em um ambiente criado do zero a cada novo commit. Bastando descrever o processo de instalação e compilação através de um script YAML. Permitindo ainda uma documentação como código de todo o processo necessário. No entanto, o script utilizado para construir e verificar a compilação pode não refletir os comandos usado durante o desenvolvimento e não permitir o teste efetivo da compilação. Ou ainda incluir uma dependência a mais de um sistema externo para integração contínua localmente.

Para resolver estes problemas, tenho adotado a estratégia de criar hooks dentro do YAML e usar o bom e velho Makefile para automatizar algumas das partes do processo. Em geral Makefile são tipicamente usados por programadores de C e C++, mas é uma ferramenta extremamente versátil para qualquer projetos em qualquer linguagem. Pessoalmente uso para tudo... A grande vantagem em relação a scripts em BASH é que permite descrever a relação entre dependecias e [comandos de forma declarativa](https://pt.wikipedia.org/wiki/Programação_declarativa) tal ocorre com os arquivo de descrição em YAML usados pelo Travis, Ansible e muitas outras ferramentas. Porém permite que toda a equipe utilize os mesmo comandos para compilar e executar qualquer tarefa ou verificação sem depender de efetivamente mandar para um servidor externo para isto.

A idea básica é definir uma regra para cada cada etapa do travis, assim tanto na verificação feita pelo travis como na hora ao baixar o repositório bastará executar uma regra e todos os comandos e dependências estarão implícitos dentro do Makefile. 

## Makefile

Assumindo que o repositório já está baixado é necessário apenas instalar as dependências:

```
# Instala, Compila e executa Testes
.PHONY: all
all: install compile test
    @echo "Programa Instalado, Compilado e Verificado"

# Instala dependências
.PHONY: install
install:
   sudo apt-get install gcc

# Compila todas dependencias
.PHONY: compilation
compilation: bin/program

bin/program: src/program.c src/program.h
   gcc -o 

# Compila e Executa testes
.PHONY: test
test: bin/testProgram
    bin/testProgram

bin/testProgram: src/testProgram.c src/testProgram.h bin/program
   gcc -o src/testProgram
```

Com isto, para instalar basta usar o comando

```
make install
```

Podemos verificar o código usando
```
make compilation
```

E executar todos os testes unitários com
```
make test
```

Por fim se for necessário executar todas as etapas basta usar `make` direto. Obviamente este é um exemplo bem simples, dá para deixar o Makefile o quão sofisticado for necessário.

## Travis

Dentro do travis basta então executar as regras do makefile que passam a funcionar como um [hook](https://pt.wikipedia.org/wiki/Hooking) para os comandos necessários por cada etapa.

 ```
language: generic
matrix:
  include:
  - name: "Xenial kinetic"
    dist: xenial

install:
 - make install

script:
 - make compilation
 - make test
```

Assim, os comandos usados para o desenvolvimento podem ser sempre testados em uma máquina completamente nova garantindo a independência do funcionamento em relação a configuração do ambiente de desenvolvimento. Ao mesmo tempo que os comandos efetivamente usados localmente por cada programador também são testados pelo Travis.

## Aprimoramentos

Obviamente esta solução acaba restringindo o tipo de plataforma. Porém isto pode ser fácilmente resolvido dentro do makefile através da detecção do sistema operacional. Também podem [arquivos de TAG](https://en.wikipedia.org/wiki/Ctags#Tags_file_formats) para sinalizar que determinada dependência já foi instalada ou alguma etapa foi concluida.

## Referências

 * https://le-gall.bzh/post/makefile-based-ci-chain-for-go/
