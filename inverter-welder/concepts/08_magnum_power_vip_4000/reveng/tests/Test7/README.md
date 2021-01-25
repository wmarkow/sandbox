# Test 7: check how output idle voltage changes with SG3525A pin 8 (Soft-Start) when small load attached to the welder

Date of test: 2nd December 2020 \
 \
Attach a 100k variable resistor between ground and Soft-Start (pin 8) pin of SG3525A. \
Attach a scope to output of positive clamp. \
Magnum Power VIP 4000 is loaded: a 40W 230V bulb is attached to the output clamps.

Change the variable resistor to set a different voltage on pin 8 and observe the signals.


Additional remarks to oscillograms:
  * time per div is 5us
  * voltage per div is 15V
  * max voltage value is around 65V

 | pin 8 [V] | PWM [%] | Output idle voltage [V]| Oscillogram | Remark |
 |---|---|---|---|---|
 | 1.63 | 17 | 59.9 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/concepts/08_magnum_power_vip_4000/reveng/tests/Test1/output_voltage_for_pwm_50_percent.jpg" width="40%" > | For reference: no bulb attached in this case!|
 | 3.26 | 17 | 50.4 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/concepts/08_magnum_power_vip_4000/reveng/tests/Test1/output_voltage_for_pwm_50_percent.jpg" width="40%" > | Bulb attached. Average voltage is 50.4V. |

The output voltage changes when a bulb is attached to the output. I also did a small MIG test. I do not have a MIG set which will feed the wire automatically (which is bad).
I just put a 10cm long wire into the clamp (normally where the stick electrode is placed) and tried to weld. 
When the voltage on pin8 was set to 5V then the wire gets hot and burned immediatelly. With the smallest 20A setting was a bit better
but anyway ...


... ok I need to do this tests one more time, because I do not remember the details.

When the voltage on pin8 was set to 1.63V I had the feeling that the welding works better, like it behaves better at the initial phase
of welding, when the wire touches to the base material. Maybe it is just a feeling, but I hope that lowering the voltage on pin 8 improve
the situation. Also the wire didn't burn immediatelly. I need to borow the wire feeder, so I can test with a real MIG equipment.
 



