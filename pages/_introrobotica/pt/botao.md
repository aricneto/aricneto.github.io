---
layout: article
title: Interfaces básicas de comunicação
permalink: /introrobotica/pt/intro
key: intro-robotica-botao
aside:
  toc: true
sidebar:
  nav: introrobotica
comments: true
---
# Botões

Se você está lendo isso, você provavelmente já apertou um botão para ligar o computador, ou para ligar o celular. Você ligou a luz do quarto, algum dia.

Você digitou uma senha em um caixa eletrônico. Você apertou uma campainha para entrar em casa. Apertou um botão pra ignorar aquelas ligações chatas que desligam na sua cara. Todos nós já tocamos e retocamos em botões.

Na sociedade de hoje, um botão é praticamente uma necessidade para qualquer atividade que exiga interação humana. De fato, é o padrão internacional para a comunicação entre ser-humano e máquina!
{:.info}

Devido a importância deste tão popular amigo (e inimigo) de longa data, a primeira coisa que faremos é uma breve e levemente formal introdução aos botões.

Para este curso, usaramos um tipo de botão muito conhecido e utilizado no mundo da eletrônica, conhecido como tact-switch, ou botão táctil: <img class="image image--xs" src="https://i.imgur.com/JrGoJKK.jpg"/>

## Introdução
### Teoria

O botão táctil é composto por quatro contatos de metal, que se tocam quando pressionados por um disco condutor.

Tipicamente, o botão táctil apresenta dois pares de contatos opostos uns aos outros. Estes contatos estão ligados de tal forma que, internamente, o contato diretamente oposto a ele é, de fato, parte do mesmo terminal. Na direita, podemos ver como estes contatos estão conectados internamente (note que eles não se tocam).
<div align="center"><img class="image image--xl" src="https://i.imgur.com/ppox02A.png"/></div>

Quando o botão é pressionado, um outro conector interno (marcado em amarelo) faz a ligação entre os dois terminais internos do botão. Na imagem a seguir, vemos como se comporta o botão em seus dois estados:
<div align="center"><img class="image image--xl" src="https://i.imgur.com/uiySbUd.png"/></div>
Na esquerda, o botão não está pressionado, portanto ele se comporta passivamente apenas como uma ligação entre os contatos opostos.  
Na direita, o botão está pressionado, logo, um conector interno liga os dois terminais do botão, criando um curto que faz a corrente ser transmitida entre todos os contatos.

### Prática

Vamos então pôr em prática o que aprendemos sobre o funcionamento interno do botão táctil.  
Abrindo o TinkerCAD, monte este simples circuito:

<div align="center">
  <img class="image image--xl" src="https://i.imgur.com/OHv2FPv.png"/>
</div>

**Exercicios:**  
**1a:** Calcule o valor do resistor utilizando a lei de Ohm, supondo que a corrente que atravessa o LED é de 20mA.  
**2a:** Mude a conexão do negativo da bateria para outros terminais do botão. O que acontece?  
**3a:** Compare a estrutura interna do botão, mostrada na parte teórica, com este exemplo. Por que este circuito funciona?
{:.warning}

Tendo compreendido o circuito acima, vamos passar este exemplo para a protoboard:

<div align="center">
  <img src="https://i.imgur.com/c7a76v2.png"/>
</div>

**Exercicios:**  
**1b:** Este circuito é exatamente igual ao anterior. Usando os conhecimentos que você tem sobre a protoboard, procure entender por quê.  
**2b:** Adicione um outro LED à protoboard, e conecte ele de um modo que, ao apertar o botão, ambos os LEDs acendam.
{:.warning}

## Aplicando ao Arduino

### Circuito

Vamos tentar agora o mesmo circuito, desta vez usando o Arduino para controlar o LED.  
Lembrando o objetivo: o LED deve ligar apenas enquanto o botão for pressionado!

Monte este esquema no TinkerCAD:
<div align="center">
  <img src="https://i.imgur.com/MrSbRRD.png"/>
</div>
**Uma breve explicação sobre o que está acontecendo no circuito:**  
Um sinal constante de 5V está sendo enviado para o botão. Quando este for pressionado, uma tensão de 5V (HIGH) será enviada para o pino 12 do Arduino.
<div align="center">
  <img src="https://i.imgur.com/1NnOQgX.png"/>
</div>
O ánodo do LED está conectado por um resistor de 220 Ω ao pino 4 do Arduino, enquanto que o cátodo está conectado direto ao GND.
<div align="center">
  <img src="https://i.imgur.com/TUp9lbL.png"/>
</div>

### Código

Envie o seguinte código para seu Arduino:

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
  digitalWrite(pinoLed, estadoBotao);
  
  // Esperar um tempo para não dar muito trabalho ao simulador
  // (este delay não é necessário na vida real)
  delay(10);
}
```

**Exercicio:**  
**1c:** Cada linha de código está comentada.  
Tente compreender o que deve acontecer, monte o circuito, e inicie a simulação!
{:.warning}

### Rodando

Se tudo der certo, o LED deverá ligar apenas quando o botão for apertado, afinal, o cirtuito está todo correto... *certo?...*
<div align="center">
  <img src="https://i.imgur.com/6hopkbD.png"/>
</div>
<div align="center"><p style="font-size:90%;">algo de errado não está certo</p></div>
Ao conectar a placa, vemos que o LED permanece ligado, apertando ou não o botão. Alguma coisa deve estar errada.  
O que está faltando nesse circuito? Ou será alguma coisa no código? Vamos fazer um experimento:  
Conecte o GND ao outro terminal do botão. O que acontece?

**Atencão:**  
Faça o experimento a seguir **APENAS** no simulador. Em uma placa de verdade, o curto pode danificar permanentemente seu Arduino!
{:.error}
<div align="center">
  <img src="https://i.imgur.com/aNYXglu.png"/>
</div>
O LED agora está desligado. Ao apertar o botão, nada muda. Na vida real, porém, isso causaria um curto entre o +5V e o GND, o que poderia queimar a sua placa.

De volta a estaca zero. Em um caso, temos um LED permanentemente ligado, em outro, temos um permanentemente desligado.

### O resistor pull-down

Nos experimentos acima, vimos que, ao conectar o GND à um dos terminais do botão, o LED permanece apagado. Porém, ao pressionar o botão, você causa um curto que pode queimar o seu Arduino. Sem o GND, o LED oscila entre ligado e desligado, aleatoriamente.

Quando conectamos o GND diretamente ao pino de leitura do botão, estamos dando uma referência ao Arduino. Uma pequena nota de rodapé que diz para ele: *"Isso aqui significa LOW"*.

O problema poderia ser resolvido simplesmente com essa conexão direta do pino ao GND. Porém, lembrando a lei de Ohm:

$$V = I * R$$

Considerando que um fio comum tem, em média, uma resistência de 0.1 Ω, fazer um curto direto do GND ao +5V do Arduino com um fio resultaria em uma corrente extremamente alta!

$$5 = I * 0.1 \: \Omega$$

$$I = 50 \: A$$

Ou seja, 50 amperes estariam passando pelo Arduino[^1]. Para fins de comparação, por uma churrasqueira elétrica tipicamente passa cerca de 10 amperes (porém com uma voltagem muito maior).  

[^1]: Essa corrente, porém, é limitada pela potência da fonte de alimentação usada na placa

**Desafio:**  
**1d:** Como vimos, ligar o GND ao pino de entrada do Arduino para dar uma referência funciona apenas enquanto o botão não está apertado.  
Que meio temos para diminuir a corrente que passa pelo curto entre o GND e o +5V, e fazer com que, ao pressionar o botão, a maior parte da corrente passe apenas para o pino de leitura, e não para o GND?
{:.warning}

---

Para limitar a corrente, usamos um resistor!  
Com o mesmo código e circuito, apenas adicione um resistor de 10k Ω ligando o GND e pino de entrada:
<div align="center">
  <img src="https://i.imgur.com/ntDCJoA.png"/>
</div>

**Exercícios:**  
**1e:** Utilizando a lei de Ohm, calcule a corrente que está passando por cada pino que definimos no Arduino, com o botão ligado e desligado.  
*(haverá uma divergência entre o valor calculado e o real, explicaremos mais tarde por quê)*  
**2e:** Insira mais um LED no circuito, e faça com que ambos sejam ligados quando o botão for apertado.  
**3e:** Insira mais um botão no circuito, e faça com que cada botão ligue um LED diferente.
{:.warning}