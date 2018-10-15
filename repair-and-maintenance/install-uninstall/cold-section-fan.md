# Cold Section Fan

On the Promega you will find two different fans. The nozzle fan, located on the bottom of the extruder assembly, and the cold-section fan, located in the front. 

## Fan Location

![Promega Fan Location](../../.gitbook/assets/hfsklgqrnj6zz2yw-fanlocation.jpg)

The cold-section fan, on the front of the extruder assembly, serves to cool the extruder assembly. This fan is very important to ensure that materials with lower printing temperatures, such as PLA, can comfortably pass through the extruder without losing its rigidity. If the cold-section fan is not functioning properly, heat could creep up from the hot-end, located right underneath, and cause filament to melt and jam the extruder. The cold-section fan is currently a 24V fan and is plugged into the "Always On" port on the Duet Maestro board. This is usually the best idea to ensure that the fan is always on while the hot-end is hot.

The nozzle fans are two 5V fans located underneath the extruder assembly, this fan allows for cooler air to reach the nozzle. This is important to allow printed filament to cool as quickly as possible and become rigid. Bridging without this fan would be very difficult. These fans are PWM controllable, by entering the G-code command `M106 Pn Sm` you can turn the fans on or off. `n` specifies the port number that the fan is plugged into. `m` represents the desired speed of the fan. This can be a value of 0 to 255, where 0 is off and 255 is the highest setting.

## Cold-Section Fan

Items you will need:

* T10 Torx Screwdriver
* Container
* Needlenose pliers
* Switch off power to the system. Wait for nearby components of the printer to cool before attempting to remove the fans.
* Remove the two screws holding the fan to the extruder assembly, one of these screws will be held in place with glue, you might have to use some force. When the fan is removed, place the nuts and bolts in a seperate container.

  ![PBezwNA9DMD3QPkF-RemoveFan.jpg](../../.gitbook/assets/pbezwna9dmd3qpkf-removefan.jpg)

* Move the fan over to the back of the extruder assembly, and observe where the cold-section fan is currently plugged in. The new fan will have to be plugged into the same location.

  ![5gYt9eINlI5zYdLd-coldsectionfanconnector.jpg](../../.gitbook/assets/5gyt9einli5zydld-coldsectionfanconnector.jpg)

* Use needlenose pliers to carefully remove the male fan connector from the female connector at the back of the cable assembly. You might have to unplug the heater cartridge connector in order to reach the fan connector.

  ![ut100yxgFKjiSFRq-needlenose.jpg](../../.gitbook/assets/ut100yxgfkjisfrq-needlenose.jpg)

* Connect the cable of the new fan. Plug the new fan into the same location that the old fan was plugged into. Before you continue with reassembling the printer, test if the fan works. Double check your wiring and turn on your Promega, the fan should start spinning immediately.
* Route the wire to the fan as shown in the image below. Remember to plug in the heater cartridge if you unplugged it.
* Insert the bolts with the M4 nut spacers to fasten the fan back to the extruder assembly. Pay attention to path of the fan wire. We recommend applying glue to one of the nozzle fan bolts to prevent it from loosening with vibration.

  ![9D7TfHnqggOJoZ2z-fanwiring.jpg](../../.gitbook/assets/9d7tfhnqggojoz2z-fanwiring.jpg)

