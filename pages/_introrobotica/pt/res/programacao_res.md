---
layout: article
title: Estruturas de controle
permalink: /introrobotica/pt/programacao/res
key: intro-robotica-programacao-res
aside:
  toc: true
sidebar:
  nav: introrobotica
comments: true
---
# If

**1a:** Seguindo o exemplo 1, desenvolva um circuito e um código no Tinkercad para acender um LED vermelho quando o valor de determinada variável for maior que 10 e se for menor acenda um LED verde.  
{:.warning}

Circuito:

<div align="center">
  <img src="https://i.imgur.com/VCfUNk4.png"/>
</div>

Código:

```c
int controle = 0; // variavel de controle

int ledR = 13;
int ledG = 9;

void setup() {
  pinMode(ledR, OUTPUT);
  pinMode(ledG, OUTPUT);
}

void loop() {
  if (controle > 10) {
    digitalWrite(ledR, HIGH);
  } else if (controle < 10) {
    digitalWrite(ledG, HIGH);
  }
}
```

---

**1b:** Modifique o programa do exercício 1 adicionando um LED amarelo de forma que ele acenda quando o valor da variável for igual a 10 (mantenha os outros LEDs e condições).  
{:.warning}

Circuito:

<div align="center">
  <img src="https://i.imgur.com/MZ40ALJ.png"/>
</div>

Código:

```c
int controle = 0; // variavel de controle

int ledR = 13;
int ledG = 9;
int ledY = 6;

void setup() {
  pinMode(ledR, OUTPUT);
  pinMode(ledG, OUTPUT);
  pinMode(ledY, OUTPUT);
}

void loop() {
  if (controle > 10) {
    digitalWrite(ledR, HIGH);
  } else if (controle < 10) {
    digitalWrite(ledG, HIGH);
  } else if (controle == 10) {
    digitalWrite(ledY, HIGH);
  }
}
```

---

**Desafio:**  
Baseado no que você aprendeu sobre botões e o uso do “if”, desenvolva um circuito com um LED, um resistor e um botão. O LED só deverá acender se o botão for pressionado (estado HIGH). Para fazer esse desafio, você deverá usar o “if”.
{:.warning}

Circuito:

<div align="center">
  <img src="https://i.imgur.com/y66MH9k.png"/>
</div>

Código:

```c
// Variaveis para definir o pino dos componentes
int pinoLed = 4;
int pinoBotao = 12;
// Variavel para guardar o estado do botão
int estadoBotao;

void setup() {
    // Configurar o botao como entrada, LED como saida
    pinMode(pinoBotao, INPUT);
    pinMode(pinoLed, OUTPUT);
}

void loop() {
    // Salvar o estado do botão na variável estadoBotão, utilizando a função digitalRead.
    // No caso, estadoBotao será HIGH se o botão estiver pressionado, ou LOW, se não
    // estiver pressionado.
    estadoBotao = digitalRead(pinoBotao);

    // Escrever o estado do botão para o pino do LED.
    if (estadoBotao == HIGH)
        digitalWrite(pinoLed, HIGH);
    else
        digitalWrite(pinoLed, LOW);
}
```
