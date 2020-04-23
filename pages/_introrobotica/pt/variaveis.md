---
layout: article
title: Entendendo variáveis
permalink: /introrobotica/pt/Qhd4hcr
key: intro-robotica-variaveis
aside:
  toc: true
sidebar:
  nav: introrobotica
comments: true
---
## Teoria

### Memória

Antes de falar sobre variáveis, vamos entender um pouco como elas são guardadas no *hardware* do Arduino:

Quando você chama um encanador para consertar um vazamento no seu banheiro, ele irá para sua casa com uma maleta de ferramentas, contendo todas as ferramentas que ele irá precisar para realizar o trabalho - um martelo, alicate, fitas... As vezes pode acontecer de faltar algum material, mas nada que uma rápida visita à um armazém não resolva.

Do mesmo jeito, quando você roda um código de computador, ele irá guardar as principais informações necessárias para o programa funcionar num lugar chamado *Memória RAM*. Dentro dessas informações, encontramos funções, variáveis, bibliotecas, e outras coisas. Assim como o encanador, pode acontecer de faltar alguma informação que não esteja na "maleta" (memória RAM). Estas informações são guardadas no disco rígido do computador (ou equivalente).

Imagine a memória RAM como uma "maleta" onde podemos guardar diversas "caixinhas" com diferentes conteúdos.

### Variáveis

Estas "caixinhas" que guardamos na memória RAM se chamam **variáveis**. Cada variável pode guardar **apenas um tipo de dado**. Isto é, uma variável que guarda números positivos não pode guardar letras ou numeros negativos. Tipos de dados comuns são:

|------+---------+---------|
| Tipo |Descrição| Exemplo
|------|:--------|:--------|
| int | número inteiro entre −32.767 e +32.767 | 42 |
| long | número inteiro entre −2.147.483.647 e +2.147.483.647 | -354.124 |
| float | número decimal | 3,14 |
| char | caractere | A |
| bool | valor verdadeiro ou falso | true |
|-----------------+------------|

Cada variável que criamos possui um **apelido**. Ele referencia a posição na memória onde a variável se encontra (ou, seguindo nossa analogia, onde está a caixinha dentro da maleta). A variável também precisa de um **valor**, que seria o conteúdo da caixinha (que deve estar de acordo com o tipo de dado que ela suporta).

**Importante:**  
Cada apelido deve ser único para cada variável (exceto em casos que iremos ver mais à frente)!  
O apelido de uma variável não pode começar com números `1Led` conter espaços `Led 1`, ou alguns caracteres especiais `#Led1`!  
O apelido também não pode ser uma palavra reservada, como `int`, `HIGH`, `OUTPUT`, `void`, etc.
{:.error} 

Por fim, a sintaxe para declaração de variáveis fica do seguinte modo:

`[TIPO] [APELIDO] = [VALOR];`
{:.info}

Segue alguns exemplos de declarações **válidas** de variáveis:

```c
int led1 = 10;
int led2 = 11;
int botao_1 = 5;
long tempo = 0;
char letra_a = 'A';
float num_pi = 3.14;
bool ceu_azul = true;
```

E alguns exemplos de declarações **inválidas**:

```c
num led1 = 10; // num não é um tipo de dado válido
int led 1 = 5; // apelidos não podem conter espaço
int 9botao = 2; // apelidos não podem começar com números
long void = 657; // apelidos não podem usar palavras reservadas
char letra_a = A; // caracteres char devem estar entre aspas simples ('A')
bool pato_real = verdadeiro; // variáveis booleanas só podem ser "true" (verdadeiro, ou 1) ou "false" (falso, ou 0)
```

**Exercícios:**  
**1a:** Declare um inteiro `int` com o apelido `joao`, e valor igual à `420`  
**2a:** Declare um inteiro longo `long` com o apelido `natal`, e valor igual à `25122020`  
**3a:** Declare um caractere `char` com o apelido `letra_b`, e valor igual à `B`  
**4a:** Declare um inteiro `int` com um apelido e valor válido  
**5a:** Declare um float `float` com um apelido e valor válido  
**6a:** Declare uma variável qualquer, com qualquer tipo, apelido e valor, válida  
{:.warning}

### Entendendo o computador

O computador fala uma linguagem diferente da nossa. O Arduino entende apenas sequências de zeros e uns. Por isso, antes do código ser enviado para a placa, o computador primeiro traduz todas as linhas de código em instruções que o Arduino possa compreender.

Quando chamamos uma variável em nosso código, o Arduino irá entender que ele deve encontrar o apelido dentro da memória RAM, e ler o que está guardado naquele lugar. Assim, se você declarou `int joao = 12` no começo do código, e mais tarde chamar `digitalWrite(joao, HIGH)`, o Arduino irá automaticamente traduzir a variável `joao` para o valor que foi dado à ela originalmente, e interpretar a linha de código anterior como `digitalWrite(12, HIGH)`.

Portanto, se declararmos o seguinte:

```c
int LED1 = 9;
int LED2 = 9;
int LED3 = 9;

void setup() {
    pinMode(LED1, OUTPUT);
    pinMode(LED2, OUTPUT);
    pinMode(LED3, OUTPUT);
}
...
```

Ele vai ser traduzido internamente para:

```c
// [codigo traduzido pelo arduino]
int LED1 = 9;
int LED2 = 9;
int LED3 = 9;

void setup() {
    pinMode(9, OUTPUT);
    pinMode(9, OUTPUT);
    pinMode(9, OUTPUT);
}
...
```

Ou seja, apenas declaramos o pino 9 como saída três vezes. O jeito correto de fazer, caso tenhamos 3 LEDs diferentes que queremos controlar individualmente, seria ligar cada LED à uma porta diferente (digamos: 9, 10 e 11), e declarar nossas variáveis de acordo com nossa ligação:

```c
int LED1 = 9;
int LED2 = 10;
int LED3 = 11;

void setup() {
    pinMode(LED1, OUTPUT);
    pinMode(LED2, OUTPUT);
    pinMode(LED3, OUTPUT);
}
...
```

Assim, teremos o resultado esperado:

```c
// [codigo traduzido pelo arduino]
int LED1 = 9;
int LED2 = 10;
int LED3 = 11;

void setup() {
    pinMode(9, OUTPUT);
    pinMode(10, OUTPUT);
    pinMode(11, OUTPUT);
}
...
```

### Operações com variáveis

Toda variável pode, por padrão, ser alterada a qualquer momento durante a execução do programa, a não ser que seja declarada com o modificador `const`, como `const int joao = 13`.

Logo, contanto que uma variável não possua esse modificador declarado, podemos fazer operações como adição, subtração, divisão, etc. E, após fazer estas modificações, alterar permanentemente o valor atribuido a ela. Por exemplo, se escrevermos:

```c
int joao = 9;

void setup() {
    pinMode(joao, OUTPUT);
    joao = 10;
    pinMode(joao, OUTPUT);
}
```

O código será interpretado como:

```c
// [codigo traduzido pelo arduino]
int joao = 9;

void setup() {
    pinMode(9, OUTPUT);
    joao = 10;
    pinMode(10, OUTPUT);
}
```

Pois, mesmo tendo declarado inicialmente `joao = 9`, alteramos para `joao = 10` no meio do código. Chamadas subsequentes dessa variável irão ser traduzidas para o valor `10`, a não ser que outra chamada mude o valor de `joao`. Tendo entendido esta parte, podemos passar para operações entre variáveis. Leia e tente interpretar o resultado de cada operação:

```c
int a = 10;
int b = 6;
int c = 16;
int d = 24;
int e = 0;

void setup() {
    a = b;           // "a" fica igual a "b", ou seja, a == 6
    b = c + d;       // "b" fica igual a "c + d", ou seja, "b = 16 + 24"
    b = b - 4;       // "b" fica igual a "b - 24, ou seja, "b = 40 - 4"
    // daqui pra frente, tente ir acompanhando os valores de cada variável
    c = a - b;
    d = a + b + c;
    d = a + 10;
    e = b / 6;
}

...
```

**Exercicio:**  
Liste o valor final de cada variável do código acima depois de todas as operações.
{:.warning}

**Atenção:**  
Antes de continuar, veja a página sobre o <a href="/introrobotica/pt/8ITcboj">protocolo serial</a> para entender como vamos ler as variáveis no computador.
{:.error}

Vamos checar se sua resposta está certa. Rode no TinkerCAD o seguinte código:

```c
int a = 10;
int b = 6;
int c = 16;
int d = 24;
int e = 0;

void setup() {
    Serial.begin(9600);
    
    a = b;           // "a" fica igual a "b", ou seja, a == 6
    b = c + d;       // "b" fica igual a "c + d", ou seja, "b = 16 + 24"
    b = b - 4;       // "b" fica igual a "b - 24, ou seja, "b = 40 - 4"
    c = a - b;
    d = a + b + c;
    d = a + 10;
    e = b / 6;
  
  	Serial.println(a);
    Serial.println(b);
    Serial.println(c);
    Serial.println(d);
    Serial.println(e);
}

void loop() {
    // deixe aqui vazio
}
```

**Exercicio:**  
Experimente um pouco com outras operações, como multiplicação, divisão e ordem de operações.
{:.warning}