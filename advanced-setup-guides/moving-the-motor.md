# Moving The Motor

## Manually Move Motors

Before you power on your motors, you can manually move the extruder head around the printer. 

Follow the steps below in order to start moving the printer:

Move the extruder head to the center of the printer by hand. This should not take a lot of effort to do as long as the motors are not powered. 

{% hint style="warning" %}
Do Not manually move any motors _**QUICKLY**_. You could damage your electronics.
{% endhint %}

Once you move the motors, the motors will be powered and resist any force acted on them.

Go to the _Machine Control_ tab of the Duet Web Console.

![Machine Control Tab in Duet Web Console](../.gitbook/assets/z81qrjdadnqori0d-machinecontrol%20%281%29.PNG)

Press _Home All_, this will home all the axes of the printer and ensure that the origin of the printer is located at the front-top-left corner of the 3D printer. 

After the homing process is complete, you can see that the position of the 3D printer is updated in the _Machine Status_ tab on the Duet Web Console.

Press the X-10 button in the _Head Movement_ window. 

This will move the extruder carriage of the printer 10mm in the negative X direction, this should be towards the left if you are facing the front of the printer. 



Now press the Y-10 button.

This will move the printer -10 mm in the Y-direction. If you are facing the front of the printer, this should send the extruder carriage towards you. 



You can also press the Z buttons, but remember that the bed is all the way down and resting on the limit switch after the homing process. 

You will have to move the bed in the negative Z direction in order to move it up. 

Press the Z-10 button in order to move the bed up 10 mm.



You can keep pressing the buttons to move the extruder carriage to become more familiar with the directions and coordinate system of the Promega.

## **Absolute vs. Relative**

A 3D printer movement allows for two different modes, absolute and relative. 

These two terms are also used frequently in machining and other engineering processes.

### Absolute

 Absolute describes a position or command with respect to the origin or zero position. 

{% hint style="info" %}
The Promega origin is located in the Top-Left-Front corner. 
{% endhint %}

Run this to enter Absolute mode.

```text
G90
```



 **For example:**

Tell the printer to move \(20,20,20\). 

```text
G1 X20 Y20 Z20
```

Absolute mode will send the printer to the point where X = 20 mm, Y = 20 mm and Z = 20 mm.

If you told it again to go to \(20,20,20\) it would just stay there. The Duet would say: I am already there!



### Relative

Relative describes the position of a 3D printer relative to the previous point the printer was located at. 

Run this to enter Relative mode.

```text
G91
```



 **For example:**

Tell the printer to move \(20,20,20\). 

```text
G1 X20 Y20 Z20
```

Relative mode will send the printer 20 mm in the X-direction, Y-direction and Z-direction relative to its previous position. 

 If you told the printer to move \(20,20,20\) again, the printer will move 20 mm in the X, Y and Z directions for the second time.



#### This is the difference between absolute and relative.

#### Your printer will go to two completely different places depending on if you are in relative or absolute mode.

