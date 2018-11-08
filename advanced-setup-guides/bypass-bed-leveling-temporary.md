# Bypass Bed Leveling \(Temporary\)

This guide should be used under these certain conditions:

{% hint style="info" %}
You understand this leveling method is FAST and TEMPORARY. The leveling will be undone after a Z homing, Home All, or power cycle. 
{% endhint %}

{% hint style="info" %}
You want to avoid mesh compensation or Z endstop calibration troubleshooting.
{% endhint %}

{% hint style="info" %}
Your print is small or medium sized.
{% endhint %}

#### 

#### Let's get started.

Physically level the bed. Follow the [Mechanical Bed Leveling](../repair-and-maintenance/mechanical-bed-leveling.md) guide.

Home your X and Y only.

![](../.gitbook/assets/home-xy.PNG)

Move your extruder to the region you will print on. 

![](../.gitbook/assets/print-position.PNG)

Enter

```text
M564 S0 H0
```

```text
G29 S2
```

```text
M290 R0 S0
```

{% hint style="info" %}
None of the codes above have any movement involved. 

Make sure they are executed
{% endhint %}

![Shows a history of executed codes.](../.gitbook/assets/gcode-history.PNG)

Heat your bed to desired temperature.

![](../.gitbook/assets/temp-selection.png)

Move the bed until is it paper-width apart from the nozzle. 

{% hint style="info" %}
Paper-width should have mild resistance when moved around.
{% endhint %}

Enter

```text
G92 Z0
```



Check your z position value is set to 0.

![](../.gitbook/assets/z-position-zero.PNG)

Start your print.

{% hint style="warning" %}
Make sure your print DOES NOT have 

ANY homing commands \(e.g. G28\)

OR 

ANY reference to `M98 Pprint_startgcode.g`
{% endhint %}

![Highlighted lines are homing lines.](../.gitbook/assets/homing-inside-gcode.PNG)

