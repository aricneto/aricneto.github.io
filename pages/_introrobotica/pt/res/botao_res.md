---
layout: article
title: Interfaces básicas de comunicação
permalink: /introrobotica/pt/intro/res
key: intro-robotica-botao-res
aside:
  toc: true
sidebar:
  nav: introrobotica
comments: true
---
# Botões - Resolução

<div align="center">
  <img class="image image--xl" src="https://i.imgur.com/OHv2FPv.png"/>
</div>

**1a:** Calcule o valor do resistor utilizando a lei de Ohm, supondo que a corrente que atravessa o LED é de 8mA.  
{:.warning}

Um LED vermelho tipicamente possui uma queda de tensão de 2.0V.

$$R = \frac{U}{i}$$

$$R = \frac{3.0 - 2.0}{8 \times 10^{-3}}$$

$$R = 125Ω$$

**2a:** Mude a conexão do negativo da bateria para outros terminais do botão. O que acontece?  
{:.warning}

No terminal inferior direito, o LED ficará sempre ligado, pois os terminais de cada extremidade estão sempre em curto.  
No terminal superior esquerdo, o botão permanece com o mesmo comportamento.

**3a:** Compare a estrutura interna do botão, mostrada na parte teórica, com este exemplo. Por que este circuito funciona?
{:.warning}

Pois, ao ser pressionado, o botão cria um contato entre os terminais opostos do circuito, fazendo com que a corrente possa fluir.

---

<div align="center">
  <img src="https://i.imgur.com/c7a76v2.png"/>
</div>
 
**1b:** Este circuito é exatamente igual ao anterior. Usando os conhecimentos que você tem sobre a protoboard, procure entender por quê.  
{:.warning}

Internamente, a protoboard é disposta desta maneira:

<div align="center">
  <img src="https://i.imgur.com/N9HZVv3.png"/>
</div>

As conexões do circuito mostrado acima na protoboard são análogas às apresentadas na primeira questão.

**2b:** Adicione um outro LED à protoboard, e conecte ele de um modo que, ao apertar o botão, ambos os LEDs acendam.
{:.warning}

<div align="center">
  <img src="https://i.imgur.com/WiN4EnY.png"/>
</div>

---

**1d:** Que meio temos para diminuir a corrente que passa pelo curto entre o GND e o +5V, e fazer com que, ao pressionar o botão, a maior parte da corrente passe apenas para o pino de leitura, e não para o GND?
{:.warning}

Basta adicionar um resistor pull-down.

---

<div align="center">
  <img src="https://i.imgur.com/ntDCJoA.png"/>
</div>

**1e:** Utilizando a lei de Ohm, calcule a corrente que está passando por cada pino que definimos no Arduino, com o botão ligado e desligado.  
{:.warning}

Quando o botão não está apertado:  
1. O pino 4 não possui corrente, pois está desligado  
2. O pino 12 está ligado diretamente a um resistor de 10KΩ, que está ligado diretamente ao GND. Logo, ele também não possui corrente.

Quando o botão está apertado:  
1. O pino 4 fornece 5V a um resistor de 220Ω que está ligado a um LED vermelho:

$$i = \frac{5 - 2}{220}$$

$$i = 13mA$$

2. O pino 12 está ligado diretamente ao 5V. Não existe um resistor no circuito, mas o Arduino possui um resistor de impedância interno na faixa de 100 megaOhms ($$100 \times 10^9$$ Ohms) que é usado quando um pino é definido como **input**. Logo, a corrente no circuito é de:

$$i = \frac{5}{100 \times 10^9}$$

$$i = 5 \times 10^{-11} A = 500 nA$$

Como se pode notar, é uma corrente extremamente baixa (apenas 500 *nano*Amperes), o que demonstra a necessidade da utilização de um resistor pull-down ou pull-up.

**2e:** Insira mais um LED no circuito, e faça com que ambos sejam ligados quando o botão for apertado.  
{:.warning}

Circuito:

<div align="center">
  <img src="https://i.imgur.com/vCUwd67.png"/>
</div>

Código:

```c
// Variaveis para definir o pino dos componentes
int pinoLed1 = 4;
int pinoLed2 = 3;
int pinoBotao = 12;

// Variavel para guardar o estado do botão
int estadoBotao;

void setup() {
  // Configurar o botao como entrada, LED como saida
  pinMode(pinoBotao, INPUT);
  pinMode(pinoLed1, OUTPUT);
  pinMode(pinoLed2, OUTPUT);
}

void loop() {
  // Salvar o estado do botão na variável estadoBotão, utilizando a função digitalRead.
  // No caso, estadoBotao será HIGH se o botão estiver pressionado, ou LOW, se não
  // estiver pressionado.
  estadoBotao = digitalRead(pinoBotao);
  // Escrever o estado do botão para o pino dos LEDs.
  digitalWrite(pinoLed1, estadoBotao);
  digitalWrite(pinoLed2, estadoBotao);
  
  // Esperar um tempo para não dar muito trabalho ao simulador
  // (este delay não é necessário na vida real)
  delay(10);
}
```

**3e:** Insira mais um botão no circuito, e faça com que cada botão ligue um LED diferente.
{:.warning}

Circuito:

<div align="center">
  <img src="https://i.imgur.com/WwLdpz5.png"/>
</div>

Código:

```c
// Variaveis para definir o pino dos componentes
int pinoLed1 = 4;
int pinoLed2 = 3;
int pinoBotao1 = 12;
int pinoBotao2 = 13;


// Variavel para guardar o estado dos botões
int estadoBotao1;
int estadoBotao2;

void setup() {
  // Configurar o botao como entrada, LED como saida
  pinMode(pinoBotao1, INPUT);
  pinMode(pinoBotao2, INPUT);
  pinMode(pinoLed1, OUTPUT);
  pinMode(pinoLed2, OUTPUT);
}

void loop() {
  // Salvar o estado do botão na variável estadoBotão, utilizando a função digitalRead.
  // No caso, estadoBotao será HIGH se o botão estiver pressionado, ou LOW, se não
  // estiver pressionado.
  estadoBotao1 = digitalRead(pinoBotao1);
  estadoBotao2 = digitalRead(pinoBotao2);
  
  // Escrever o estado do botão para o pino dos LEDs.
  digitalWrite(pinoLed1, estadoBotao1);
  digitalWrite(pinoLed2, estadoBotao2);
  
  // Esperar um tempo para não dar muito trabalho ao simulador
  // (este delay não é necessário na vida real)
  delay(10);
}
```