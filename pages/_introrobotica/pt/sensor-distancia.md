---
layout: article
title: Distância
permalink: /introrobotica/pt/juGJ6Yk
key: intro-robotica-sensores-distancia
aside:
  toc: true
sidebar:
  nav: introrobotica
comments: true
---

# Introdução

Sensores de distância têm como principal função calcular a distância entre um ponto de referência conhecido, e um ponto desejado a uma distância $$x$$, desconhecida.

Os dois tipos de sensores de distância mais utilizados na robótica são os *sonares* e os *ópticos*. Ambos atuam de forma similar, mas alguns possuem diferentes métodos para calcular o resultado final.  
É importante também não confundir os sensores de **distância** com os sensores de **proximidade**, que veremos mais à frente.

## Teoria

### *Time of Flight* (tempo de vôo)
O método mais simples e econômico para cálculo de distância é apartir do princípio que chamamos de *Time of Flight* (ToF ou tempo de vôo).

Estes sensores emitem um sinal que possui uma velocidade $$v$$ conhecida, e esperam até que o sinal atinja uma superfície e seja refletido, voltando ao sensor em um tempo $$t$$.

<div align="center"><img class="image image--xl" src="https://i.imgur.com/vUaMxw6.png"/></div>


> **Referências:**  
> 1. https://www.maxwellbohr.com.br/downloads/robotica/mec1000_kdr5000/tutorial_eletronica_-_aplicacoes_e_funcionamento_de_sensores.pdf
