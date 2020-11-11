# Hardware tests of SG3525 module

This document contains a set of hardware tests results of SG3525 module.
They can help to understand how the module works and what are the possibilities of controllig the generated PWM.

## SG3525 pinout
<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/sg3525_pinout_onsemi.png" width="30%" >


## SG3525 internal diagram
<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/sg3525_block_diagram_onsemi.png" width="50%" >

## Basic test circuit
<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/00_basic_test_circuit.png" width="50%" >
<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/00_basic_test_circuit.jpg" width="30%" >


## Test 1: error amplifier configured as comparator
In this test pin 9 is left unconnected. Error amplifier is configured to work as a comparator.
Pins 1 and 2 are inputs which get compared with each other and a comparison voltage result is fed to the PWM amplifier. This voltage can be
meassured back on pin 9. \
**Remark 1:** **do not** leave pins 1 or 2 unconnected as it leads to unpredictable output PWM to be generated! \
**Remark2:** in this configuration only two PWM duty cycles are generated: either 0% or 50%.

<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/01_simple_comparator_test_circuit.png" width="35%" >

 | pin 1 [V] | pin 2[V] | pin 9[V] | PWM [%] | Oscillogram |
 |---|---|---|---|---|
 | 0.0 | 0.0 | 0.0 |  0 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/01_0_percent.jpg" width="40%" > |
 | 0.0 | 5.1 | 5.7 | 50 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/01_50_percent.jpg" width="40%" > |
 | 5.1 | 5.1 | 0.3 |  0 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/01_0_percent.jpg" width="40%" > |
 | 5.1 | 0.0 | 0.0 |  0 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/01_0_percent.jpg" width="40%" > |


## Test error amplifier to act as a voltage follower

<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/02_voltage_follower_test_circuit.png" width="40%" >

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

<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/03_magnum_power_vip_4000_test_circuit.png" width="40%" >

 | pin 1 [V] | pin 2[V] | pin 9[V] | PWM image|
 |---|---|---|---|
 | 0 | 5 | 5 | ? |
 | 0 | 5 | 0 | ? |
 
## Test controll PWM with Soft-Start pin

<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/04_limit_pwm_with_pin8.png" width="40%" >
