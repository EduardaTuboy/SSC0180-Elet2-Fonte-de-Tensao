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
$V_m_á_x = V_t_r_a_n_s_f_o_r_m_a_d_o_r \cdot \sqrt{2}-(2 \cdot 0,7V)$
$V_m_á_x = 18 \cdot \sqrt{2}-(1,4)$
$V_m_á_x = 24,06V$


### Esquema do diagrama da fonte
![image](https://github.com/EduardaTNardin/SSC0180-Elet2-Fonte-de-Tensao/assets/128496419/bbf88920-d824-407e-98b8-3a7f5e0b5204)



## Vídeo da fonte funcionando
Vídeo do funcionamento da fonte nesse [link](https://drive.google.com/file/d/1ItndYaJXKqj53ECNaNRtKMORyY3nLMsF/view?usp=sharing)

































