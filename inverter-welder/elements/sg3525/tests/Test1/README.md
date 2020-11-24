# Test 1: error amplifier configured as comparator
In this test pin 9 is left unconnected. Error amplifier is configured to work as a comparator.
Pins 1 and 2 are inputs which get compared with each other and a comparison voltage result (which can be meassured back on pin 9)
is fed to the PWM amplifier.

**Remark 1:** **do not** leave pins 1 or 2 unconnected as it leads to unpredictable output PWM to be generated! \
**Remark 2:** in this configuration only two PWM duty cycles are generated: either 0% or 50%.

<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/Test1/01_simple_comparator_test_circuit.png" width="35%" >

 | pin 1 [V] | pin 2[V] | pin 9[V] | PWM [%] | Oscillogram | Remark |
 |---|---|---|---|---|---|
 | 0.0 | 0.0 | 0.0 |  0 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/Test1/01_00_percent.jpg" width="40%" > | |
 | 0.0 | 5.1 | 5.7 | 50 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/Test1/01_50_percent.jpg" width="40%" > | PWM frequency can be read as ~47.6 kHz|
 | 5.1 | 5.1 | 0.3 |  0 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/Test1/01_00_percent.jpg" width="40%" > | |
 | 5.1 | 0.0 | 0.0 |  0 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/Test1/01_00_percent.jpg" width="40%" > | |
