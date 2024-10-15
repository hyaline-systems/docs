---
title: "Simple Robot Brain"
weight: 1
# bookFlatSection: false
bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

# Hyaline Simple Robot Brain

*The Hyaline Simple Robot Brain* is a "hat" for Raspberry Pi Pico compatible boards, designed for controlling motors. 

Designed by Mads Kjeldgaard.

![robotbrain1.png](robotbrain1.png) 
![robotbrain2.png](robotbrain2.png) 

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


| Motor    | Function | GPIO Pin |
|----------|----------|-----------|
| Motor1   | A1       | gpio2     |
| Motor1   | A2       | gpio3     |
| Motor1   | SLEEP    | gpio6     |
| Motor1   | B1       | gpio18    |
| Motor1   | B2       | gpio19    |
| Motor1   | FAULT    | gpio17    |
| Motor1   | Encoder A| gpio0     |
| Motor1   | Encoder B| gpio10    |
| Motor2   | A1       | gpio14    |
| Motor2   | A2       | gpio15    |
| Motor2   | SLEEP    | gpio7     |
| Motor2   | B1       | gpio20    |
| Motor2   | B2       | gpio21    |
| Motor2   | FAULT    | gpio16    |
| Motor2   | Encoder A| gpio12    |
| Motor2   | Encoder B| gpio22    |

## Power

The motor drivers support 5v to 10.8v DC power inputs through the large power inlet on the board.

This power is automatically converted to 5V and fed to the Pico board as a power source if you have not connected a USB cable, making it much simpler to wire.
