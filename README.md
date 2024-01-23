# Motor-Inducao-Trifasico
Acionamento de motor de indução trifásico.

## Introdução
Sistemas de elevação são recursos muito utilizados no transporte de carga em galpões 
produtivos e a automatização de seu acionamento implica em maior confiabilidade e agilidade 
no processo de transporte. 
Uma vez que a implementação desse sistema não pode ser propriamente executada na ausência 
de um projeto adequado, este documento possui tanto o objetivo de sintetizar o processo de 
elaboração e simulação do diagrama de ligações, realizado com auxílio do software CADe
Simu, quanto de realizar as especificações do motor de indução selecionado.

## Diagrama elétrico
Na imagem representada abaixo é possível observar o diagrama elétrico usado para garantir 
a automação do sistema proposto, cujos componentes serão detalhados a seguir.

<div align="center">
<img src ="https://github.com/Brenoaalencar/DAC_R2R_8bits/assets/72100554/32d508b7-b671-4e6a-83bc-b2fdfb7cf9cf" width="600px"/>
</div>

Para realização do diagrama elétrico de acionamento foi escolhida a topologia estrela, na qual 
as fases W2, U2 e V2 do diagrama se encontram curto-circuitadas. Para acionar o motor é 
necessário que os fusíveis representados em F1 estejam fechados com o circuito, garantindo 
energização do circuito de potência. Além disso, a presença do relé térmico (RT) também 
garante uma maior segurança desse circuito, possibilitando o monitoramento da temperatura 
do sistema e auxiliando na indicação de eventuais falhas térmicas.

Para a movimentação de subida e descida do elevador são usadas as botoeiras de chamada 
indicadas como “sobe” (S1) e “desce” (S2), responsáveis pela ativação dos contatores K1 e K2
que garantem a inversão do sentido de rotação do motor, que permanecerá ativado até que outro 
comando seja dado pelo usuário ou até que as chaves fim de curso (FC1 e FC2), que são do 
tipo NF (normalmente fechadas), sejam atingidas.

Uma característica importante a respeito de tais botoeiras de comando consiste na presença de
intertravamento, que se estende também aos contatores K1 e K2 presentes na interface de 
potência. O intertravamento é essencial para realização do projeto, uma vez que impede que 
ocorra o acionamento simultâneo dos comandos “sobe” e “desce”, que implicaria na ativação 
de ambos os contatores ao mesmo tempo, podendo gerar danos significativos ao circuito, 
diminuindo consistentemente não somente a confiabilidade do sistema e sua integridade, mas
também a segurança do operador. Além disso, é possível verificar que existem alguns 
dispositivos adotados com o intuito de garantir a segurança do usuário como por exemplo o 
botão de emergência (SE).

O botão de emergência escolhido apresenta dois contatos distintos, de forma que ao pressionálo, um outro contato é fechado, possibilitando a alimentação de um circuito de sinalização e 
acendendo um led vermelho, de forma a informar o operador que o sistema se encontra em 
estado de emergência. 
Quanto aos led adotados foram escolhidas 3 diferentes cores. Na representação o amarelo 
sinaliza a falha térmica, o verde se o motor está em modo de operação (tanto para subida como 
descida) e o vermelho, por fim, sinaliza se o estado de emergência está ativado, como 
previamente citado.

Por fim, outra informação importante a respeito do sistema é que ele foi desenvolvido conforme 
a norma de segurança NR-12, o que implica no uso de uma fonte DC de 24V para a alimentação 
dos componentes dispostos no painel de comando, para viabilizar isso foi usado um conversor 
de tensão AC/DC, conectado na fase L1 por meio do fusível F2, no neutro e na proteção 
elétrica.

## Especificações do motor
O motor sugerido para automatizar o elevador foi um o Motor de Indução Trifásico 6(MIT) de 
380V/60Hz da Weg de 1 cv de potência mecânica e de potência ativa igual a 𝑃𝑎 = √3 ⋅ 𝑈 ⋅ 𝐼 ⋅
cos(𝜑), sendo U a tensão, I a corrente e cos(𝜑) o fator de potência, logo 𝑃𝑎   = 932,96 𝑊 . Por 
fim a potência útil será 𝑃𝑢 = 𝜂 ⋅ 𝑃𝑎𝑃𝑢 = 𝜂 ⋅ 𝑃𝑎 =  0,805 ⋅ 932,96  =  0,75 𝐾𝑊 da placa.

<div align="center">
<img src ="https://github.com/Brenoaalencar/DAC_R2R_8bits/assets/72100554/dd541ce4-e0b1-466d-a63a-a185bd2e6676" width="500px"/>
</div>

Por meio da placa de identificação, pode-se notar que se trata de um motor de 4 polos, pois 
como a velocidade síncrona (Ns) é a soma da velocidade nominal (1730 RPM da placa) com 
o escorregamento (resultando em 1800 RPM) e o número de polos é dado por: 𝑛𝑝 =
120⋅𝑓𝑟𝑒𝑞𝑢ê𝑛𝑐𝑖𝑎[𝐻𝑧]
𝑁𝑠
, logo temos 𝑛𝑝 =
120⋅60
1800
=  4 𝑝𝑜𝑙𝑜𝑠.
O motor é de categoria N, de baixo escorregamento e corrente de partida normal. O 
Conjugado Básico (𝐶𝑜) é dado por:
𝐶𝑜 =
736⋅𝑃(𝑐𝑣)
𝑛𝑠
, sendo P a potência nominal do motor e 𝑛𝑠 a rotação síncrona, portanto 𝐶𝑜 =
736⋅1
1800
= 0.409 𝑘𝑔𝑓. 𝑚.
