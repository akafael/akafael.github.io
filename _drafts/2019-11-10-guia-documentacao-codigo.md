---
layout: post
title:  "Guia para documentação de código"
date:   2015-01-01 18:00:00
categories: wiki
tags: [wiki]
lang: pt
ref: code-documentation
description: A new page has been born !
img: https://images.unsplash.com/photo-1497271679421-ce9c3d6a31da?ixlib=rb-0.3.5&s=fb2bf45324ffdbe8780fc90bb813a35e&auto=format&fit=crop&w=1051&q=80
img-ref:
---

Ninguém gosta de documentação. Mas não adianta você falar "vou lembrar" o que fiz aqui. Daqui a uma semana você não é mais você e toda as informações que tinha frescas na mente terão se perdido em outra dimensão no espaço-tempo. Então a melhor forma de previnir qualquer problema é documentar o código. Segue uma série de dicas de como garantir uma boa documentação:

# 1. Use Nomes que façam sentido

Sim. A primeira documentação é a buscar escrever de forma clara usando a própria linguagem de programação. Internamente tudo são apenas 1 e 0. Sem contexto toda informação é apenas dado jogado ao vento. Assim a primeira fonte de documentação é usar nomes que indiquem claramente o que aquela variável ou função representa. Para todo computador uma lista de 0 e 1 é plenamente suficiente para entender o que é preciso de executado. Nomear variáveis e rotinas é uma dos recursos primordiais de qualquer linguagem de programação para facilitara vida de seres humanos que terão que ler e manter aquele código depois.

## Alguma convenções interessantes

Segue uma lista de convenções comumente usadas em diversos lugares que podem ajudar:

 * prefixo m para instancias de objeto usados internamente: mCarro = new Carro();
 * prefixo is para flags booleanas: isCold = ! isHot;
 * sufixo com o nome de algoritmos conhecidos: objectHandler(), DataBaseConnectorFactory(), generateFFT(inputSignal)
 * prefixo para tipo de objeto ( s para strings, num para Inteiros ) particulamente útil em códigos Orientados a Objetos.

## 2. Agrupe porções de código responsáveis por alguma rotina

Sei que você deve se coçar para usar aquelas rotinas convolutas que fazem tudo numa linha só e 

2. Use guias de estilo

Guias de estilo tal qual um bom design conferem integridade ao código permitindo que pequenas pistas ajudem no entendimento do contexto. Mesmo algumas coisas pequenas como CAPITAL_LETTERS para constantes e cammelCase para variáveis fazem todo a diferença e facilitam imensamente a manutenção do código. 

# 3. Comentários

"Todo comentário é uma mentira latente". Comentários são extremamente úteis para acrescentar informações extras no código. Em alguns casos pode ser intepretados para compor documentações mais extensas. Porém não compõe partes funcionais do código que serão interpretadas e executadas. Assim escrever em um comentario que aquele algorítmo mágico faz tudo certo é zero garantia que aquela parte funcione.

Muitas vezes o código evolui e o comentário continua o mesmo e aquela parte deixa representar o real funcionamento do programa. Assim primeiro escreva um código que possa ser entendido claramente sem comentário algum. E depois use comentários para coisas ajudem seu futuro eu: seja adicionando referências externas como artigos sobre o algoritmousado que ajudem no entendimento de determinada porção de código, seja indicando sugestões em partes que poderiam ser implementadas de uma forma melhor ou até 

# 4. Gerador de Documentação

Tipicamente não conseguimos ver mais de 50 linhas de código por vez. Assim para ter uma noção geral do código por vezes é nessário um bom tempo pulando de chamada de função em chamada de função e isto demanda muito tempo. No lugar disto existem ferramentas de análise estática que podem gerar relatórios como gráficos de chamadas e de depedência entre cada parte do código. Assim ao invés de ter que ficar pulando entre linhas.

# 5. Testes Automáticos

Mais código para documentar código? Exato! Testes são um forma de documentar o comportamento esperado de cada funcionalidade do programa. Compilar e estar bem escrito não é garantia de que o código fará o que é esperado. Para isto são criados testes em que o sistema é interpretado como um caixa preta e avaliado quanto a expectativa de funcionamento. Se algo no sistema não estiver operando como esperado, um teste irá indicar isto prontamente e evitar grandes prejuizos depois. Com isto o sistema pode continuar evoluindo sempre e ainda garantir que todas as funcionalidade serão preservadas.

# 6. Formalização

Em alguns casos é preciso uma garantia forte

Ter um Golden Model de um

# 7. Documentação

Níveis de abstração.

