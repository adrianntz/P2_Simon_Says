# P2_Simon_Says
Proiect Simplu proiectat cu microcontroller AVR ATMEGA164A pentru a creea un joc simplu de tip Simon Says, folosind 4 butoane pentru user input si 4 led-uri pentru system output. 

## Inspiratie Proiect
Ideea de functionare a jocului a fost preluata din acest proiect pe arduino:

[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/xLLTxN_UBnI/0.jpg)](https://www.youtube.com/watch?v=xLLTxN_UBnI)

https://youtu.be/xLLTxN_UBnI

## Firmware Architecture
Bootloader-ul pentru Atmega164A este deja incarcat inainte de primirea chip-ului. Firmware-ul poate fi flashed folosind programul AvrBuster.exe
Firmware-ul pentru Atmega164A este scris in C folosind compilatorul CodeVisionAVR ANSI C Compiler si IDE-ul CodeVisionAVR. Codul in C  a fost creat folosind Code Wizard-ul IDE-ului.
Pentru jocul Simon Says vom folosi doar Portul A al microcontrollerului. Astfel, cu Code Wizard am initializat Pinii PA0->3 ca input si conectati la rezistorul pull-up intern, acesti pini fiind conectati la switch-uri, iar pinii PA4->7 sunt de tip output prin care aprindem LED-urile.
Codul are ca structura principala doi vectori de lungime MAX_LEVEL, unul fiind lista de secvente a nivelului si al doilea fiind secventa introdusa de catre jucator.
Astfel, lungimea jocului poate fi setata folosind MAX_LEVEL. La pornirea firmware-ului se umple vectorul nivelului cu valori randomizate intre 0 si 4. De-a lungul jocului se completeaza si vectorul cu secventele introduse de jucator, si se vor compara ce doi vetori. In momentul in care se greseste o secventa sau se ajunge la lungimea maxima, se termina jocul si se reseteaza vectorii.
De asemenea Firmware-ul are implementat o dificultate a jocului, anume viteza afisarii secventei curente. Cu cat este mai avansat jocul intr-o secventa mai mare, aceasta viteza creste, facand jocul mai dificil cu cat te joci mai mult.

Utilizare Memorie Firmware:
EEPROM usage: 0 byte(s), 0.0% of EEPROM

Program size: 646 words (1292 bytes), 7.9% of FLASH

RAM Global variables size: 404 byte(s)

Estimated Data Stack usage: 6 byte(s)

(Informatie data de compilator)


## Hardware Schematic 
![Simon Says Schematic](https://user-images.githubusercontent.com/107213955/173852601-c4251566-8397-4a43-937b-b6ac5f7ba3bf.jpg)

## BOM 

| Component Count:               | 39   |                   |                                                            |                                                         |
|--------------------------------|------|-------------------|------------------------------------------------------------|---------------------------------------------------------|
| Ref                            | Qnty | Value             | Footprint                                                  | Description                                             |
| C1, C5,                        | 2    | 18p               | Capacitor_SMD:C_0805_2012Metric                            | Capacitor symbol for simulation only                    |
| C2, C4, C6, C11,               | 4    | 100n              | Capacitor_SMD:C_0805_2012Metric                            | Capacitor symbol for simulation only                    |
| C3,                            | 1    | 1u                | Capacitor_Tantalum_SMD:CP_EIA-3216-18_Kemet-A              | Polarized capacitor                                     |
| C7, C9,                        | 2    | 22p               | Capacitor_SMD:C_0805_2012Metric                            | Capacitor symbol for simulation only                    |
| C8,                            | 1    | 22u               | Capacitor_Tantalum_SMD:CP_EIA-3216-12_Kemet-S              | Capacitor symbol for simulation only                    |
| C10,                           | 1    | 10n               | Capacitor_SMD:C_0805_2012Metric                            | Capacitor symbol for simulation only                    |
| D1,                            | 1    | RED LED           | LED_SMD:LED_0805_2012Metric                                | Light emitting diode                                    |
| D2, D6,                        | 2    | RED  LED          | LED_SMD:LED_0805_2012Metric                                | Light emitting diode                                    |
| D3,                            | 1    | GEEN LED          | LED_SMD:LED_0805_2012Metric                                | Light emitting diode                                    |
| D4,                            | 1    | BLUE LED          | LED_SMD:LED_0805_2012Metric                                | Light emitting diode                                    |
| D5,                            | 1    | ORANGE LED        | LED_SMD:LED_0805_2012Metric                                | Light emitting diode                                    |
| J1, J2, J3, J4,                | 4    | Conn_01x08_Female | Connector_PinHeader_1.00mm:PinHeader_1x08_P1.00mm_Vertical | Generic 1x8 Connector                                   |
| J5,                            | 1    | USB_A             | Connector_USB:USB_A_Molex_67643_Horizontal                 | USB Type A connector                                    |
| R1,                            | 1    | 10k               | Resistor_SMD:R_0805_2012Metric                             | Resistor                                                |
| R2,                            | 1    | 470               | Resistor_SMD:R_0805_2012Metric                             | Resistor                                                |
| R3, R4, R5, R6,                | 4    | 100               | Resistor_SMD:R_0805_2012Metric                             | Resistor                                                |
| R7,                            | 1    | 220               | Resistor_SMD:R_0805_2012Metric                             | Resistor                                                |
| SW1, SW2, SW3, SW4, SW5, SW6,  | 6    | SW_MEC_5G         | Button_Switch_SMD:SW_MEC_5GSH9                             | MEC 5G single pole normally-open tactile switch         |
| U1,                            | 1    | ATmega16A-AU      | Package_QFP:TQFP-44_10x10mm_P0.8mm                         | 16MHz, 16kB Flash, 1kB SRAM, 512B EEPROM, JTAG, TQFP-44 |
| U2,                            | 1    | CH340G            | Package_SO:SOIC-16_3.9x9.9mm_P1.27mm                       | USB serial converter, UART, SOIC-16                     |
| Y1,                            | 1    | 20MHz             | Crystal:Crystal_SMD_HC49-SD_HandSoldering                  | Two pin crystal                                         |
| Y2,                            | 1    | 12MHz             | Crystal:Crystal_SMD_HC49-SD_HandSoldering                  | Two pin crystal                                         |

## Bibliography

https://create.arduino.cc/projecthub/bernieri/genius-game-simon-0e76dc

https://www.youtube.com/watch?v=xLLTxN_UBnI

http://ww1.microchip.com/downloads/en/devicedoc/atmel-8272-8-bit-avr-microcontroller-atmega164a_pa-324a_pa-644a_pa-1284_p_datasheet.pdf

https://cdn.sparkfun.com/datasheets/Dev/Arduino/Other/CH340DS1.PDF



