# Z Probe

## Z-probe Not Triggering

### Problem

Pressing the Z-probe does not result in a change in Z-probe value in the Duet Web Console _Machine Status_ table.

### Solution

This indicates a broken Z-probe or a problem with the Z-probe wiring. 

#### Z-probe Limit Switch Wiring Problem

The limit switch has an extension cable that extends into the cable chain as it goes to the Duet Board. It is possible that the Z-probe become disconnected from the extension cable during printer use.

#### Let's start.

Turn off the printer.

Open the cable chain segments until you find the connection of the Z-probe limit switch cable to the extension cable.

{% hint style="info" %}
 Read [this guide](../repair-and-maintenance/install-uninstall/cable-chain.md#how-to-open) for more instructions on how to open the cable chain.
{% endhint %}

 ![](../.gitbook/assets/zprobeconnector%20%281%29.jpg) 

Make sure the cable is properly plugged in. 

{% hint style="info" %}
Polarity does not matter as it is a switch.
{% endhint %}

You can apply glue to the connector to ensure that the connector stays in place. 

Make sure that the cable overall has enough slack for the gantry to move around the entire CoreXY plane.

#### Z-probe IR Probe Wiring Problem

A connection problem has been identified in some of the IR probe connectors. This is easy to fix with the following procedure.

#### Let's start.

Turn off the printer.

Unplug the connector from the IR board.

Take the contact of the white signal cable out of the connector. You will notice that this contact has a U shape on the end. This is meant to properly contact the pin on the IR board, but it does not. Crimp this U so that the tips come closer together.  
 ![](../.gitbook/assets/z-probecable.jpg) 

When inserting the white cable back in the connector it might help to apply a little bit of superglue to keep it in place.

Plug the connector back in the IR board.

Put the fan duct and IR board back in their place.

Test the IR Z-probe.

## Error: Z-probe Triggered Before Move

![](../.gitbook/assets/errorzprobetriggeredbefore.png)

### Problem

The probing procedure does not start and the Error: Z-probe Triggered Before Move is  printed in the console.

### Explanation

This indicates that the firmware has detected a triggering Z-probe value before it has even started moving the Z-platform. This can be seen in the _Machine Status_ table as the _Z-probe_ value will usually be 1000. The procedure here is attempting to move the Z-platform to the Z-probe in order to trigger it, but the Z-probe is already triggered.

### Solution

Test that the Z-probe value in the Duet Web Console is toggling correctly.

Ensure that the Z-probe is properly connected.

Ensure that the Z-probe is properly configured with the `M558` command.

## Error: Z-probe Not Triggered During Move

![](../.gitbook/assets/errorzprobenottriggered.png)

### Problem

As the image above indicates, the Error: Z-probe Not Triggered During Move is printed out and the probing operation has failed. If the printer was moving during the probing command, the printer stopped moving before the Z-probe was triggered.

### Explanation

This error is actually a fail safe, the printer is preventing what it presumes is a crash. Since the printer does not know where the mechanical limits of the printer are, it assumes the software limits are the limits of its motion. When the printer is performing its probing procedure it reaches the axes limit before the Z-probe is triggered and prints the error above.  

### Solution

Disable axes limits with the command `M564 S0`

Make sure that the Z-probe value on the Duet Web Console changes when the Z-probe is supposed to be triggered.

Ensure that the printer never reaches a value less than 0 in the Z, during a probe move. You can do this by sending the command `G92 Z50` while the printer is less than 50mm away from the nozzle.

{% hint style="warning" %}
Travelling to a small Z-value after you do this will crash the printer!
{% endhint %}

