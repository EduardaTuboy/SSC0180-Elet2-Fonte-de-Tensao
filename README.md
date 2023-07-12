# Trabalho 1 - Fonte de tensão variável
Projeto realizado para a disciplina Eletrônica para Computação [SSC0180], ministrado pelo docente [Eduardo Vale Simões](https://gitlab.com/simoesusp), durante o primeiro semestre do curso de Bacharelado em Ciências de Computação, na USP campus São Carlos.

## Integrantes do Grupo 8
* [Eduarda tuboy Nardin](https://github.com/EduardaTNardin) | nº USP 13732495
* [Gabriel Barbosa dos Santos](https://github.com/GotemBarbosa) | nº USP 14613991
* [Guilherme Antonio Costa Bandeira](https://github.com/Guilherme-Bandeira) | nº USP 14575620
* [Rafael Brazolin Alvez Mansur](https://github.com/RafaelMansurUsp)| nº USP 14604020
* [Renan Parpinelli Scarpin](https://github.com/RenanScarpin)| nº USP 14712188

## Objetivo
Montar em uma *protoboard* um circuito que recebe como entrada uma corrente alternada de 127V e retorna como saída uma corrente contínua ajustável entre 3V a 12V, com capacidade de 100mA de corrente.

## Diagrama de fonte no Falstad
![circuit-20230623-2040](https://github.com/EduardaTNardin/SSC0180-Elet2-Fonte-de-Tensao/assets/128496419/eff1741d-a03e-48c7-b863-e95b94549229)
Link do circuito no Falstad [aqui](https://tinyurl.com/2mkt75e9).

## Escolha dos Componentes
Todos os componentes, menos o cabo conectado ao transformador, foram comprados na loja “Ca And Ma Componentes Eletrônicos”, localizada em São Carlos.

Quantidade | Componente | Especificações | Preço Unidade
--- | --- | --- | ---
1 | Transformador | Trafo Bivolt 18+18v 500mA | R$ 41,90
1 | Ponte Retificadora | KBP206 2A 600V Tower | R$ 3,80
1 | Capacitor | Elco 680 µF 25V | R$ 5,80
1 | LED | Cristal, cor vermelha | R$ 1,30
1 | Diodo Zenner | 1N47430 [ 13V \ 1W ] | R$ 0,48
1 | Transistor NPN | BD137 [ 60V \ 1,5A ] | R$ 1,40
1 | Potenciômetro 5K | 1W \ B5K | R$ 7,00
2 | Resistor 1K | CR25 Carvão LGE | R$ 0,14
1 | Resistor 2.7K | CR25 Carvão | R$ 0,07
1 | Resistor 6.8K | CR25 Carvão Rohs | R$ 0,07
10 | Jumpers | Femea x Macho | R$ 0,70
1 | Protoboard | BB-01 400P Sem base tower | R$ 20,40
Total | | | R$ 89,36

## Projeto no Software Eagle

## Cálculos e Montagem
De início, é necessário saber a razão Ns / Np, utilizado nas definições do Falstad, sendo Ns número de espiras do enrolamento da bobina secundária e Np número de espiras do enrolamento da bobina primária. Essa razão se dá pela relação:

$\frac{V_p}{N_p}=\frac{V_s}{N_s}$

$\frac{127}{N_p}=\frac{18}{N_s}$

$\frac{N_s}{N_p}=\frac{18}{127} = 7,05$

Depois, é calculada a tensão de pico do circuito, que é a voltagem que sai do transformador vezes raiz de dois subtraindo duas vezes o valor 0,7V, que é a quantidade de tensão dissipada por cada diodo, e já que em cada ciclo a corrente passa por 2 diodos, é necessário multiplicar 0,7V por dois:

$V_{máx} = V_{transformador} \cdot \sqrt{2}-(2 \cdot 0,7 V)$

$V_{máx} = 18 \cdot \sqrt{2}-(1,4)$

$V_{máx} = 24,06 V$

Em seguida, inicia-se a montagem e cálculo do circuito pelo diodo zener, visto que tal componente requer o mínimo de valor de corrente que passa por ele, caso contrário ele pode queimar, e também que passe uma tensão maior que 13V, para que o zener de 13V consiga ligar e fixar a corrente passada por ele em 13V. Assim, com essas condições, foi utilizado o Falstad para ajustar o resistor acima do diodo zener de forma que atinja um valor de resistor comercial e as especificações, sendo este valor 2,7K $\Omega$.

Após isso, foi calculado o resistor logo abaixo do potenciômetro, sendo este necessário para regular o range do potenciômetro entre 3V e 12V, visto que sem tal resistor o range vai de 0V até 13V. Testando no Falstad, chegou-se em 2,2K $\Omega$, porém devido a problemas de mal-contato ocasionados pelos grandes pinos do potenciômetro, foi colocado dois resistores de 1K $\Omega$ em série para gerar 2K $\Omega$ de resistência a fim da fonte entregar 3V quando estiver no mínimo do potenciômetro.

Para calcular o resistor do LED, foi ajustado através do Falstad o valor do resistor que faz com que passe o mínimo de corrente possível e ainda faça com que o LED funcione, sendo esse valor 3mA. Logo, foi concluído que o resistor precisa ser do valor de 6,8K $\Omega$.

Para calcular a capacitância do capacitor, foi utilizado a seguinte fórmula:

$C = Io \cdot (2 \cdot f \cdot V_s \cdot ripple)^{-1}$

* Io - Corrente de saída do capacitor
* V_s - Tensão de pico
* Ripple - Voltagem de ripple
* f - Frequência da fonte

Para a obtenção da corrente, são somadas a corrente no led, no diodo zener e na saída do carregador, todas obtidas pela primeira lei de ohm.

$Io = I_{led} + I_{zener} + I_c$

$I_{led} = \frac{24,06V - 3,1V}{6800\Omega}=0,0031A=3,1mA$

$I_{zener} = \frac{24,06V - 13V}{2700\Omega}=0,0041A =4,1mA$

$I_c = pela_especificação do problema = 100mA $

$Io = 3,1mA + 4,1mA + 100mA = 107,2mA$

Voltando á fórmula do capacitor:

$C = Io \cdot (2 \cdot f \cdot V_s \cdot ripple)^-1$

$C = 0,1072 \cdot (120 \cdot 24,06 \cdot 0,06)^-1$

$C = $0,0006188233F=618,82 \mu F

### Esquema do diagrama da fonte
![image](https://github.com/EduardaTNardin/SSC0180-Elet2-Fonte-de-Tensao/assets/128496419/bbf88920-d824-407e-98b8-3a7f5e0b5204)



## Vídeo da fonte funcionando
Vídeo do funcionamento da fonte nesse [link](https://drive.google.com/file/d/1ItndYaJXKqj53ECNaNRtKMORyY3nLMsF/view?usp=sharing)

































