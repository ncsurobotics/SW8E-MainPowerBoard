The 12V module is designed to supply 12V power at up to 8A of current. This module uses TI's LM5156H chip as a SEPIC controller. SEPIC topology is selected over a Flyback topology as it is better for higher currents. Additionally, SEPIC is used instead of a four FET buck-boost to reduce cost of the design and due to what chips are currently available for purchase.

SW8 is powered off 2 4 cell LiPo batteries resulting
- Min voltage (dead batteries) = 12.8V
- Nominal voltage = 14.8V
- Max voltage (full charge) = 14.8V

However, since thrusters are run off the batteries directly there is potential for sudden voltage drops due to rapid changes in load (thrusters). As such, it is not sufficient to simply use a buck regulator for 12V as the input could easily drop below 12V. From (limited) experimental data, we beleive the voltage could drop as low as 8V (likely no lower as other regulators in the system would shut off below this and have not in practice). Data on voltage drops will be collected later and added to this document.


Files:
- Quickstart spreadsheet is a SEPIC quickstart calculator for the LM5156 provided by TI.
- DatasheetDesign spreadsheet is a custom spreadsheet used to evaluate formulas in the datasheet as the design was being planned. Mostly used to make sure there are no oversights from using the quickstart sheet.
- PSpiceSimulation folder contains a PSpice project to simulate the 12V converter. This is used to verify max current through components and analyze the regulator's response to sudden changes in input voltage (this can occur as motors are run directly off the battery). PSpice for TI can be obtained for free from TI at https://www.ti.com/tool/PSPICE-FOR-TI

