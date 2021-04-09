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

## [Test 1: error amplifier configured as comparator](https://github.com/wmarkow/sandbox/tree/master/inverter-welder/elements/sg3525/tests/Test1/README.md)

## [Test 2: error amplifier configured as a voltage follower](https://github.com/wmarkow/sandbox/tree/master/inverter-welder/elements/sg3525/tests/Test2/README.md)

## [Test 3: shutdown by pull down compensation pin](https://github.com/wmarkow/sandbox/tree/master/inverter-welder/elements/sg3525/tests/Test3/README.md)

## [Test 4: limit PWM duty cycle with Soft-Start pin](https://github.com/wmarkow/sandbox/tree/master/inverter-welder/elements/sg3525/tests/Test4/README.md)

## [Test 5: pull down compensation pin with external PWM signal](https://github.com/wmarkow/sandbox/tree/master/inverter-welder/elements/sg3525/tests/Test5/README.md)

## [Test 6: limit PWM duty cycle with Compensation pin](https://github.com/wmarkow/sandbox/tree/master/inverter-welder/elements/sg3525/tests/Test6/README.md)
