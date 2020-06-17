---
layout: article
title: Potenciômetro
permalink: /introrobotica/pt/m24PaKL
key: intro-robotica-potenciometro
aside:
  toc: true
sidebar:
  nav: introrobotica
comments: true
---

# Potenciômetro

O potenciômetro é um dispositivo tipicamente composto por um pino rotativo e algumas entradas. Sua principal função é servir como um resistor variável, ajustável por meio da rotação de seu pino.

<div align="center">
<img class="image image--m" src="https://i.imgur.com/L6CKAyg.jpg"/>
<p><i><small>O tipo de potenciômetro mais comumente encontrado em projetos eletrônicos</small></i></p>
</div>

No potenciômetro retratado acima, a resistência entre os conectores extremos e o conector central é variada a partir da rotação do pino metálico.

A resistência máxima alcançada por um potenciômetro depende da sua resistência nominal, geralmente encontrada escrita em alguma de suas faces (não existe código de cores de potenciômetros!).

O símbolo do potenciômetro é um resistor com uma seta apontando para seu centro:

<div align="center">
<img class="image image--m" src="https://i.imgur.com/aRVTJGK.png"/>
<p><i><small>Simbolo eletrônico do potenciômetro</small></i></p>
</div>

## Funcionamento Interno

Internamente, o potenciômetro é composto por uma fita resistiva e um conector que percorre ao longo desta fita. Dependendo da posição do conector, ajustável pelo usuário,, a corrente que atravessa o potenciômetro pode percorrer um caminho mais curto ou mais longo, sendo resistido ao longo do percusso por esta fita resistora, assim alterando a sua corrente devido à lei de Ohm.

<div align="center">
<img class="image image--xl" src="https://i.imgur.com/kmJeF0z.png"/>
<p><i><small>Na direita, podemos ver o esquema interno de um potenciômetro. A fita resistiva é representada pelo semi-circulo cinza, enquando que o conector é representado pela alavanca central</small></i></p>
</div>

## Utilizando no Arduino

Diferente do botão, que só possui dois estados (apertado e não apertado), o potênciometro é um dispositivo de entrada analógico. Ou seja, sua entrada pode variar entre totalmente apertado e totalmente não apertado, além de todos os estados entre estes.

Logo, o metodo de ler esta entrada também deve ser diferente. No Arduino, existem portas digitais e analógicas. As analógicas, localizadas opostas às digitais na placa do Arduino, são utilizadas apenas para *leitura*, sendo a *saida* analógica realizada pelas portas digitais PWM (veremos mais à frente o que isto significa).

<div align="center">
<img class="image image--xl" src="https://i.imgur.com/Qq9Q9I0.png"/>
<p><i><small>No Arduino Uno, as portas analógicas estão localizadas na parte de baixo, numeradas de A0 à A5</small></i></p>
</div>

### Funções para dados analógicos

No Arduino, possuimos algumas funções especiais para facilitar o trabalho com entradas e saídas analógicas. São elas:

**analogRead** `analogRead(PINO)`  
Esta função irá ler o pino especificado, e retornar um valor correspondente na escala de **0-1023**.  
**0** significa que o valor está totalmente baixo (*LOW*).  
**1023** significa que o valor está totalmente alto (*HIGH*).  
Qualquer valor retornado que esteja entre estes dois extremos representa um estado intermédiario.  
**Ex.:** `analogRead(A0);`
{:.info}

**analogWrite** `analogWrite(PINO, VALOR)`  
Esta função irá enviar um sinal analógico para o pino escolhido, com o valor especificado. O **valor** inserido nesta função *deve* estar dentro da escala de **0-255**.  
**0** significa que o valor está totalmente baixo (*LOW*).  
**255** significa que o valor está totalmente alto (*HIGH*).  
Qualquer valor que esteja entre estes dois extremos representa um estado intermédiario.  
**Ex.:** `analogWrite(13, 210);`
{:.info}

**map** `map(VARIAVEL, deMin, deMax, paraMin, paraMax)`  
Esta função irá ler uma variável (especificada no primeiro argumento) e, dado seus valores minimos e máximos (deMin, deMax), adapta-las para uma nova escala, descrita pelos valores (paraMin, paraMax). A função então retorna este numero adaptado, que pode ser salva em uma nova variável.   
É extremamente útil para converter escalas diferentes. Por exemplo, converter a escala de 0-1023 proporcionada pelo `analogRead` à escala de 0-255, necessária para o `analogWrite`. A conversão se dá por meio da sintaxe descrita abaixo:  
**Ex.:** `map(analogRead(A0), 0, 1023, 0, 255);`
{:.info}

## Atividades

### 1. Brilho do LED (Exemplo)

Utilizando o circuito já pronto, disponível neste link do TinkerCAD: [tinkercad.com/things/5HafgpKMw2O](http://www.tinkercad.com/things/5HafgpKMw2O), programe o Arduino de forma que o potenciômetro controle o brilho do LED conectado ao pino 6, como mostra o vídeo abaixo:

<div align="center">
<iframe src='https://gfycat.com/ifr/valuablehugelacewing' frameborder='0' scrolling='no' allowfullscreen width='100%' height='400'></iframe>
</div>

#### Resolução:

```c
void setup() {
  pinMode(A0, INPUT); // pino analógico do potenciômetro (note que o pino possui um A, para diferencia-los dos pinos digitais)
  pinMode(6, OUTPUT); // pino do LED
}

void loop() {
  int pot = analogRead(A0); // ler o potenciômetro, e salvar o valor na variavel pot
  pot = map(pot, 0, 1023, 0, 255); // mudar a escala original de 0-1023 do analogRead, para a escala 0-255, requerida pelo analogWrite, e salvar esta alteração na variável pot
  analogWrite(6, pot); // enviar o valor com a escala adequada para o pino do LED
}
```

Antes de passar para o exercício seguinte, tente compreender o que cada linha de código está fazendo.


### 2. Barra de progresso

Utilizando o circuito já pronto, disponível neste link do TinkerCAD: [tinkercad.com/things/56Nia8Ukymf](http://www.tinkercad.com/things/56Nia8Ukymf), programe o Arduino de forma que o potenciômetro controle uma barra de progresso composta pelos LEDs conectados aos pinos 7, 6, 5 e 4, como mostra o vídeo abaixo:

<div align="center">
<iframe src='https://gfycat.com/ifr/ConfusedAdventurousLeopardseal' frameborder='0' scrolling='no' allowfullscreen width='100%' height='400'></iframe>
</div>

O primeiro LED deve acender quando a leitura do potênciometro for maior ou igual a 25% da leitura máxima. O segundo LED deve acender quando esta for maior ou igual a 50%, e o terceiro e quarto devem acender quando a leitura for maior ou igual a 75% e 100% da máxima, respectivamente.  
Use a resolução do exercício anterior como um ponto de partida.

---

> Referências:  
> Evan Amos - Vanamo Media Public Domain (potenciômetro)  
> TinkerCAD  
> teachwithict.com  