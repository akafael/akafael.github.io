---
layout: post
title:  "Executando Windows dentro do Linux"
date:   2020-06-09 18:00:00
categories: wiki
tags: [vm,linux]
lang: pt
ref: vm-xsession
description: Usando o Virtual Box sem Gerenciador de Janelas
img: https://source.unsplash.com/jZvlT-FvTZM
img-ref: https://unsplash.com/photos/jZvlT-FvTZM
---

Existem várias opções para utilizar programas de um outro sistema operacional dentro do Linux, como o [Wine](https://www.winehq.org) e o uso de Dual Boot. Um outra possíbilidade é o uso de máquinas virtuais, assim pode ter ambos sistemas operacionais em execução ao mesmo tempo e desfrutar do benefício de ambos sem o risco de expor os dados de um ao outro.

Para este cenário segue um truque interessante de abrir o Virtual Box sozinho sem gerenciador de Janela, dando a impressão total estar usando o Windows diretamente. 

# Virtual Box via XSession 

Para criar uma definição de sessão para o X basta criar um [Arquivo Desktop](https://specifications.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html#basic-format) dentro da pasta `/usr/share/xsessions/` indicando qual programa ou gerênciador de janelas deseja usar. Segue o formáto básico:

<script src="https://gist.github.com/akafael/66e397daaf8f02584a23860edd606ae8.js"></script>

O mesmo truque pode se utilizado com Android x86 ou qualquer outro sistema operacional. A vantagem desta abordagem é que ser um meio termo entre prover o máximo de recursos a VM sem ter que trabalhar com Dual Boot. O mesmo truque pode ser utilizado com o Google Chrome no lugar do Virtual Box para criar um sessão igual ao um ChromeBook. A melhor parte é que, ao fechar o programa, a sessão do X é automáticamente fechada e retorna para a tela de login. Ou ainda pode ter um modo Arcade utilizando o Retro Arch ou a Steam...

## Vá Além

 * https://wiki.archlinux.org/index.php/Display_manager#Session_configuration

