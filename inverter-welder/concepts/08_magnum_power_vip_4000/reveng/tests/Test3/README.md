# Test 3: check how voltages of pin 11 of SG3525A and pin 5 of VT1 chip changes with SG3525A pin 8 (Soft-Start)

Attach a 100k variable resistor between ground and Soft-Start (pin 8) pin of SG3525A. \
Attach one scope to pin 11 of SG3515A. \
Attach second scope to pin 5 of VT1 chip. \
Magnum Power VIP 4000 is not loaded: no balast is attached to the output clamps.

Change the variable resistor to set a different voltage on pin 8 and observe the signals.

VT1 chip is powered up with 15.8V

Additional remarks to oscillograms:
 * signal at the top is from pin 11 of SG2325
   * time per div is always 5us
   * voltage per div is always 5V
   * max voltage value is around 15V
 * signal at the bottom is from pin 5 of VT1 element
   * time per div is always 5us
   * voltage per div is always 5V
   * max voltage value is around 15V

 | pin 8 [V] | PWM [%] | Oscillogram |
 |---|---|---|
 | 4.00 | 50 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/concepts/08_magnum_power_vip_4000/reveng/tests/Test3/vt1_pin5_for_pwm_50_percent.jpg" width="40%" > | |
 | 2.00 | 20 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/concepts/08_magnum_power_vip_4000/reveng/tests/Test3/vt1_pin5_for_pwm_20_percent.jpg" width="40%" > | |
 
The voltage on the pin 5 of VT1 chip follows the changes of SG3515A pin 11. This is good.