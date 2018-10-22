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

