# Serenity's Game 1

## Introduction

This is an implementation of a classic electronic memory Game built with the Microchip PIC16F690 MCU.
All work is performed by Serenity-Rose under the supervision of her father.


## Game

### UI

 * On / Off Power Switch
 * 4 x LED (Red, Yellow, Green, Blue)
 * 4 x Push Button Switches (Red, Yellow, Green, Blue)
 * Last Sequence Push Button
 * Start Push Button
 * Longest Sequence Push Button
 * Game Selection Sliding Switch (3 position)
  1 = Repeat
  2 = Player Adds
  3 = Elimination
 * Level Selection Sliding Switch (4 position)
  1 = 8 Sequence Length
  2 = 14 Sequence Length
  3 = 20 Sequence Length
  4 = 31 Sequence Length
 * PWM Controlled Sounder
 * Internal
  * Reset Button
  * ICSP Programming / Debug Header

### Games

#### Repeat (1)

Computer starts a colour sequence with a length of 1.
Player repeats the colour sequence.
Computer adds an additional colour to the sequence.
Player has to keep repeating the last shown sequence.
If a colour is not pressed within 5 seconds or an incorrect colour is pressed the game ends and the player loses.
If the maximum sequence is reached the player wins.


#### Player Adds (2)

The computer starts a colour sequence with a length of 1.
The player repeats the sequence and adds an additional colour to the sequence.
The computer repeats the new sequence.
Player repeats the last shown sequence and adds a new colour.
If a colour is not pressed within 5 seconds or an incorrect colour is pressed the game ends and the player loses.
If the maximum sequence is reached the player wins.


#### Elimination (3)

The computer starts a colour sequence with a length of 1.
The players repeat their own colours in sequence.
Computer adds an additional colour to the sequence.
The computer repeats the new sequence.
The players repeat their own colours in sequence.
If a player makes a mistake and doesn't press within 5 seconds or presses their colour at an incorrect time their colour is removes from the sequence.
Computer adds an additional colour still in the game to the sequence.
The computer repeats the new sequence.
The players repeat their own colours in sequence.
If a player makes a mistake and doesn't press within 5 seconds or presses their colour at an incorrect time their colour is removes from the sequence.
The winner is the last player left in the game or one colour left.
(TODO: Does the game end at reaching the maximum sequence length?)


#### Notes

 * A response must be provided within 5 seconds.
 * A low buzz indicates an error
 * Six short beeps of the last colour indicates a win.
 * After the 5th, 9th, and 13th sequence the sequence speeds up (only the showing of the sequence and not the response timeout).


## Microcontroller

### Summary

Microchip PIC16F690-I/P or -E/P Microcontroller.
 * 4096 Flash Words
 * 256 SRAM Bytes
 * 256 EEPROM Bytes
 * 18 I/O
 * 12 10-bit ADC
 * 2 Comparators
 * 2 8-bit Timers
 * 1 16-bit Timer
 * SSP
 * ECCP+
 * EUSART

Note that a smaller MCU may be a cheaper alternative e.g. PIC16F685. This MCU was chosen as I already had a tube. 


### Game Pin ALlocation

| Pin | Signal      | Allocation               |
| --- | ----------- | ------------------------ |
|   1 | Vdd         | Positive 4.5 - 5.0 Volts |
|   2 | RA5         | SW Skill 2               |
|   3 | RA4         | SW Skill 1               |
|   4 | -MCLR/VPP   | Reset and programming    |
|   5 | RC5         | LED 2 (YELLOW)           |
|   6 | RC4         | LED 1 (RED)              |
|   7 | RC3         | Sounder                  |
|   8 | RC6         | LED 3 (GREEN)            |
|   9 | RC7         | LED 4 (BLUE)             |
|  10 | RB7         | SW 4 (BLUE)              |
|  11 | RB6         | SW 3 (GREEN)             |
|  12 | RB5         | SW 2 (YELLOW)            |
|  13 | RB4         | SW 1  (RED)              |
|  14 | RC2         | SW Level 3               |
|  15 | RC1         | SW Level 2               |
|  16 | RC0         | SW Level 1               |
|  17 | RA2         | SW Start                 |
|  18 | RA1/ICSPCLK | SW Longest               |
|  19 | RA0/ICSPDAT | SW Last                  |
|  20 | Vss         | Ground                   |

Note that only the used signals are shown and other signals may be available on the pins.


## Licensing

Copyright (C) 2021 Justin Lane.
All rights reserved.

This repository, projects, and contents are Copyright (C) 2021 Justin Lane and are released under the Solderpad Hardware License 2.1.
This is a liberal open-source license derived from the Apache License Version 2.0.
Please see the [LICENSE](LICENSE) file for more details.


## Contact Us

Please email serenitygame1@jigglesoft.co.uk regarding this repository.

