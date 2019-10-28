---
layout: post
title:  "Máquina de Estados finitos em Ladder"
date:   2019-08-23 18:00:00
categories: wiki
tags: [ladder]
lang: pt
ref: ladder-fsm
description: Máquina de Estados feita utilizando só relés.
img: https://images.unsplash.com/photo-1472235008642-bb3ce23994ac?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1050&q=80
img-ref: https://unsplash.com/photos/4pPzKfd6BEg
---

[Ladder](https://pt.wikipedia.org/wiki/Linguagem_ladder) foi originalmente concebida para documentar diagramas elétricos. No entanto como no mundo elétrico tudo ocorre em paralelo pode ser que ocorram situações inesperadas como condições de corrida e afins. Ou pior: o sistema resultar em diagramas muito complexo levando a maior dificuldade de manutenção e implementação. Um forma de evitar isto é utilizar técnicas da programação como a representação de [máquina de estados finita](https://pt.wikipedia.org/wiki/Máquina_de_estados_finita) para desenvolvimento dos diagramas Ladder e assim simplificar instalações elétricas e programas feitos em CLP.

# Passo a passo para construir uma máquina de estados 

Basta seguir o seguintes passos:

 1. Listar todas ações do sistema
 2. Associar cada ação a um estado
 3. Listar todas as entradas
 4. Associar um conjunto de entradas a um evento no sistema
 5. Associar cada transição de estados

Para uma implementação em Ladder, o segredo está em usar uma combinação de relés para representar de forma única a necessidade de acionamento. Desta forma o acionamento é feito em dois níveis: um nível apenas para comandar gerenciar os sensores e um nível para acionar diretamente.

Podemos representar a operação lógica "E" como uma ligação em série entre acionamentos e a operação "OU" como uma ligação em paralelo. De forma similar podemos usar a representação binária para gerar uma identificação da combinação de várias entradas de forma mais compacta.

## Exemplo - 3 Way

Tendo dois interruptores, se apertar qualquer um dos interruptores muda o estado entre ligado e desligado.

Primeiro definimos os possíveis estados do sistema:

 1. lâmpada ligada
 2. lâmpada desligada

Depois definidmos as possíveis entradas do sistema:

 1. Relé 1 Desligado e Relé 2 Desligado
 2. Relé 1 Desligado e Relé 2 Ligado
 3. Relé 1 Ligado e Relé 2 Desligado
 4. Relé 1 Ligado e Relé 2 Ligado

For fim basta associar cada entrada a uma situação desejada. Podemos por exemplo associar interruptores em posição diferente ao acendimento da lâmpada.

 1. Relé 1 Desligado e Relé 2 Desligado -> Lâmpada Desligada
 2. Relé 1 Desligado e Relé 2 Ligado -> Lâmpada Ligada
 3. Relé 1 Ligado e Relé 2 Desligado -> Lâmpada Ligada
 4. Relé 1 Ligado e Relé 2 Ligado -> Lâmpada Desligada

A partir disto podemos gerar diretamente o diagrama ladder com a resposta final:

``` 
     I1       I2            L
|---|/|------|/|-----------(/)---|
|---|/|------| |-----------( )---|
|---| |------| |-----------(/)---|
|---| |------|/|-----------( )---|
```

Podemos simplificar o diagrama retirando as situações em que a lâmpada está desligada:

```
|---|/|------| |-----------( )---|
|---| |------|/|-----------( )---|
```

Podemos simplificar ainda mais combinando os fios comuns:
```
           I1       I2          L
|-----+---|/|------| |---+-----( )---|
      |---| |------|/|---|
```

Para algo mais natural, isto é, com os 2 nterruptores em posições iguais acendendo a lâmpada, basta modificar levemente o diagrama final:

```
           I1       I2          L
|-----+---| |------| |---+-----( )---|
      |---|/|------|/|---|
```


Note que esta é exatamente a forma de instalar os interruptores de 3 vias, mas poderia ser colocado em uma CLP para emular o mesmo comportamento. Óbvio que este é um exemplo super simples porém a mesma lógica poderia ser estendida a para coisas mais sofisticadas incluindo adicionar sensores e contatoras. Máquina de estados é apenas um modelo com uma representação lógica que permite análise independente do formato de implementação. Podemos realizar a mesma máquina de estados de diversas formas e usando diversas tecnologias. A vantagem de associar isto a um diagrama Ladder é que podemos implementar estruturas computacionais utilizando somente dispositivos elétricos, dispensando o uso de microcontroladores ou ainda poder validar possiveis problemas usando ferramentas de verificação formal.

Para quem é da área computacional, pode parecer estranho falar de máquinas de estado sem mencionar tecnologias como FPGA ou micro-processadores. No entanto, existiram vários computadores antigos baseados interamente em relés como o [FACOM 128](http://museum.ipsj.or.jp/en/computer/dawn/0012.html) que continua [em operação até hoje](https://canaltech.com.br/infra/tecnico-mantem-computador-criado-em-1959-funcionando-perfeitamente-145777/). Obviamente relés não são usados nos computadores atuais por terem chavemento lento, falhas ocasionais por magnetização da chave e consumirem mais corrente que transistores, mas isto não torna impossível a implementação de sistemas computacionais.

## Referências

 * https://hackaday.com/2019/08/03/maybe-the-oldest-computer-probably-the-oddest/
 * https://docplayer.com.br/110916655-Controle-de-processos-industriais-programacao-logica-de-clp-s-com-ladder-e-fsm.html
 * https://www.dmcinfo.com/Portals/0/State%20Transition%20Diagram%20to%20PLC%20Ladder%20Logic%20Translation%20Whitepaper.pdf
 * http://hamiltonsena.net/programacao-logica-de-clps-com-ladder-e-fsm/
 * https://www.allaboutcircuits.com/textbook/digital/chpt-6/programmable-logic-controllers-plc/
 * https://www.splatco.com/fsm_in_ladder.htm
 * http://www.rosebotics.org/me430-plc-fsm/unit?unit=3&lesson=2
