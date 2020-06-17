---
layout: post
title:  "Magic Post"
date:   2015-01-01 18:00:00
categories: wiki
tags: [bash,linux]
lang: en
ref: bash-magic
description: Coleção de truques no linux usando bash
img: https://images.unsplash.com/photo-1497271679421-ce9c3d6a31da?ixlib=rb-0.3.5&s=fb2bf45324ffdbe8780fc90bb813a35e&auto=format&fit=crop&w=1051&q=80
img-ref:
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

