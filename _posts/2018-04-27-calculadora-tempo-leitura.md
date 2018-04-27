---
layout: tool
title:  "Calculadora de Tempo de Leitura"
date:   2018-04-20 18:00:00
categories: tools
tags: [tools]
lang: pt
ref: read-time-calculator
description: Calcule o tempo de leitura do seu texto antes de publicar.
img: https://images.unsplash.com/photo-1478980236323-01c287f81aed?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=6b4d94e1b5fb4d004c6c9b042eb0234d&auto=format&fit=crop&w=1051&q=80
---

<script src="https://cdn.rawgit.com/akafael/javascript_cookbook/master/scripts/reading_time.js"></script>
<script>
function onCount()
{
    timeSec = readingTimeSec(document.getElementById("textBox").value,"avg");

    // Format Text Result
    resultBox.innerHTML = ' TEMPO ESTIMADO: '
    if(timeSec <= 60)
    {
        resultBox.innerHTML += timeSec + ' s';
    }
    else
    {
        timeMin = Math.floor(timeSec/60);
        resultBox.innerHTML += timeMin + ' min ' + (timeSec-timeMin*60) + ' s';
    }
}
</script>

Calcule o tempo de leitura do texto

<textarea onkeydown="onCount()" onkeyup="onCount()" id="textBox" style="width: 100%" cols="1" rows="6" placeholder=" Insira seu texto"></textarea>

<div id="result">
    <span id="resultBox" style="background-color: #e9e9e9;">TEMPO ESTIMADO: - </span>
</div>
