# Critical Warnings & Information

The M3D Promega is an industrial product. The user assumes all responsibility for proper operation and acknowledges that they understand the operation and standard practices of additive manufacturing. The user assumes all responsibility for its proper use and agrees to follow the directives below to ensure a safe and working unit before any other operation.

## Warnings

1. CHECK POWER SUPPLY'S OPERATING INPUT VOLTAGE. Failure to do so will damage the power supply. There are two input wall voltages: 115V or 230V. Choose the appropriate settings. 
2. DO NOT TOUCH PRINTER WHILE OPERATING The Promega is a powerful industrial machine. While the Promega is moving or printing you should not reach into the buildspace.
3. DO NOT MOVE THE BED WITHOUT POWER

   The belts on the printer bed can skip, causing a 2mm shift in your bed level, which will need to be fixed. There is a small but real chance it may damage the Duet board. Do not place heavy items or lean on the bed as it can also skip it.

4. MOVE MOTORS SLOWLY

   Moving motors generates power on all printers and can damage your board. A good indicator of the power you are generating is the cold section fan on the front. If you can hear the fan moving air, you're close to voltages that will break the duet regulator \(more than 28V\). As long as you can see the fan is not gaining speed you are fine. Move components at about 30 mm/s. It is best to always move components while the system is powered.

5. DISABLING MOTORS

   When you disable motors the bed will drop to the limit switch. Giving you print access.

6. ESD SAFETY:

   The Duet contains an ARM class 2 processor, we recommend you use a wrist straps when touching any wires that could send shocks to the main processor and fry it.

7. DON'T USE AN ESD WRIST STRAPS TIED TO A SURGE STRIP

   The printer is grounded. If you wire the strap wrong it can cause a short circuit through your body whenever you touch the printer.

8. USE UNDER SUPERVISION

   Place the printer in a place where nothing can catch on fire should the worst occur. The promega is constructed out of metal and fireproof materials. Still, PLA and other filaments can burn and cause a fire if the printer is used improperly.

9. MAXIMUM EXTRUDER SPEED

   Don't extrude faster than 5.6 mm^3/s with any filament in compound extruder to start. Get success first with no skipping then try to push the limits. Do the math: 45mm/s movement, 0.3 mm layers and 0.5 mm wide would be 6.75mm^3/s , a bit to fast for your first print, especially with pla. So adjust layer heights accordingly, for example to 0.25mm high for your first prints. Over time you should be able to print faster. Remember that speed depends on material, number of print moves per second, nozzle type and temperature.

10. Z SPEED

    The bed current, acceleration and speed are configured for heavy prints. You can increase speed when printing lighter items. Currently, the acceleration of the z-axis is set to 75 mm / s ^2 and a max linear speed of 2300 mm/s but that can be improved depending on your application of the printer.

11. REMOVE TOP COVER

    Whenever printing PLA you must remove the top cover or it will overheat.

12. BED TEMPERATURE

    If you are using a glass print bed, give the printer an extra few minutes to reach temperature. Without the side and front covers, the glass will be 5-10 C cooler than the bed temperature readouts from the thermistor.

13. FRAME CAN BE SHARP

    The frame of the printer is metal and could be sharp. Use caution when moving the printer or moving around the printer. Keep your hands out of the machine during operation and be careful when lifting.

14. BURN HAZARD

    BED and NOZZLES may cause burns when hot.

15. USE CAUTION WHEN REMOVING PRINTS

    Use caution when scraping prints off the bed. Push the bed down against a foam pad \(relieving pressure on the z belts\) or remove the glass with the print attached in order to remove it on a firm surface. Best strategy is let the bed cool, most prints pop off by themselves.

16. WATCH THE FAN

    The cold section fan is spinning very fast when the system is on. Please keep tools and yourself clear of it when it is operational.

17. MANUALLY DEPLOY Z-PROBE

    This printer features both an IR probe and a manually deployable limit switch probe. Be sure to put the limit switch magnet on the mount before probing with the limit switch. Failure to do so could crash the bed into the nozzle. Change the config.g file commands in order to change which probe is being used.

18. CRASHING THE BED

    Crashing the bed into the nozzle can result in the bed skipping and falling down **fast** due to gravity. Stay clear of the printer and do not enter the buildspace while the promega is printing.

## About the Z-assembly

1. The bed is designed to skip if the bed crashes into the nozzle. Once the Z-motor skips it will let the bed fall down to its resting position. The speed of this fall can be very fast, but it's better than a cracked glass bed.
2. A normal bed must meet the following condition: Pushing down gently on the bed \(less than 10lb\) on any spot on the bed should make the bed move. The same must be true for pushing upwards from the center of the bed, or lifting the bed with two hands in the middle of two opposing faces. All beds will skip if you attempt to lift them from one corner, this is normal.
3. The bed can skip if moved improperly, which is normal. It is safe to adjust the bed by skipping the belt in corners. Follow the [Repair & Maintenance](../repair-and-maintenance/) guides for more information on tensioning and leveling your bed. 
4. Currently the only way to mechanically level the bed is to skip belts in corners of the bed. This leaves you with an accuracy of +-1mm per corner. Future designs will come with an improved mechanical leveling system. A normal bed will one or two corners off 1 or 1.5mm from the rest with an RMS flatness of 0.2 - 0.35mm. This is still relatively small across the Promega's big buildspace.
5. New belt tops and bottoms were designed as of 06/04/18. Use [this link](https://drive.google.com/drive/folders/1cmnAcQU7NjgBqAub60Pz7tJyY-e5qH1w) to the public google drive to download the _.STL_ files in order to print them. They can also be shipped to you.
6. Sliders and the bed frame are tightened based on experience to achieve the best possible backlash, smoothness, ideal kinetic friction across the entire range. The system is designed to be tighter towards the bottom to brake the bed if it comes down. Smoothness of the Z-axis is tied closely with belt tension and trueness of the frame.
7. The Z-sliders each have two screws attaching them to the bed platform. Only one of these screws is meant to be completely tightened. This allows the sliders to maintain the proper amount of friction on the sliders to perform fast moves such as a Z-hop.
8. In order to test your bed, move the z-motor by hand and observe the movement of the 4 sliders, none should stick. 
9. Tension your Z-belts approperiately so that the belts can not skip easily. You should be able to strum the belts.

Continue on to the [Unboxing & Assembly](unboxing-and-assembly.md), the next chapter in the [Getting Started](./) guide.

