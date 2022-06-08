Main power board is designed to regulate LiPo batteries down to 12V and 5V for various boards and devices on the robot

Approximated 5V load
- Jetson = 2.5A / 4A (depends on if in 5W or 10W power mode and what devices connected to USB)
- Cube orange has its own regulator directly from battery power. Also could be powered by jetson USB (included in above number)
- USB Hub = 2A (max, realistically more likely 1A)
- MEB = < 1A (probably much less)
- LED Strip = 60mA / LED * 20 LEDs = 1.2A  (Note: probably only 20mA not 60mA per so this is overestimate)
- Total = 8.2A

Design of power board
- One 5V@8.2+A regulator is quite difficult to design.
- Instead multiple 5V@4A regulators can be used (4A per module selected as it is sufficient for jetson in all cases)
- Additionally, the 5V regulator is easier to design if its input is relatively stable. LiPo voltage varies greatly due to thrusters. As such, the 5V modules will be run off the 12V module.

- Power board will consist of a 12V module to power the 5V modules. All boards / devices in the system will run off either 5V or 12V (or have a builtin regulator). Only 12V and 5V will be distributed to other components in the system. Many boards will have a builtin 3.3V regulator (eg MEB). By providing 5V power to MEB a linear regulator can be used to get 3.3V (easy since current is low). If current requirements from 3.3V made linear regulator non-idea, a buck regulator could still be used easily. Similarly, acousitcs boards need 10V. If provided with 12V a linear regulator can be used on-board to obtain clean 10V for the acoustics system. LEDs (neopixels) will either be 5V or 12V (both of which are available in the system)
- The 12V module will have connectors for up to three 5V modules. Additionally, various connectors will be available for 12V power directly.
- Assuming 85% regulator efficiency for 12V down to 5V (realasic for buck converters) expected load on 12V per 5V module is as follows
	- 5V * 4A = 20W output
	- 20W out / 0.85 = 23.53W input
	- 23.53W / 12V = 1.96A input
- As such, 12V regulator requires 6A capability just for 5V modules

Other 12V devices:
- LED Strip = 20mA / LED * 20 LED = 400mA (likely an overestimate, generally 300 pixel strips with WS2811 are specd as 6A max, likely 4A typical meaning 13mA per more likely)
- Acoustics power board sub 1A (likely less than 100mA)
- Total other approx 1.5A

- 12V board designed for 12V@8A (allows all three 5V modules at full load plus 2A extra off 12V)

