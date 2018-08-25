---
layout: tool
title:  "Mensagem automática com um clique para whatsapp"
date:   2015-01-01 18:00:00
categories: tools
tags: [tools]
lang: pt
ref: whats-instchat
description: Gerador de links de chat para whatsapp
img: https://images.unsplash.com/photo-1512428559087-560fa5ceab42?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=665f85219b6ad4ee4b274871593f3394&auto=format&fit=crop&w=1050&q=80
---

<script src="https://cdn.rawgit.com/akafael/javascript_cookbook/master/scripts/reading_time.js"></script>
<script>

whatsLink = ""

function onCount()
{
    phoneNumber = document.getElementById("textCellphone").value;
    chatMsg = document.getElementById("textBox").value;

    // Generate Link
    resultBox.href = 'https://wa.me/';
    resultBox.href += phoneNumber;
    resultBox.href += '?text=';
    resultBox.href += encodeURI(chatMsg);

    // description
    resultBox.innerHTML = resultBox.href;
}
</script>

Gere uma link para mensagem direta no whatsapp

<input type="number" size="14" maxlength="14" onkeydown="onCount()" onkeyup="onCount()" id="textCellphone" style="width: 100%" cols="1" rows="1" placeholder=" Insira seu telefone">


<textarea onkeydown="onCount()" onkeyup="onCount()" id="textBox" style="width: 100%" cols="1" rows="6" placeholder=" Insira seu texto"></textarea>

<div id="result">
    <a id="resultBox" style="background-color: #e9e9e9;">Link Gerado</a>
</div>
