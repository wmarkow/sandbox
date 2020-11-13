# Hardware tests of SG3525A (KA3525A) module

This document contains a set of hardware tests results of SG3525 module.
They can help to understand how the module works and what are the possibilities of controllig the generated PWM.

## SG3525 pinout
<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/sg3525_pinout_onsemi.png" width="30%" >


## SG3525 internal diagram
<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/sg3525_block_diagram_onsemi.png" width="50%" >

## Basic test circuit
In the tests a KA3525A chip has been used. Power supply about 12.3V and oscillator frequency about 93kHz.
This will produce PWM signal on single Output A and B with frequency of 46.5 kHz. The basic test circuit is as below:

<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/00_basic_test_circuit.png" width="50%" >
<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/00_basic_test_circuit.jpg" width="30%" >

## General about tests
For all tests keep in mind:
 * a test circuit is always presented
 * test circuit relates only to the following pins: 1, 2, 8, 9, 11 and 14
 * other pins remain unchanged as presented in the previous section **Basic test curcuit**
 * pins 11 (Output A) and 14 (Output B) are always output pins
 * pins 1, 3, 8 and 9 are either inputs or outputs - depend on test description
 * for pins 11 and 14 an oscillogram image may be presented:
   * time per div is always 5us
   * voltage per div is always 5V
   * the signal on top comes from pin 11 (Output A)
   * the signal on bottom comes from pin 14 (Output B)

## Test 1: error amplifier configured as comparator
In this test pin 9 is left unconnected. Error amplifier is configured to work as a comparator.
Pins 1 and 2 are inputs which get compared with each other and a comparison voltage result (which can be meassured back on pin 9)
is fed to the PWM amplifier.

**Remark 1:** **do not** leave pins 1 or 2 unconnected as it leads to unpredictable output PWM to be generated! \
**Remark 2:** in this configuration only two PWM duty cycles are generated: either 0% or 50%.

<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/01_simple_comparator_test_circuit.png" width="35%" >

 | pin 1 [V] | pin 2[V] | pin 9[V] | PWM [%] | Oscillogram | Remark |
 |---|---|---|---|---|---|
 | 0.0 | 0.0 | 0.0 |  0 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/01_00_percent.jpg" width="40%" > | |
 | 0.0 | 5.1 | 5.7 | 50 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/01_50_percent.jpg" width="40%" > | PWM frequency can be read as ~47.6 kHz|
 | 5.1 | 5.1 | 0.3 |  0 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/01_00_percent.jpg" width="40%" > | |
 | 5.1 | 0.0 | 0.0 |  0 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/01_00_percent.jpg" width="40%" > | |


## Test 2: error amplifier configured as a voltage follower

<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/02_voltage_follower_test_circuit.png" width="40%" >

 | pin 2 [V] | pin 9[V] | PWM [%] | Oscillogram | Remark |
 |---|---|---|---|---|
 | 0.00 | 0.02 |  0 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/02_00_percent.jpg" width="40%" > | |
 | 0.85 | 0.85 |  5 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/02_05_percent.jpg" width="40%" > | The smallest value which showed stable non zero PWM signal on my oscilloscope |
 | 1.01 | 1.01 |  7 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/02_07_percent.jpg" width="40%" > | |
 | 1.50 | 1.50 | 15 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/02_15_percent.jpg" width="40%" > | |
 | 2.00 | 2.00 | 24 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/02_24_percent.jpg" width="40%" > | |
 | 2.50 | 2.51 | 33 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/02_33_percent.jpg" width="40%" > | |
 | 3.01 | 3.01 | 43 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/02_43_percent.jpg" width="40%" > | |
 | 3.22 | 3.22 | 50 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/02_50_percent.jpg" width="40%" > | Minimum voltage that gives 50% PWM |
 | 5.04 | 5.04 | 50 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/02_50_percent.jpg" width="40%" > | |
 
## Test 3: shutdown by pull down compensation pin
In this test error amplifier is configured as comparator to generate 50% PWM on both outputs A and B.
Compensation pin is used to be pulled down to ground to shutdown the output PWM signal.

<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/03_magnum_power_vip_4000_test_circuit.png" width="40%" >

 | pin 9[V] | PWM [%] | Oscillogram |
 |---|---|---|---|---|
 | 5.1 | 50 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/03_50_percent.jpg" width="40%" > |
 | 0.0 |  0 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/03_00_percent.jpg" width="40%" > |
 
## Test 4: limit PWM duty cycle with Soft-Start pin.
In this test by attaching a variable resitor to the Soft-Start pin we limit the duty cycle of generated PWM signal no matter what voltage is 
applied to pin 9 or what is generated by error amplifier. Soft-Start mechanism is left intact. It is adviced to use max 100k potentiometer. Together
with chip's internal 50uA current source, it will generate max 5V on pin 8, which is good enough to limit the duty cycle between 0% and 50%.

<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/04_limit_pwm_with_pin8.png" width="40%" >
