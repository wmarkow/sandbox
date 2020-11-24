# Test 3: shutdown by pull down compensation pin
In this test error amplifier is configured as comparator to generate 50% PWM on both outputs A and B.
Compensation pin is used to be pulled down to ground to shutdown the output PWM signal.

<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/Test3/03_magnum_power_vip_4000_test_circuit.png" width="40%" >

 | pin 9[V] | PWM [%] | Oscillogram |
 |---|---|---|
 | 5.1 | 50 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/Test3/03_50_percent.jpg" width="40%" > |
 | 0.0 |  0 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/elements/sg3525/tests/Test3/03_00_percent.jpg" width="40%" > |
 