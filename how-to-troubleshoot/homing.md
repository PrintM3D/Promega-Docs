# Homing

## Won't Complete: Just Keeps Skipping

### Problem

I starting homing. The printer starts moving and then it just keeps skipping. It never homes.

### Solution

#### **Your limit switch may not work.**

Let's see if your limit switches works.

Run:

```text
M18 X Y; This disables the CoreXY (motion) motors
```

Slowly move the extruder head to the center

Run: 

```text
M564 H0; Let's you move the motors without homing.
G91;
```

Manually engage \(press down\) on the X, Y, and Z Limit Switch. We recommend using tape.

{% hint style="warning" %}
We discourage using your fingers. Do so at your own risk. 
{% endhint %}

Run:

```text
G1 Y100 S1;
G1 X100 S1;
G1 Z100 S1;
```

#### Let's evaluate:

If the _**extruder moves forward or backward,**_ 

* The Y Limit Switch is not working.

If the _**extruder moves to either side**_, 

* The X Limit Switch is not working.

If the _**bed moves down**_,

* The Z Limit Switch is not working. 

## Homing Z: Weird Z Endstop Values

### Problem

I am calibrating my z endstop value. After I home Z, the Z endstop value is not what I put.

### Solution

#### Your new z endstop value may not be saved.

Let's check what your current Z Endstop Value is.

Go to _**Settings**_. Then click the _**System Editor**_ tab. Open the _**machine\_zendstop.g**_ file. 



Scroll down to the last line.

Check your Z Endstop Value. Is this the calibrated value?



{% tabs %}
{% tab title="YES" %}
Change it to a new value.

Click "Save Changes" button.

Home the Z.

Check to see if your Z Endstop Value is correct.

If not, continue reading.
{% endtab %}

{% tab title="NO" %}
Continue reading. 
{% endtab %}
{% endtabs %}

#### Your machine boundaries may be too low.

Let's check if your machine boundaries are interfering. 

Go to _**Settings**_. Then click the _**System Editor**_ tab. Open the _**machine\_axisdimension.g**_ file. 



Look for the line labeled " Maximum"

```text
M203 X# Y# Z#; Maximum
```

Is this value smaller than your new Z Endstop Value?

{% tabs %}
{% tab title="YES" %}
This value MUST be at least 0.5 mm above your calibrated Z Endstop Value.

Add 0.5 mm to your new Z Endstop Value. This is your new Maximum Z Value.

Change the Z value to the new Maximum Z Value.

Click "Save Changes"

Home the Z.

Check to see if your Z Endstop Value is correct.

If not, continue reading.
{% endtab %}

{% tab title="NO" %}
Continue reading. 
{% endtab %}
{% endtabs %}

#### Your mesh compensation may be changing the value.

Home the Z.

Run:

```text
G29 S2
```

The Z Endstop Value should now be the calibrated value.

Mesh compensation is changing the value of your Z Endstop Value. 

Proceed with printer operation.

