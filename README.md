View this project on [CADLAB.io](https://cadlab.io/project/30194). 

# Projecte Maleter 

>**Autors: Alba Martin i Mireia Campanera
>**Versió: 

----------

## Objectiu

>PCB per 
 - Obrir i tancar el maleter amb un motor
 - Detectar el peu sota el cotxe per obrir-lo
 - Activar el calefactor del vidre del maleter
 - Detectar objectes per evitar atrapaments

## Diagrama de blocs
![Diagrama de blocs](C:\Users\User\Desktop\UB\2N\eines de disseny\projecte\edd-project-grup-dimecres-dc_b_malater\DIAGRAMA DE BLOCS.png)
### Descripció/funcionalitat de cada bloc

  * El motor pot funcionar amb 12V de la bateria, però el microcontrolador en necessita 3.3V, per tant hem de posar reguladors de tensió que la redueixin.[Baixem de 12 a 5V (LM2596)] [Baixem de 5 a 3.3V (LM1117)]
  * Motor DC: un motor DC té dos cables, quan connectem una bateria, connectem un a 12V i l’altre a GND, i el motor comença a girar en un sentit. Què passa si canviem els cables? si invertim la polaritat, el motor gira cap a l’altre costat. Això ho necessitem perquè el maleter necessita dues accions: obrir i tancar. Per tant el motor ha de poder girar: sentit 1 —> obrir,, sentit 2—> tancar.
  * DRIVER DE MOTOR (H-Bridge):
El driver és un circuit que ens permet:
controlar el motor
canviar el sentit de gir*
controlar la velocitat (PWM)
En el nostre cas utilitzarem el DRV8871
  * SENSOR D’OBERTURA AMB EL PEU:
El cotxe detecta el peu sota el para-xocs, això ho fa amb un sensor de distància. Nosaltres hem triat el ToF VL53L0X  (Time of Flight). Mesura la distància amb llum infraroja. Aquesta informació la envia al micro amb un sistema de comunicació anomenat I2C, aquest, permet que dos circuits parlin entre ells. Només necessita dos cables: SDA(Serial Data), cable per on passen les dades i SCL(Serial Clock), cable que marca el ritme de comunicació.
  * SENSOR DE FINAL DE CARRERA:
Detecta si el maleter està totalment obert. És simplement un interruptor mecànic, quan el maleter està tancat l’interruptor està en OFF, quan està obert està en ON. 
  * SENSOR ANTI-ATRAPAMENT:
Evita que t’atrapis la mà amb el maleter.
Això ho evitarem detectant quan el motor està bloquejat (per una mà atrapada). Quan el motor es bloqueja la corrent del motor augmenta molt, detectant aquest augment de corrent és com evitarem l’atrapament. Això ho farem amb un circuit de tres parts:
Resistència molt petita (0.05Ω) entre el motor i el GND
quan passa corrent per una resistència tan petita la tensió serà proporcional al corrent que circuli per aquesta. Per tant, si circula un corrent normal (petit) obtindrem tensió petita.
Amplificador INA180
aquest tensió és massa petita per al micro, per això necessitem un amplificador de corrent. Així el micro ho podrà mesurar.
Microcontrolador
el micro rep aquesta tensió al seu ADC. L’ ADC és un pin que pot mesurar voltatge.
  * CALEFACTOR DEL VIDRE:
El vidre del maleter té una resistència calefactora que funciona amb 12V i 3A - 5A, per tant el microcontrolador no pot alimentar-lo directament, hem de fer servir un MOSFET. Aquest funciona com un interruptor electrònic, quan el micro activa el MOSFET el calefactor s’encén.


-----------

## Requisits / Especificacions

  * Alimentació; 12V, regulada 5V (LM2596), regulada 3.3V (LM1117)
  * Microcontrolador PIC24HJ128GP502
  * Driver Motor DRV8871
  * Sensor d'obertura amb el peu ToF VL53L0X  
  * Sensor final de carrera microswitch kw11
  * Sensor anti-atrapament (amplificador INA180)
  * Calefactor (mosfet)
  * Comunicació Can MCP2551

-----------

## Components (Veure datasheets en la carpeta datasheet)

| Descripci&#243; | Ref | Package |Datasheet | Prove&#239;dor | Preu | Unitats |
| --- | --- | --- | --- | ---| --- | --- |
| Microcontrolador | PIC18F26Q83-I/SS | SOIC-28 |[Datasheet](https://www.mouser.es/datasheet/2/268/PIC18F27_47_57Q83_Preliminary_Data_Sheet_40002265B-2887591.pdf) | [Mouser](https://www.mouser.es/c/?q=PIC18F27Q83-I%2FSO)| 2,17&euro;| 1x |
| XTAL-Ressonador | CSTCR7M99G53-R0 | SMD |[Datasheet](https://www.mouser.es/datasheet/2/281/p16e-522700.pdf) | [Mouser](https://www.mouser.es/ProductDetail/Murata-Electronics/CSTCR7M99G53-R0?qs=Zd9RUO93%2Fo7cnwzsujIkpA%3D%3D)  | 0,27&euro; | 1x |

-----------

## Software

### Eines:

  * KiCad 9.0 o superior
  * 

### Configuraci&#243; :

  * 

### Funcionalitats:

  * 

-----------


## Historial de canvis

| Data | Autor     | Branch | Versi&#243; | Descripci&#243; |
| --- | --- | --- | --- | --- |
|  28/03/2023 | mlopez | Master | initial commit | Primera versi&#243; d'esquem&#224;tic i selecci&#243; de components |
