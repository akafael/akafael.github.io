---
layout: post
title:  "Bash Magic"
date:   2020-04-04 18:00:00
categories: wiki
tags: [bash,linux]
lang: pt
ref: bash-magic
description:
img: https://images.unsplash.com/photo-1521776943084-9a3512bd6311?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1470&q=80
img-ref: https://unsplash.com/photos/-RMBf_xSf2U
---

Coleção de truques no linux usando bash.

# Substituição de processos

Este processo é denominado substituição de processos [1][1]. Assim dá para utilizar a saída de qualquer programa como ser fosse um arquivo para entrada em outro programa.

# ConCATenar Arquivos

Embora a maioria das pessoas usem apenas para visualizar textos, `cat` é na verdade é uma ferramenta conCATenar arquivos e um só. Exemplo, podemos juntar 3 arquivos e redirecionar para um outro com tudo junto usando o seguinte comando:

```
cat header.txt body.txt tail.txt > completefile.txt
```

Poderiamos por exemplo gera uma lista com todos os comentários marcados com TODO dentro de um projeto.

```
cat <(echo "=== My TODO List ==") <(grep *.cpp -e TODO)
```

# Diff entre duas pastas

Usando Substitituição de processos[1][1] é possível comparar o conteúdo de duas pastas:

```
diff <(ls newFolder) <(ls oldFolder)
```

[1]: https://en.wikipedia.org/wiki/Process_substitution

