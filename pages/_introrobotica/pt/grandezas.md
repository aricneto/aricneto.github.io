---
layout: article
title: Grandezas Elétricas
permalink: /introrobotica/pt/j03JdPL
key: intro-fisica-grandezas
aside:
  toc: true
sidebar:
  nav: introrobotica
comments: true
---
# Noções Básicas

Provavelmente você já deve ter ouvido falar em uma dessas grandezas: corrente elétrica, tensão elétrica, resistência elétrica e potência elétrica. Se não ouviu, pelo menos já usou elas no seu dia-a-dia. Vamos a partir de agora aprender o que são essas grandezas, pois elas serão utilizadas ao longo do projeto de robótica. Para adquirir as primeiras noções sobre elas, assista o vídeo abaixo:

<div align="center">
<iframe width="80%" height="315" src="https://www.youtube.com/embed/JtttnL28m3Q" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

## Introdução

Quando você liga um dispositivo eletrônico é necessário que para ele funcionar, exista uma fonte de tensão (bateria, pilha, “tomada”). Essa fonte de tensão é responsável por fornecer energia elétrica para o dispositivo. Por exemplo, para acender a lâmpada da animação ao lado está conectada uma pilha (fonte) a ela. Mas afinal, o que acontece a nível “microscópico” quando eu ligo essa fonte? Para entender isso precisamos compreender de que são constituídos os materiais.

<div align="center"><img src="https://i.imgur.com/LsIs7nG.gif"/></div>

### Estrutura Atômica

Os materiais são constituídos por partículas pequenas chamadas de **átomos**. De forma simplificada, os átomos são compostos por **elétrons**, **prótons** e **nêutrons**. Os prótons possuem carga elétrica positiva e os nêutrons não possuem carga elétrica. Estes compõem o núcleo do átomo. Já os elétrons, possuem carga elétrica negativa e “orbitam” o núcleo. A figura abaixo ilustra como é a estrutura do átomo.

<div align="center"><img src="https://i.imgur.com/ndmOJ6O.gif"/></div>

### Condutores e Isolantes

Os materiais podem ser classificados eletricamente em **condutores** e **isolantes**. (Existem outros materiais que não se encaixam dentro dos condutores e isolantes, que são chamados de semicondutores, mas não vamos falar deles aqui agora).

Os **isolantes** se caracterizam por não permitirem que as cargas elétricas se movimentem com facilidade. Podemos citar como exemplo a borracha e o plástico.  
Os **condutores** elétricos permitem que os elétrons se movimentem com mais facilidade. Podemos citar exemplos de bons condutores elétricos os metais como: a prata, o ouro, o cobre, etc.

No simulador abaixo, veja o que acontece com a lâmpada ao clicar em cada um dos materiais para completar o circuito.

<div align="center">
<iframe width="60%" height="440" src="https://www.edumedia-sciences.com/en/media/frame/515/?auth=bfb2bccebeeb6a55cbbdfb04a8979bda/24964" frameborder=0></iframe>
</div>

# Grandezas Elétricas

## Corrente

Uma grandeza física importante que você irá utilizar bastante é chamada de corrente elétrica. A corrente elétrica pode ser entendida como um movimento ordenado de cargas elétricas. Nos metais, as cargas elétricas que se movimentam ordenadamente são os elétrons livres. A animação abaixo mostra os elétrons livres se movendo ordenadamente em um condutor elétrico.

<div align="center">
<video autoplay loop muted playsinline>
  <source src="https://i.imgur.com/uCDSpnM.mp4" type="video/mp4">
</video>
</div>

A corrente elétrica é quantificada através de sua intensidade. A intensidade da corrente elétrica (chamaremos apenas de corrente elétrica), que representaremos pela letra *i*, está relacionada com a quantidade de cargas elétricas que atravessam uma região de um condutor a cada segundo.

A unidade de medida padrão de corrente elétrica é o **Ampére**. Usaremos a letra “A” para indicar essa unidade de medida. Nos nossos circuitos eletrônicos, a corrente elétrica é baixa e usaremos submúltiplos do Ampère como o **miliampère (mA)** e o **microampère (𝛍A)**.

1 miliampère = 1 mA = 0,001 A = $$10^{-3} A$$  
1 microampère = 1 𝛍A = 0,000001 A = $$10^{-6} A$$

### Contínua e alternada

De forma simplificada, corrente elétrica contínua (CC, ou em inglês DC - “direct current”) não muda de sentido. Se a corrente contínua é constante, além do sentido não mudar, sua intensidade não varia ao longo do tempo. 
Já a corrente alternada (CA, ou em inglês AC - “alternating current”) não muda de sentido ao longo do tempo.

As animações abaixo ilustram como a corrente se comporta em um circuito DC (figura acima) e em um circuito AC (figura abaixo). 

<div align="center"><img src="https://i.imgur.com/kAzurZh.gif"/></div>

<div align="center"><img src="https://i.imgur.com/0DMPX53.gif"/></div>

### Submúltiplos da corrente

Converta:

a) 500 mA para A

$$500 mA = 500 \times 10^{-3}  = 500 \times 0.001 = 0.5 A$$

b) 0,2 A para mA

$$0.2 A = 0.2 \times 10^3 = 0.2 \times 1000 = 200 mA$$

c) 0,00004 A para 𝛍A

$$0.00004 A = 0.00004 \times 10^6 = 0.00004 \times 1000000 = 40 𝛍A$$

## Diferença de Potencial (ddp)

Falamos anteriormente que a corrente elétrica é o movimento ordenado de cargas elétricas. Mas, o que provoca esse movimento ordenado?

A resposta da pergunta acima é a **diferença de potencial elétrico**, também chamada de **ddp**, **voltagem** ou **tensão elétrica**. Essa ddp é fornecida pela fonte de tensão (bateria, pilha, tomada) quando você a conecta no circuito.

Representaremos a ddp pela letra **U**. A unidade de medida de ddp é o Volts (V).  

As fontes de tensão podem fornecer uma tensão contínua ou uma tensão alternada. Nos circuitos que serão criados nos projetos, utilizaremos fontes de tensão contínua.

## Resistência

Podemos definir a resistência elétrica como uma grandeza física que é caracterizada pela dificuldade que um condutor pode oferecer à passagem de corrente elétrica.

A resistência elétrica R está relacionada com a corrente elétrica e a ddp de acordo com a seguinte relação:

$$R = \frac{U}{i}$$

A unidade de medida de resistência é o Ohm representada pela letra grega ômega cujo símbolo é 𝛀.

Quando variamos a ddp U nos terminais de um condutor a corrente também irá variar. Se a resistência permanecer constante quando variamos a tensão (e por consequência a corrente), dizemos que o condutor é ôhmico.

### Resistores

Os resistores são dispositivos que tem por função limitar a passagem de corrente elétrica em um trecho do circuito.

Ele possui diversos formatos (veremos outros mais na frente), mas o mais comum é mostrado na figura ao lado. Eles possuem dois terminais (“perninhas”) que podem ser ligados ao circuito em qualquer posição (não tem polaridade).

Chuveiros elétricos, lâmpadas incandescentes, churrasqueiras elétricas e outros dispositivos que podem ser encontrados na nossa casa possuem resistores que costumamos chamar de resistência.

#### Código de cores

No corpo dos resistores existem listras coloridas. Essas listras servem para identificar qual o valor de sua resistência elétrica.

A tabela abaixo mostra o código de cores para resistores que possuem quatro listras. As duas primeiras listras correspondem aos dígitos significativos, a terceira ao multiplicador e a quarta à tolerância.

<div align="center"><img src="https://i.imgur.com/LEnsjSp.png"/></div>

#### Exemplo - Determinando a resistência de um resistor a partir do código de cores

Para determinar a resistência a partir do código de cores, deve-se posicionar a faixa mais afastada das outras para o lado direito. A leitura começa pelas faixas da esquerda. Vamos ver como se faz a leitura do exemplo abaixo:

<div align="center"><img src="https://i.imgur.com/N5WrKXO.png"/></div>

1° faixa cor azul = 6  
2° faixa vermelho = 2  
3° faixa vermelho = 102 = 100  
4° faixa cor dourado = 0,5% (tolerância)

### Múltiplos do Ohm

Muitas vezes precisamos escrever esses valores em termo dos múltiplos, utilizando os prefixos  k (quilo) e M (mega). Quando o prefixo k está antes da unidade, significa que o valor está sendo multiplicado por mil. Lembre-se de quilômetro. 2 km é igual a  2 x 1000 m = 2000 metros.  
No exemplo anterior, utilizando o código de cores, encontramos a resistência do resistor como sendo 6200 𝛀 e tolerância de 5%. Esse valor poderia ser escrito da seguinte forma:

$$6200 𝛀 =  6,2 \times 1000 = 6.2 \times 10^3  = 6.2 k𝛀 \rightarrow 6.2 quiloohms$$

Já quando prefixo M encontra-se antes da unidade, significa que o valor está sendo multiplicado por 1000000 (um milhão). Por exemplo:

$$3000000 𝛀 =  3 \times 1000000 = 3 \times 10^6 = 3 M𝛀 \rightarrow 3 megaohms$$

Logo temos 62 × 100 = 6200. isso significa que temos um resistor de 6200 𝛀 com uma tolerância de +-5% (5% de 6200 𝛀 é 310 𝛀).

# A lei de Ohm

Georg Simon Ohm realizou várias experiências utilizando condutores elétricos. Através dessas experiências percebeu que quando aplicava uma ddp nos terminais de um condutor, uma corrente passava a circular por esse condutor. Quando aumentava a ddp, a corrente passava a aumentar proporcionalmente. Então:

$$\frac{U_1}{i_1} = \frac{U_2}{i_2} = \frac{U_3}{i_3} = R$$

Vamos entender como seria isso utilizando o simulador abaixo:  
Modifique o valor da ddp e veja o que acontece com a corrente e com a resistência elétrica.

<div align="center">
<iframe width="80%" height="440" src="https://phet.colorado.edu/sims/html/ohms-law/latest/ohms-law_pt_BR.html" frameborder=0></iframe>
</div>

Dessa forma, podemos relacionar as grandezas, diferença de potencial, corrente e resistência elétrica através da seguinte expressão:

$$U = R \times i$$

U → ddp - tem como unidade padrão o Volt (V);  
R → resistência elétrica - tem como unidade padrão o Ohm (𝛀);  
i → intensidade da corrente elétrica - tem como unidade padrão o Ampère (A).

# Circuito Elétrico

Circuito elétrico é um caminho fechado percorrido pela corrente elétrica, que na sua forma mais simples é formado por:

Um gerador (dispositivo que converte alguma forma de energia em elétrica - Ex. bateria, pilha)  
Um condutor, responsável por ligar os elementos do circuito (Ex. fios) e a carga (não confundir com carga elétrica)  
Um dispositivo que converte energia elétrica em outra forma de energia (lâmpadas, motores).

Perceba que para a lâmpada acender, o circuito elétrico deve estar fechado, como mostrado na figura da direita. Na figura da esquerda a lâmpada não acende.

<div align="center"><img src="https://i.imgur.com/ou5uhZn.png"/></div>

<div align="center">
<iframe width="80%" height="440" src="https://phet.colorado.edu/sims/html/circuit-construction-kit-dc/latest/circuit-construction-kit-dc_pt_BR.html" frameborder=0></iframe>
</div>


> **Referências:**  
> https://phet.colorado.edu/sims/html/circuit-construction-kit-dc/latest/circuit-construction-kit-dc_pt_BR.html  
> https://www.youtube.com/watch?v=ZAFW4zdXpbY 

