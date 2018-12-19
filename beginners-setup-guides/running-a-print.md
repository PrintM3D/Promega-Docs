# Running A Print

Running a print is best done using the Duet Web Console. To connect to your Duet via a network, visit the [Network Setup]() guide. For an introduction on the Duet Web Console visit the [Accessing Web Interface]() guide.

This guide assumes you have properly configured your printer with all the previous guides. That means:

* You have homed all axes of your printer
* You have configured your Z-probe offset
* You have run and enabled mesh bed leveling
* You have loaded filament into the extruder

## Uploading the Print

In order to print something from the Duet board you must first upload the print to the Duet Board. This can be done via the Duet Web Console or by ejecting the SD card and uploading it with a computer. 

**Uploading a print via the Duet Web Console is the easiest way**. 

{% hint style="info" %}
To print on the Duet board your print must have a _.gcode_ file extension. 

To create a G-code file you must slice a model with a slicer. Look at the [What is Slicing?](../advanced-setup-guides/what-is-slicing.md) guide for guidance on how to create a _.gcode_ file.
{% endhint %}

### **Uploading via Duet Web Console**

![The Gcode Upload Button](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LH1ZPQUJrjMM5Ql5c--%2F-LHJKvRYSgPi9YCoq9TP%2F-LHJMO42BCgUjNoJGmEP%2Fuploadinggcodefiles.png?alt=media&token=41704a18-a635-42fe-942f-46ba13cc223e)

First, we will have to upload the G-code file we produced in the previous guide. 

Connect to the Duet Web Console on the printer. 

Then, press the _G-code Files_ button and then press the _Upload G-code File\(s\)_ button as shown in the image above. This will open a window which will allow you to select the G-code file you sliced. 

_Open_ your preferred file and wait for it to upload.

### **Uploading via microSD**

Power off your printer with the blue power switch.

Remove your microSD card from its slot on the Duet board by pressing it into the board. 

{% hint style="warning" %}
Be careful as the microSD slot on the board is fragile.
{% endhint %}

Insert the microSD card with microSD card reader into your computer.

Open up the drive and select the folder _gcodes_. Upload all the _.gcode_ prints you want into this folder.

When this has completed, safely eject the card and insert it back into the Duet board.

Power on the printer and reconnect to the Duet Web Console. 

You should now be able to see all your prints in the _G-Code Files_ tab on the console \(shown in the image above\).

## Printing the File

Once the file is uploaded, you can click the file in order to print it. A window will pop-up confirming that you are about to print something. Click _Yes._

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LH1ZPQUJrjMM5Ql5c--%2F-LHJKvRYSgPi9YCoq9TP%2F-LHJOTh2YY8lAkMkWcyu%2Fprintingthegcodefile.png?alt=media&token=9489e4ca-ad7f-4cec-bd54-d8a214adc48c)

## Monitoring Prints

Once you have selected a file to print it you can view the prints progress in the _Print Status_ tab.

![JsgIIZGuUS48ntAX-PrintSettingsScreen.PNG](../.gitbook/assets/jsgiizguus48ntax-printsettingsscreen.PNG)

With various buttons on this screen you can manipulate your print. This can help in certain cases.

### Speed Factor

Change the print speed with the _**Speed Factor**_ ****slider, on the right. This can be helpful to slow down your print during tricky parts, such as the first layer. 

### Z Baby stepping

With the _**Z Baby Stepping**_ buttons you can change the height of the Z during a print. This is very helpful to improve first layer stick during a print. 

### _Extruder Factors_

_**Extruder Factors**_ sliders can be used to change the flow rate of the extruders. 

{% hint style="warning" %}
Exercise caution when using these controls, improper use can quickly ruin your print.
{% endhint %}

### Print Statistics

Aside from these controls the Duet Web Console displays, a heap of cool statistics such as Layer time and length of filament required. 

{% hint style="info" %}
Remember that these statistics are estimates!
{% endhint %}

### Pause

At any point during a print you can pause the print with the orange _**Pause Print**_ button. This will execute a file on the microSD card called _pause.g_. 

This will remove the extruder head from the print, and retract filament but keep the temperature steady. 

You will then be able to execute G-code commands. 

{% hint style="warning" %}
Be careful as you can easily damage your print and printer if you move the extruder into the print. 
{% endhint %}

### Resume

Whenever you want to continue printing you can press _**Resume**_. This will execute _resume.g_. 

### Cancel

If you want to stop your print, you can press the _Cancel_ button. This will execute _stop.g._

This file is also called at the end of a print.



Continue on to the phase: [Common Terminology](common-terminology.md).

