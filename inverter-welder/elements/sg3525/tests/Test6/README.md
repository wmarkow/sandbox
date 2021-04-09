# Test 6: limit PWM duty cycle with Compensation pin

In this test error amplifier is configured as comparator to generate 50% PWM on both outputs A and B.
Compensation pint is pulled up by 1k resistor and pulled down by a variable VR resistor. It will be tested how
variable resitor VR can influence the generated PWM signals.
Test circuit is as below:

<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/Test6/06_limit_pwm_with_pin9_circuit.png" width="50%" > 
<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/Test6/06_limit_pwm_with_pin9_circuit.jpg" width="60%" >

 | Potentiometer [kOhm] | pin 9[V] | PWM [%] | Oscillogram | Remark |
 |---|---|---|---|---|
 | 0.039 | 0.20 |  0 | | |
 | 0.059 | 0.30 |  0 | | |
 | 0.081 | 0.40 |  0 | | |
 | 0.106 | 0.50 |  0 | | |
 | 0.128 | 0.60 |  0 | | |
 | 0.181 | 0.80 |  0 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/Test6/06_00_percent.jpg" width="40%" > | |
 | 0.189 | 0.83 |  5 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/Test6/06_05_percent.jpg" width="40%" > | The smallest potentiometer value which showed stable non zero PWM signal on my oscilloscope |
 | 0.295 | 1.19 | 10 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/Test6/06_10_percent.jpg" width="40%" > | |
 | 0.607 | 1.97 | 24 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/Test6/06_24_percent.jpg" width="40%" > | |
 | 0.917 | 2.50 | 33 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/Test6/06_33_percent.jpg" width="40%" > | |
 | 1.612 | 3.21 | 50 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/Test6/06_48_percent.jpg" width="40%" > | Minimum potentiometer value that gives 50% PWM |
 | 2.090 | 3.51 | 50 | | |
 | 3.370 | 4.00 | 50 | | |
 | 6.710 | 4.50 | 50 | | |
 | 9.960 | 4.70 | 50 | | |
 