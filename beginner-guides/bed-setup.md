# Get Your Bed Ready

## Setup Your Bed

### Setup 1: BuildTak Bed



### Setup 2: Glass Bed



## Setup Bed Probe

### Press Home All Button

![](../.gitbook/assets/homeall%20%282%29.PNG)

### Send the extruder toward center

```text
G1 X200 Y200
```

#### Minor G-code Lesson

G1 = Linear Movement

X\#\#\# = X position

Y\#\#\# = Y position

Z\#\#\# =  Z position

### Turn On The Bed

```text
M140 S60
```

#### Minor G-code Lesson

M140 = Set Bed Temperature

S\#\#\# = Bed Temperature \( Celsius\)

### Code Inputs

```text
G31 P999 X-40 y28.5 Z0
G29 S2
```

### Engage Bed Probe

![DISENGAGED](../.gitbook/assets/disengaged-bed-probe.JPG)

![ENGAGED](../.gitbook/assets/engage-bed-probe.JPG)

### Move Bed Up

```text
G1 Z20
```

### Probe

```text
G30
```

### Disengage Bed Probe

### Move Bed To Nozzle

Use these two buttons to move the bed up.

![Ignore the yellow home blocks \(for now\).](../.gitbook/assets/z-buttons.PNG)

Switch to a smaller step when you get close to the nozzle

### Record Z offset

![](../.gitbook/assets/z-offset.PNG)

### More Code Inputs

Replace \#\#\# with the Z offset number from the last step.

The number is POSITIVE ONLY.

```text
G31 P999 X-40 Y28.5 Z###
M564 S1
```

### Move Bed Down

```text
G1 Z20
```

### Engage Bed Probe \(Again\)

### Probe \(Again\)

```text
G30
```

### Disengage Bed Probe \(Again\)

### Check nozzle height

```text
G1 Z0
```

The bed should be about a paper sheet away from the nozzle.



### Save Into SD card.

Go to the System Editor tab under Settings

![](../.gitbook/assets/system-editor.PNG)

Look for "machine\_zprobe.g" \(and click\)

![](../.gitbook/assets/machine_zprobe.PNG)

Go to the last line of code.

![](../.gitbook/assets/g31line.PNG)

Replace the Z\#\#\# \(e.g. Z0.95\) with your new Z offset number \(POSITIVE ONLY\).

Save changes. 

Done.

## Map The Bed

### Note:

Assumption: Your bed probe has been setup. 

### Home Printer

![HOMED](../.gitbook/assets/homed.PNG)

![NOT HOMED](../.gitbook/assets/not-homed.PNG)

### Turn On The Bed

```text
M140 S60
```

### Engage Bed Probe

### Read The Bed

```text
G29
```

Wait for the probing to finish.

Check for any signs of green. 

* There should be some green.
* If not, your bed probe is NOT setup.

![](../.gitbook/assets/heightmap.PNG)

Click close.

You are ready to print.

