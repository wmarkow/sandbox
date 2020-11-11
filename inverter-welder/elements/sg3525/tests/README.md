# Hardware tests of SG3525 module

This document contains a set of hardware tests results of SG3525 module.
They can help to understand how the module works and what are the possibilities of controllig the generated PWM.

## SG3525 pinout
<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/sg3525_pinout_onsemi.png" width="50%" >


## SG3525 internal diagram
<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/sg3525_block_diagram_onsemi.png" width="80%" >

## Basic test circuit
![SG3525 diagram](https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/00_basic_test_circuit.png)
<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/00_basic_test_circuit.jpg" width="50%" >


## Test error amplifier to act as a simple comparator
In this configuration pin 9 is left unconnected. Error amplifier is configured to work as a volatge comparator.
Pins 1 and 2 are fed with various voltages. Amplifier compares them and gives a controll voltage to PWM amplifier; this voltage can be
meassured back on pin 9.

![SG3525 diagram](https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/01_simple_comparator_test_circuit.png)

 | pin 1 [V] | pin 2[V] | pin 9[V] | PWM [%] | Oscillogram |
 |---|---|---|---|---|
 | 0 | 0 | ? | ? | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/sg3525_pinout_onsemi.png" width="40%" > |
 | 0 | 5 | ? | ? | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/sg3525_pinout_onsemi.png" width="40%" > |
 | 5 | 5 | ? | ? | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/sg3525_pinout_onsemi.png" width="40%" > |
 | 5 | 0 | ? | ? | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/sg3525_pinout_onsemi.png" width="40%" > |


## Test error amplifier to act as a voltage follower

![SG3525 diagram](https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/02_voltage_follower_test_circuit.png)

 | pin 2 [V] | pin 9[V] | PWM [%] | Oscillogram |
 |---|---|---|--|
 | 0.0 | ? | ? | ? |
 | 0.6 | ? | ? | ? |
 | 0.9 | ? | ? | ? |
 | 1.0 | ? | ? | ? |
 | 1.1 | ? | ? | ? |
 | 2.0 | ? | ? | ? |
 | 2.5 | ? | ? | ? |
 | 3.0 | ? | ? | ? |
 | 3.3 | ? | ? | ? |
 | 3.6 | ? | ? | ? |
 | 4.0 | ? | ? | ? |
 | 4.5 | ? | ? | ? |
 | 5.0 | ? | ? | ? |
 
## Test PWM with Compensation pin

![SG3525 diagram](https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/03_magnum_power_vip_4000_test_circuit.png)

 | pin 1 [V] | pin 2[V] | pin 9[V] | PWM image|
 |---|---|---|---|
 | 0 | 5 | 5 | ? |
 | 0 | 5 | 0 | ? |
 
## Test controll PWM with Soft-Start pin

![SG3525 diagram](https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/04_limit_pwm_with_pin8.png)
