# Test 4: check how output coil idle voltage changes with SG3525A pin 8 (Soft-Start) when no load attached to the welder

Date of test: 18th November 2020 \
 \
Attach a 100k variable resistor between ground and Soft-Start (pin 8) pin of SG3525A. \
Attach one scope to pin 11 of SG3515A. \
Attach second scope directly to one of the output coils of the output trafo. \
Attach multimeter to the output clamps. \
Magnum Power VIP 4000 is not loaded: no balast is attached to the output clamps.

Change the variable resistor to set a different voltage on pin 8 and observe the signals.

Additional remarks to oscillograms:
 * signal at the top half of the view (looks like a shark's finn) is from pin 11 of SG2325
   * time per div is 5us
   * voltage per div is always 5V
   * max voltage value is around 15V
 * signal at the whole part of the view is from output coil
   * time per div is 5us
   * voltage per div is 15V
   * min voltage value is around -65V
   * max voltage value is around  65V

 | pin 8 [V] | PWM [%] | Output clamps voltage [V]| Oscillogram: pin 11 vs output coil voltage | Remark |
 |---|---|---|---|---|
 | 3.66 | 43 | 62.5 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/concepts/08_magnum_power_vip_4000/reveng/tests/Test4/output_coil_voltage_pwm_43.jpg" width="40%" > | |
 | 2.53 | 30 | 61.0 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/concepts/08_magnum_power_vip_4000/reveng/tests/Test4/output_coil_voltage_pwm_30.jpg" width="40%" > | |
 | 1.98 | 21 | 60.5 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/concepts/08_magnum_power_vip_4000/reveng/tests/Test4/output_coil_voltage_pwm_21.jpg" width="40%" > | Output voltage doesn't drop even if PWM is around 20%. |
 | 1.51 | 11 | 60.2 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/concepts/08_magnum_power_vip_4000/reveng/tests/Test4/output_coil_voltage_pwm_11.jpg" width="40%" > | Output voltage still doesn't drop. |
 | 1.25 | 07 | 40.0 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/concepts/08_magnum_power_vip_4000/reveng/tests/Test4/output_coil_voltage_pwm_07.jpg" width="40%" > | Output clamp voltage drops to around 40V. Multimeter shows unstabe results. Oscillogram shows unstability (probably the voltage toggles) |
 | 1.20 | 05 | 10.0 | <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/concepts/08_magnum_power_vip_4000/reveng/tests/Test4/output_coil_voltage_pwm_05.jpg" width="40%" > | Here the output clamp voltage drops to around 10V. |

The output voltage doesn't react much on the PWM signal generated by SG3525. The wide of signal ramains mostly the same.
What is true: when PWM goes down to around 5% then the output idle voltage also goes drastically down. I tought that will react smoothly on PWM.

