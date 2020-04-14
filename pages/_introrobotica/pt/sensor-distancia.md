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
É importante também não confundir os sensores de *distância* com os sensores de *proximidade*, que veremos mais à frente.

## Teoria

### Introdução

O método mais simples e econômico para cálculo de distância é o utilizado pelos *sonares*, chamado de método *Time of Flight* (ToF ou tempo de vôo).

**Sensores ToF:**  
Estes sensores emitem um sinal que possui uma velocidade ***v*** conhecida, e esperam até que o sinal atinja uma superfície e seja refletido, voltando ao sensor com a mesma velocidade após um tempo ***t***. Assim, a distância ***d*** pode ser calculada a partir da fórmula:  
$$d = \frac{v\times t}{2} \tag{1}$$
{:.info}

Para entender como funciona esse conceito, imagine que você joga uma bolinha de borracha contra uma parede a uma velocidade ***v*** de ***10m/s***[^1]. No momento que a bolinha sai da sua mão, você começa a cronometrar. A bolinha bate na parede, e volta para sua mão com a mesma velocidade depois de ***2 segundos***.

[^1]: Metros por segundo é uma unidade de medida de velocidade que corresponde à distância percorrida por um objeto no periodo de um segundo. Ela é representada pelo símbolo ***m/s***.

A partir dessas informações, você pode calcular a distância total percorrida utilizando a equação de Movimento Retilíneo Uniforme:

$$d = v\times t$$

$$10\mathrm{m/s} \times 2\mathrm{s} = 20\mathrm{m}$$

Como ***20m*** é a distância total percorrida, ou seja, de ida e volta, e sabemos que a distância para ambos percursos é o mesmo, podemos dividir o resultado da equação anterior por ***2*** para encontrar a sua distância até a parede. Sendo assim, descobrimos que a distância $$d = \frac{20m}{2} = 10m$$.

**Exercicios:**  
**1a:** Considerando as mesmas condições descritas acima, e utilizando a fórmula (1), calcule qual seria a distância até a parede caso a bolinha:  
  **1aa:** Seja lançada a uma velocidade de ***15m/s***, e retorne após ***5 segundos*** com a mesma velocidade.  
  **1ab:** Seja lançada a uma velocidade de ***50m/s***, e retorne após ***3 segundos*** com a mesma velocidade.
{:.warning}

### Sonar

<div align="center">
  <img class="image image--m" src="https://i.imgur.com/ZbQjGZq.png"/>
  <i>Um sensor ultrassom modelo HC-SR04 [fonte:robocore.net]</i>
</div>

Os sonares, quando ativados, emitem um sinal sonoro ultrassônico[^2], que caminha na *velocidade do som* até encontrar um obstáculo e ser refletido de volta ao sensor.

**Velocidade do som:**  
A velocidade do som no ar depende de vários fatores, mas a diferença é negligivel para sensores que não necessitam de uma precisão incrivelmente alta, então é comum associar este valor à constante de ***343 m/s***. Este será o valor que iremos utilizar para todos os calculos com sonares.  
$$v_{som} = 343 \mathrm{m/s} \tag{2}$$  
{:.info}

[^2]: Quando dizemos ultrassônico, estamos nos referindo a sinais que estão além da capacidade auditiva do ser humano (20 a 20.000 Hz). Estes sinais, portanto, só conseguem ser detectados por sensores extremamente sensíveis, ou por animais que possuem um sistema auditivo mais especializado, como cachorros, morcegos e golfinhos.

<div align="center">
  <img src="https://i.imgur.com/mbsiLmD.png"/>
  <p><i>[fonte:wikipedia.org]</i></p>
</div>

Na figura acima, podemos ver em mais detalhe a atuação do ultrasônico. O sensor, à esquerda, envia ondas sonoras que são refletidas de volta pelo obstáculo.  
É importante notar que o som é uma onda, e não um objeto ou partícula; por isso que vemos o sinal emitido ser representado como ondas que se propagam pelo ar.

Para calcular a distância a partir de um sinal ultrassom, basta utilizar a equação (1), descrita no começo, com $$v = v_{som}$$

$$d = \frac{343 \times t}{2}$$

### Exemplo

Imagine que um sensor ultrassônico é ativado. Ele emite um sinal e, depois de ***500ms***, detecta que este sinal voltou. Qual a distância do ultrassônico até o objeto detectado?

Utilizamos a equação (1) com $$v = v_{som}$$, sendo que é importante notar que o tempo ***t*** especificado na questão é dado em *milisegundos*, portanto teremos que multiplica-lo por $$10^{-3}$$ para o transformar em segundo:

$$d = \frac{343 \times 500 \times 10^{-3}}{2}$$

$$d = \frac{343 \times 0.5}{2}$$

$$d = \frac{171.5}{2}$$

$$d = 85.75\mathrm{m}$$

Logo, a distância do ultrassom até o obstáculo é igual a ***85,75 metros***.

**Exercicios:**  
**2a:** Um ultrassônico é ativado. Ele emite um sinal, e detecta que ele voltou depois de ***20ms***. Qual a distância do ultrassônico até o objeto detectado?  
**2b:** Um ultrassônico é ativado. Ele emite um sinal, e detecta que ele voltou depois de ***85ms***. Qual a distância do ultrassônico até o objeto detectado?
{:.warning}

> **Referências:**  
> 1. maxwellbohr.com.br/downloads/robotica/mec1000_kdr5000/tutorial_eletronica_-_aplicacoes_e_funcionamento_de_sensores.pdf  
> 2. robocore.net  
> 3. wikipedia.org/wiki/Ultrasound  