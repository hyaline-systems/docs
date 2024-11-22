---
title: "Simple Robot Brain"
weight: 1
draft: false
# bookFlatSection: false
bookToc: true
bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

# About Simple Robot Brain

*The Hyaline Simple Robot Brain* is a "hat" for Raspberry Pi Pico compatible boards, designed for controlling motors. 

Designed by Mads Kjeldgaard.

![robotbrain1.png](../../images/robotbrain1.png) 
![robotbrain2.png](../../images/robotbrain2.png) 

## Features

- Control 4 DC motors using PWM
- Supports motors with encoders / hall sensors for position and speed controls – pins are broken out and easily accessible
- Hardware MIDI in/out (you can add USB MIDI in software as well) via UART
- Extend board using I2C: i2c0 broken out as both 2.54mm pins and [StemmaQT](https://learn.adafruit.com/search?q=stemmaqt) connector
- 5v - 10.8v power supply for motors.
- Programmable sleep mode: Put motors to sleep via software.
- Regulated 5V output, unused GPIO pins accessible too
- Small (59.07 mm x 76.33 mm)
- 4 x M3 mounting holes
- Pico board can either be mounted thru hole or SMD for a super low profile

## Datasheets

The board uses the DRV8833 motor driver. [See datasheet here.](https://www.ti.com/lit/ds/symlink/drv8833.pdf)

## Pin connections

### MIDI
| Function | GPIO Pin |
|----------|-----------|
| MIDI tx  | gpio8     |
| MIDI rx  | gpio9     |

### StemmaQT / I2C
| Function | GPIO Pin |
|----------|-----------|
| i2c0 sda | gpio4     |
| i2c0 scl | gpio5     |

### Motor drivers

Each motor output section has two sorts of output pins:

One set for just a screw terminal, allowing to screw in the two wires to a motor, as well as a header for connecting a motor with an encoder / hall sensor. The latter is broken out as 2.54mm pins behind the screw terminals including the ground and VCC pins for the encoder part of it. Only use one of them at a time per motor. 


| Motor driver   | Function | GPIO Pin |
|----------|----------|-----------|
| 1   | A1       | 2     |
| 1   | A2       | 3     |
| 1   | SLEEP    | 6     |
| 1   | B1       | 18    |
| 1   | B2       | 19    |
| 1   | FAULT    | 17    |
| 1   | Encoder A| 0     |
| 1   | Encoder B| 10    |
| 2   | A1       | 14    |
| 2   | A2       | 15    |
| 2   | SLEEP    | 7     |
| 2   | B1       | 20    |
| 2   | B2       | 21    |
| 2   | FAULT    | 16    |
| 2   | Encoder A| 12    |
| 2   | Encoder B| 22    |

## Power

The motor drivers support 5v to 10.8v DC power inputs through the large power inlet on the board.

This power is automatically converted to 5V and fed to the Pico board as a power source if you have not connected a USB cable, making it much simpler to wire.

## MIDI connections

The MIDI ins and outs are broken out as 2.54mm pins. These can then be connected to DIN-5 connectors for classic full-size MIDI cables or TRS-A / TRS-B connectors for the minijack sized ones.

### DIN-5 MIDI

#### In

- MIDI_IN_SLEEVE to pin 2 on din connector
- MIDI_IN_SOURCE to pin 4
- MIDI_IN_SINK to pin 5
- Pins 1 and 3 are unconnected.

#### Out

- Connect MIDI_OUT_SINK to pin 5 on the din connector
- connect MIDI_OUT_SOURCE to pin 4 on the din connector
- connect MIDI_OUT_SHIELD to pin 2
- Pins 1 and 3 on the DIN connector are unconnected.

### TRS-A

TODO

### TRS-B

TODO

# Building

## Bill of materials (BOM)


| Reference                                                                      | Value          | Datasheet                                                                                    | Footprint                                                      | Qty |
|--------------------------------------------------------------------------------|----------------|----------------------------------------------------------------------------------------------|----------------------------------------------------------------|-----|
| 5VOUTPINS1,gpio3v1,gpiognd1,motor1,motor2,motor3,motor4,Powerpins1,unusedgpio1 | Conn_01x02     | -- mixed values --                                                                           | -- mixed values --                                             | 9   |
| C1,C5,C7,C8                                                                    | 10uF/16v       | ~                                                                                            | Capacitor_SMD:CP_Elec_5x5.7                                    | 4   |
| C2,C3                                                                          | 0.01uF         | ~                                                                                            | Capacitor_SMD:C_0603_1608Metric                                | 2   |
| C4,C6                                                                          | 10uf           | ~                                                                                            | Capacitor_SMD:CP_Elec_5x5.7                                    | 2   |
| D2                                                                             | B5819W         | ~                                                                                            | Diode_SMD:D_SOD-323_HandSoldering                              | 1   |
| D3                                                                             | 1N4148         | [Datasheet](https://datasheet.octopart.com/1N4148TR-ON-Semiconductor-datasheet-42765246.pdf) | Diode_SMD:D_SOD-323_HandSoldering                              | 1   |
| H1,H2,H3,H4                                                                    | MountingHole   | ~                                                                                            | MountingHole:MountingHole_3.2mm_M3                             | 4   |
| J1                                                                             | Conn_01x04_Pin | ~                                                                                            | Connector_PinSocket_2.54mm:PinSocket_1x04_P2.54mm_Vertical     | 1   |
| MIDI_IN1,MIDI_OUT1                                                             | Conn_01x03     | ~                                                                                            | Connector_PinHeader_2.54mm:PinHeader_1x03_P2.54mm_Vertical     | 2   |
| motor1_enc1,motor2_enc1,motor3_enc1,motor4_enc1                                | Conn_01x06     |                                                                                              | Connector_PinSocket_2.54mm:PinSocket_1x06_P2.54mm_Vertical     | 4   |
| OC1                                                                            | H11L1M         | [Datasheet](https://www.tme.eu/Document/3f201601fbfb640f9cf7e492372dade8/H11L1.pdf)          | PCM_Package_DIP_AKL:DIP-6_W7.62mm_LongPads                     | 1   |
| POWERLED1                                                                      | LED            | ~                                                                                            | LED_SMD:LED_0603_1608Metric                                    | 1   |
| POWERLEDRESISTOR1                                                              | 1k             | ~                                                                                            | Resistor_SMD:R_0603_1608Metric_Pad0.98x0.95mm_HandSolder       | 1   |
| Q1                                                                             | DMP2045U       | [Datasheet](https://www.tme.eu/Document/4c3956670db2c68cea161ad240ee1e39/DMP2045U.pdf)       | PCM_4ms_Package_SOT:SOT-23                                     | 1   |
| Q2                                                                             | DMG2305UX      | [Datasheet](https://www.tme.eu/Document/79cbea1ac95301c813f57d9a7787c43d/DMG2305UX.pdf)      | PCM_Package_TO_SOT_SMD_AKL:SOT-23                              | 1   |
| R3                                                                             | 220            | ~                                                                                            | Resistor_SMD:R_0603_1608Metric_Pad0.98x0.95mm_HandSolder       | 1   |
| R4                                                                             | 10             | ~                                                                                            | Resistor_SMD:R_0603_1608Metric_Pad0.98x0.95mm_HandSolder       | 1   |
| R5                                                                             | 33             | ~                                                                                            | Resistor_SMD:R_0603_1608Metric_Pad0.98x0.95mm_HandSolder       | 1   |
| R6                                                                             | 470            | ~                                                                                            | Resistor_SMD:R_0603_1608Metric_Pad0.98x0.95mm_HandSolder       | 1   |
| R7,R8                                                                          | 10k            | ~                                                                                            | Resistor_SMD:R_0603_1608Metric_Pad0.98x0.95mm_HandSolder       | 2   |
| RSENSEA1,RSENSEA2,RSENSEB1,RSENSEB2                                            | 0.2            | ~                                                                                            | Resistor_SMD:R_0805_2012Metric_Pad1.20x1.40mm_HandSolder       | 4   |
| STEMMA_QT_I2C1                                                                 | JST_SH_SM04    | ~                                                                                            | Connector_JST:JST_SH_SM04B-SRSS-TB_1x04-1MP_P1.00mm_Horizontal | 1   |
| U1                                                                             | TLV1117-50     | [Datasheet](http://www.ti.com/lit/ds/symlink/tlv1117.pdf)                                    | Package_TO_SOT_SMD:SOT-223                                     | 1   |
| U3,U4                                                                          | DRV8833PW      | [Datasheet](http://www.ti.com/lit/ds/symlink/drv8833.pdf)                                    | Package_SO:TSSOP-16_4.4x5mm_P0.65mm                            | 2   |
| U7                                                                             | Pico           |                                                                                              | MCU_RaspberryPi_and_Boards:RPi_Pico_SMD_TH                     | 1   |
