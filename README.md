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

  *

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
