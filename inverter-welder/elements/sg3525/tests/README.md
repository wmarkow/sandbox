# Hardware tests of SG3525 module

This document contains a set of hardware tests results of SG3525 module.
They can help to understand how the module works and what are the possibilities of controllig the generated PWM.

## SG3525 pinout
![SG3525 pinout](https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/sg3525_pinout_onsemi.png)

## SG3525 internal diagram
![SG3525 diagram](https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/sg3525_block_diagram_onsemi.png)

## Basic test circuit
![SG3525 diagram](https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/00_basic_test_circuit.png)



## Test error amplifier to act as a simple comparator
In this configuration pin 9 is left unconnected. Error amplifier is configured to work as a volatge comparator.
Pins 1 and 2 are fed with various voltages. Amplifier compares them and gives a controll voltage to PWM amplifier; this voltage can be
meassured back on pin 9.

 | pin 1 [V] | pin 2[V] | pin 9[V] | PWM image|
 |---|---|---|---|
 | 0 | 0 | ? | ? |
 | 0 | 5 | ? | ? |
 | 5 | 5 | ? | ? |
 | 5 | 0 | ? | ? |


## Test error amplifier to act as a voltage follower
