# Fans

## What are the Fans?

On the Promega you will find two different fans.

* The cold-section fan, on the front of the extruder assembly.
* The nozzle fans are two 5V fans currently located on the sides \(or under, in previous revisions\) of the extruder assembly.

#### Cold Section Fan

Serves to cool the extruder assembly. 

This fan is **very important** to ensure that materials with lower printing temperatures, such as PLA, can comfortably pass through the extruder without losing its rigidity. If the cold-section fan is not functioning properly, heat could creep up from the hot-end, located right underneath, and cause filament to melt and jam the extruder. 

The cold-section fan is currently a 24V fan and is plugged into the **"Always On"** port on the Duet Maestro board. This is usually the best idea to ensure that the fan is always on while the hot-end is hot.

#### Nozzle Fan

Allows for cooler air to reach the nozzle. This is important to allow printed filament to cool as quickly as possible and become rigid. Bridging without this fan would be very difficult. 

These fans are PWM controllable, by entering the G-code command:

```text
M106 Pn Sm
```

you can turn the fans on or off. 

`n` specifies the port number that the fan is plugged into. 

`m` represents the desired speed of the fan. 

* This can be a value of 0 to 255, where 0 is off and 255 is the highest setting.

## Version: Current

### General Fan Location

![Promega Fan Location](../../.gitbook/assets/img_1042.JPG)

### Warning

Do not attempt to start the guide with a hot extruder. Wait for the hot end\(s\) of the printer to cool before continuing with this guide.

### Tools

1. T10 Torx Screwdriver
2. T30 Torx Screwdriver
3. Needle-nose pliers

### Additional Hardware

_**NONE**_

### How To Uninstall Fan Mount

Turn off board.

Move the bed all the way down. Let it rest on the limit switch. 

{% hint style="warning" %}
Do not place a significant amount of weight on the bed. It could skip your bed.
{% endhint %}

Disconnect the heater and PT1000 \(extruder side\).

![](../../.gitbook/assets/heater-and-pt1000-wires.jpg)

Disconnect the nozzle fan and cold section fan cables \(extruder side\).

![The nozzle fan connector](../../.gitbook/assets/img_1369.JPG)

Unscrew the Wall-E. 

![](../../.gitbook/assets/walle-screws.jpg)

Remove the Wall-E from the chassis. 

{% hint style="info" %}
Parts inside the Wall-E may fall out. Be careful not to lose them.
{% endhint %}

![](../../.gitbook/assets/remove-walle.jpg)

Slide the Cold Section down.

![](../../.gitbook/assets/slide-down.jpg)

Unscrew the M3 screws.

![](../../.gitbook/assets/m3-fan-screw.jpg)

Remove the nozzle fans from the fan mount

![](../../.gitbook/assets/remove-nozzle-fans.jpg)

Slide the Cold Section Fan out of the fan mount. 

![](../../.gitbook/assets/remove-cold-section.jpg)

### 

### How To Install Fan Mount

Disconnect the heater and PT1000 \(extruder side\).

![](../../.gitbook/assets/heater-and-pt1000-wires.jpg)

Unscrew the Wall-E. 

Remove the Wall-E from the chassis. 

{% hint style="info" %}
Parts inside the Wall-E may fall out. Be careful not to lose them.
{% endhint %}



Line up the Wall-E onto the Fan Mount.

Screw in both M3 screws onto the Fan Mount. 

{% hint style="info" %}
Aligning the Wall-E to the Fan Mount may be a bit tricky, as it may slip. 
{% endhint %}

![](../../.gitbook/assets/m3-fan-screw%20%281%29.jpg)

Check for any gaps.

![](../../.gitbook/assets/nozzle-fan-gaps.jpg)

If you have gaps, slowly unscrew and clamp \(with your hands\). The gap should start close.

Once its closed, tighten the screws down.

![](../../.gitbook/assets/no-fan-mount-gap.jpg)

## Version: Legacy

### General Fan Location

![Promega Fan Location](../../.gitbook/assets/hfsklgqrnj6zz2yw-fanlocation.jpg)

### Warning

Do not attempt to start the guide with a hot extruder. Wait for the hot end\(s\) of the printer to cool before continuing with this guide.

### Tools

1. T6 Torx Screwdrive
2. T10 Torx Screwdrive
3. Needlenose pliers
4. Container

### Additional Hardware

_**NONE**_

### How To Uninstall Nozzle Fan

Switch off power to the system. Wait for nearby components of the printer to cool before attempting to remove the fans.

Move the bed all the way down. Let it rest on the limit switch. 

{% hint style="warning" %}
Do not place a significant amount of weight on the bed. It could skip your bed.
{% endhint %}

Remove the four T6 Torx bolts holding the nozzle fan duct, IR probe board and limit switch mount to the extruder assembly. 

Place the four T6 torx bolts, two M2 nuts and two M3 nuts aside in a container.

![Right side of extruder](../../.gitbook/assets/fan-screw1.jpg)

![Left side of extruder](../../.gitbook/assets/fan-screw2.jpg)

Once all the screws are removed, you should be able to pull the nozzle fan duct down and out of the extruder assembly. You can now remove the nozzle fans from the fan duct by simply pulling them out.

![Unscrewed Fan Mount](../../.gitbook/assets/fan-pull-out.jpg)

Place the fan duct aside, now we will remove the nozzle fan connector from the cable assembly on the back of the extruder assembly.   
Find the connector pictured below and remove it with needlenose pliers, you might have to remove the thermistor connector first in order to reach the nozzle fan connector.

![](../../.gitbook/assets/noz-fan-disconnect.jpg)

Once you disconnect the nozzle fan connector you should be able to pull out the nozzle fans.

### How To Install Nozzle Fan

The orientation of your nozzle fans is very important, be sure that you have your new nozzle fans inserted into the fan duct as shown below. This will blow the air out the center of the fan duct. 

{% hint style="warning" %}
If you flip your nozzle fans it will result in the fans attempting to blow air out the sides of the fan duct \(not a great idea!\).
{% endhint %}

![](../../.gitbook/assets/noz-fan-mount-positions.jpg)

Push the nozzle fan connector up through the extruder assembly and above the X-axis rod. The fan connector should be right next to its female connector. Plug it in with needlenose pliers. 

Before you continue reassembling your printer it is best to check that both new fans work. Double check your wiring.

Turn on your Promega, connect to the printer, and send the g-code command to turn the nozzle fans on. Remember that these fans are PWM controllable.

By entering the G-code command

```text
 M106 Pn Sm 
```

you can turn the fans on or off.

 `n` specifies the port number that the fan is plugged into.

 `m` represents the desired speed of the fan. This can be a value of 0 to 255, where 0 is off and 255 is the highest setting.

Once you have verified that your nozzle fans work you can slide your fan duct back into place. Ensure that the IR probe board is right on the side as shown in the image in step 4. 

Screw the bolts back into the IR board and attach the limit switch mount. Ensure that you fasten the nuts on the bolts of the limit switch mount. 

Make sure both the limit switch mount and the IR probe board are level.

![Nozzle Fan Screw](../../.gitbook/assets/fan-screw-3.jpg)

### How To Uninstall Cold-Section Fan

Switch off power to the system. Wait for nearby components of the printer to cool before attempting to remove the fans.

Remove the two screws holding the fan to the extruder assembly, one of these screws will be held in place with glue, you might have to use some force. When the fan is removed, place the nuts and bolts in a separate container.

![](../../.gitbook/assets/cold-section-fan1.jpg)

Move the fan over to the back of the extruder assembly, and observe where the cold-section fan is currently plugged in. The new fan will have to be plugged into the same location.

![](../../.gitbook/assets/cold-section-fan2.jpg)

Use needlenose pliers to carefully remove the male fan connector from the female connector at the back of the cable assembly. You might have to unplug the heater cartridge connector in order to reach the fan connector.

![](../../.gitbook/assets/cold-section-fan3.jpg)

### How To Install Cold-Section Fan

Connect the cable of the new fan. Plug the new fan into the same location that the old fan was plugged into. Before you continue with reassembling the printer, test if the fan works. Double check your wiring and turn on your Promega, the fan should start spinning immediately.

Route the wire to the fan as shown in the image below. Remember to plug in the heater cartridge if you unplugged it.

Insert the bolts with the M4 nut spacers to fasten the fan back to the extruder assembly. Pay attention to path of the fan wire. We recommend applying glue to one of the nozzle fan bolts to prevent it from loosening with vibration.

![](../../.gitbook/assets/cold-section-fan4.jpg)



