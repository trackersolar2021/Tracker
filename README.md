# Tracker
## Circuito completo
![TCC](Images/TCC2021.PNG)

## Pinos utilizados
 - DHT11 = pino digital 9
 - Sensor de tensão tracker = pino analogico A8
 - Sensor de tensão fixo = pino analogico A9
 - Sensor de tensão motor = pino analogico A10
 - Sensor de corrente tracker = pino analogico A3
 - Sensor de corrente fixo = pino analogico A4
 - Sensor de corrente motor = pino analogico A5
 - Fim de curso 1 = pino digital 2
 - Fim de curso 2 = pino digital 3
 - RTC SDA = pino digital 20
 - RTC SLC = pino digital 21
 - Motor step = pino digital 7
 - Motor dir = pino digital 8
 - Motor Enable = pino digital 10
 - LDR esquerda baixo = pino analógico A12
 - LDR esquerda topo = pino analógico A15
 - LDR direita baixo = pino analógico A13
 - LDR direita topo = pino analógico A14

## DHT11
 - Foi utilizado a biblioteca dht11 para facilitar a leitura da umidade e temperatura;
 - O sensor dht11 está sendo lido no pino digital 9;
 - A leitura do sensor está dentro da função readSensors() que está sendo chamada dentro do loop;
### Esquemático
![esquematico_dht11](Images/DHT11.PNG)

NÃO COLOCAR RESISTOR para o dht11 que só possui 3 terminais.

## Sensor de Tensão
 - Foi utilizado um divisor de tensão que permite ler uma tensão de até 60V;
 - Para esse circuito foram utilizados um resistor de 220KΩ (R1) e um resistor de 20KΩ (R2);
 - Os sensores de tensão estão conectados nas entradas:
   - A8: Painel fotovoltaico Tracker;
   - A9: Painel fotovoltaico Fixo;
   - A10: Motor;
 - O valor da tensão é calculado pela função readVoltage.
### Esquemático
![Sensor de tensao](Images/Sensordetensao.png)

## Sensor de corrente
 - Foi utilizado o sensor ACS712-30A
 - Os sensores de corrente estão conectados nas entradas:
   - A3: Painel fotovoltaico Tracker;
   - A4: Painel fotovoltaico Fixo;
   - A5: Motor;
 - O valor da corrente é calculado pela função readCurrentSensor.
### Esquemático
![Sensor de corrente](Images/corrente.PNG)

## Motor
 - Pinos de step, direção e enable são conectados aos pinos digitais 7, 8 e 10 respectivamente;
 - É preciso testar para ver quantos pulsos será preciso para cada angulo;
 - Os valores dos pulsos deverão ser colocados nas váriaveis:
   ```
   const unsigned long leaveLimitSwitch1 = 10000; // solta fim de curso
   const unsigned long revolution2Position = 128270; // posição 2
   const unsigned long revolution3Position = 168918; // posição 3
   const unsigned long revolution4Position = 54957; // posição 4
   const unsigned long revolution5Position = 49497; // posição 5
   const unsigned long revolution6Position = 113639; // posição 6
   const unsigned long revolution7Position = 81425; // posição 7
   const unsigned long arriveLimitSwitch2 = 10000; // bate fim de curso 2
   const unsigned long leaveLimitSwitch2 = 5569; // solta fim de curso 2
   const unsigned long leaveLimitSwitch2 = 10000; // solta fim de curso 2
   const unsigned long restPosition = 256427; // posição de descanço
   const unsigned long arriveLimitSwitch1= 400000; // posição inicial
   ```
### Esquemático
![Motor](Images/corrente2.PNG)
## Armazenamento de dados
 - Foi utilizado o cartão SD para o armazenamento de dados;
 - Foi utilizado o pino digital 4;

## RTC
 - Foi realizado implementação utilizando a biblioteca Wire e tratando o valor recebido do RTC com comunicação I2C;

## Ajuste fino
![Ajuste fino](Images/LDR.PNG)
![Ajuste fino](Images/LDR2.PNG)

 - Para instalar os LDR's é preciso escolher quais serão os 2 LDR's da direita e quais serão da esquerda pois o calculo do ajuste fino será comparando os LDR's da direita com os da esquerda;
 - No momento da instalação é necessário verificar a direção do motor, pois no código assumi que a direção HIGH é para a direita e a direção LOW é para a esquerda;

## Referências
 - dht11: https://create.arduino.cc/projecthub/arcaegecengiz/using-dht11-b0f365

 - Sensor de tensão: https://br-arduino.org/2015/06/voltimetro-com-arduino-como-montar-programar-e-calibrar.html

 - Sensor de corrente: https://www.electronicshub.org/interfacing-acs712-current-sensor-with-arduino/

 - Motor : https://www.robocore.net/tutoriais/controlando-motor-de-passo

 - Armazenamento de dados: https://scholarslab.lib.virginia.edu/blog/saving-arduino-sensor-data/

 - RTC: http://projectsfromtech.blogspot.com/2013/06/arduino-rtc-tinyrtc-v1-with-arduino.html

 - LDR: https://www.filipeflop.com/universidade/kit-maker-arduino/projeto-10-sensor-de-luz-ambiente/

 - Artigo e dados: https://www.dropbox.com/sh/pjw48whlda5b5aj/AAAHGorWxIQ7ePcbdcptORiXa?dl=0
