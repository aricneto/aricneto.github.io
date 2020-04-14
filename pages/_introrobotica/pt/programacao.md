---
layout: article
title: Estruturas de controle
permalink: /introrobotica/pt/programacao
key: intro-robotica-programacao
aside:
  toc: true
sidebar:
  nav: introrobotica
comments: true
---
# If

Imagine que você queira que um LED acenda somente se o ambiente estiver escuro, ou se alguém bater palmas, ou você queira que um robô vire para à direita se ele tiver a uma distância de 10 cm da parede. Para receber a informação do ambiente como distância, luminosidade, som é necessário o uso de sensores (estes serão temas de aulas posteriores). Porém, é necessário que no seu código, dentro do ambiente de programação do Arduino (IDE), sejam usadas algumas estruturas de controle. As estruturas de controle são blocos de instruções que alteram o fluxo de execução do código de um programa. Vamos iniciar nosso estudo com uma das estruturas de controle mais simples, o `if`.

**Descrição do IF:**  
**IF** significa **SE**, traduzindo do inglês para o português. O comando **if** verifica uma expressão e, apenas **se** ela for verdadeira, executa um conjunto de comandos, ou seja, ele executa uma lógica do tipo: "**se** isso for verdadeiro, **então** faça aquilo".
{:.info}

### Sintaxe

```c
if (condicao) {
  //aqui você deverá digitar o(s) comando(s)
}
```

**Parâmetros:**  
*condição*: uma expressão booleana, isto é, que pode resultar apenas em `true` (verdadeiro) ou `false` (falso).
{:.info}

### Exemplo 1 – Ligar um LED se o número digitado for maior que certo valor.

#### Circuito

O circuito da figura abaixo foi desenvolvido na plataforma TinkerCad e mostra um LED conectado a porta 9 do arduino em série com um resistor de 220 Ω.
<div align="center"><img src="https://i.imgur.com/1wsABkM.png"/></div>

#### Código

```c
/* Este é um exemplo simples para mostrar como usar a estrutura de controle "if" para o Arduino */
int LED1 = 9;
int controle = 11;
 
void setup() {
  pinMode(LED1, OUTPUT);
}
 
void loop() {
  if (controle > 10) {
    digitalWrite(LED1, HIGH);
  }
}
```

#### Analisando o código

No código, é definida uma variável do tipo `int` (numero inteiro) que recebe o nome `LED1` e um valor de `9`.

Em seguida, é definida outra variável do tipo `int`, que recebe o nome `controle` e um valor de `11`.

Dentro do `void setup()` é definido o modo de um dos pinos digitais do arduino como saída (`OUTPUT`) e o número do pino é o `LED1` que foi atribuído o valor `9`. Dessa forma, essa instrução diz ao arduino que o pino digital `9` deve ser definido no modo `OUTPUT`.

No `void loop()` foi utilizado a estrutura de controle `if`. Neste caso, é verificado se a condição `(controle > 10)` é satisfeita. Se for, o LED é acesso através do comando `digitalWrite(LED1, HIGH);`.

Como o valor de controle atribuído anteriormente foi 11, o LED acende.

#### Observações
As expressões sendo testadas dentro dos parênteses geralmente requerem o uso de um ou mais dos operadores mostrados abaixo.

**Operadores de comparação:**  
`x == y` (x é igual a y)  
`x != y` (x é diferente de y)  
`x <  y` (x é menor que y)  
`x >  y` (x maior que y)  
`x <= y` (x é menor ou igual a y)  
`x >= y` (x é maior ou igual a y)
{:.info}

**Cuidado para não usar acidentalmente o símbolo de igual simples (ex. `if (x = 10)`)!**  
O símbolo de igual simples (`=`) é o operador de atribuição:  
  `(x = 10)`, atribui 10 a x (coloca o valor 10 na variável x).  
O símbolo de igual duplo (`==`) é o operador de comparação:  
  `(x == 10)`, compara o valor x com a constante 10 (verifica se a variável x é igual a 10).
{:.info}

O primeiro comando mostrado resultará sempre em verdadeiro, enquanto que o segundo comando testará se x é igual a 10 ou não.

Isso acontece porque a linguagem C interpreta `if (x = 10)` da seguinte forma:  
10 é atribuído a x (lembre que o símbolo de igual simples é o `operador de atribuição`), então x agora contém 10.  
Então o comando `if` testa 10, o que sempre resulta `true`, já que qualquer número diferente de zero resulta em `true`. Consequentemente, `if (x = 10)` irá sempre resultar em `true`, o que não é desejável ao se usar um comando `if`. Além disso, a variável x irá receber o valor 10, o que também é indesejado.

**Exercícios**  
**1a:** Seguindo o exemplo 1, desenvolva um circuito e um código no Tinkercad para acender um LED vermelho quando o valor de determinada variável for maior que 10 e se for menor acenda um LED verde.  
**1b:** Modifique o programa do exercício 1 adicionando um LED amarelo de forma que ele acenda quando o valor da variável for igual a 10 (mantenha os outros LEDs e condições).  
{:.warning}

**Desafio:**  
Baseado no que você aprendeu sobre botões e o uso do “if”, desenvolva um circuito com um LED, um resistor e um botão. O LED só deverá acender se o botão for pressionado (estado HIGH). Para fazer esse desafio, você deverá usar o “if”.
{:.warning}


> **Referências:**
>
> 1. https://www.arduino.cc/reference/pt/language/structure/control-structure/if/ 
> 2. https://www.circuitar.com.br/tutoriais/programacao-para-arduino-primeiros-passos/#if  
> 3. https://www.tinkercad.com/  