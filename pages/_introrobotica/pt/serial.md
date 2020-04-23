---
layout: article
title: O protocolo serial no Arduino
permalink: /introrobotica/pt/8ITcboj
key: intro-robotica-serial
aside:
  toc: true
sidebar:
  nav: introrobotica
comments: true
---

Você já sabe enviar instruções para o Arduino, ligar um LED e interagir com a placa por meio de botões conectados a ela. Mas e se você quiser controlar o Arduino por meio do seu teclado? Ou enviar informações do Arduino de volta para o computador?

É aí que entra o protocolo serial. Basicamente, é um meio de transmissão de dados entre dois dispositivos conectados. Por meio dele, você pode transmitir qualquer informação digital entre o Arduino e seu computador.

## Inicializando

Para começar a utilizar o serial no Arduino, precisamos primeiramente **inicializar** o protocolo serial. Para isso, usaremos a função:

`Serial.begin([BAUD_RATE]);`
{:.info}

Note que o Serial sempre começa com **S** maíusculo! Dentro dos parênteses, precisamos colocar o que é conhecido como *baud rate*. De modo simples, o *baud rate* é a quantidade de dados que vamos transmitir em um determinado periodo de tempo, tipicamente medido em bits/segundo. Aplicações com um *baud rate* muito alto geralmente requerem cabos e processamento de altissima qualidade.

Para a grande maioria dos casos, um *baud rate* na faixa de 10.000 é suficiente para transmitir informações entre o computador e o Arduino. Por motivos técnicos, se convencionou utilizar a faixa de 9600, que é a que utilizaremos para todos os projetos.

Assim, começamos a escrever o código iniciando o protocolo no `void setup()`:

```c
void setup() {
    Serial.begin(9600); // Inicializamos o protocolo serial
}

void loop() {
    ...
}
```

Uma vez iniciado, podemos começar a utilizar as suas funções.

## Escrevendo

Para enviar informações do Arduino para o computador, utilizamos a função:

`Serial.println([MENSAGEM]);`
{:.info}

Dentro dos parênteses, colocamos a mensagem que queremos enviar por serial. Esta pode ser uma variável, um texto, um número ou qualquer tipo de dado. Vamos ver alguns exemplos:

```c
int joao = 13; // Definimos a variável joao

void setup() {
    Serial.begin(9600); // Inicializamos o protocolo serial
}

void loop() {
    Serial.println("Ola Mundo!"); // Enviando uma mensagem de texto para o serial
    Serial.println(42); // Enviando um número
    Serial.println(true); // Enviando uma booleana
    Serial.println(joao); // Enviando a variável joao, que criamos no inicio
}
```

Para ver as mensagens que enviamos do Arduino, precisamos abrir o monitor serial no seu computador.  

### Monitor na IDE

Certifique-se primeiramente de que o Arduino está devidamente conectado ao computador. Dentro da interface do Arduino, clique na lupa no canto superior direito da IDE, e selecione o *baud rate* correto (no caso, 9600).  

<div align="center"><img src="https://i.imgur.com/NK3ZuS3.png"/></div>

<div align="center"><img src="https://i.imgur.com/IP5GxM6.png"/></div>

### Monitor no TinkerCAD

Certifique-se primeiramente de que a simulação está rodando. Na aba de código do TinkerCAD, clique em "Monitor serial" na parte inferior da tela.  

<div align="center"><img src="https://i.imgur.com/874X1Gp.png"/></div>

<div align="center"><img src="https://i.imgur.com/gkp7gxl.png"/></div>

**Atividade:**  
Experimente usar o comando de escrever para enviar diferentes informações e variáveis para o serial.
{:.warning}