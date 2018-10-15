# Common Terminology

The Duet Web Console includes a tool system. Tools allow you to quickly change between different extruder configurations. For example, if you were printing with your right K'Tana nozzle but wanted to start printing with your left K'Tana nozzle, you can change tools. The default SD configurations released by M3D on the [Promega GitHub repository](https://github.com/PrintM3D/Promega) enable a number of tools depending on your mounted extruder head \(K'tana or Compound\). The guide below includes an introduction to tools and how to use them.

## What are tools?

A tool is a defined extruder setup. A tool will be configurated to use a specific extruder motor or motors at specific speeds. If you are printing with the compound hotend, you will have a tool that allows for mixing 50% on each side as well as two tools that extrude with only one extruder \(left and right\). If you perform the correct setup in your slicer, you can switch between these tools while printing. In order to switch between tools you can enter the command `Tnnn`, where `nnn` is the tool number. If you wanted to switch to tool 1, you can enter the command `T1` in the G-code Console. The tools can be viewed in the top right corner of the Duet Web Console. An underline will indicate which tool is currently selected.

> Before you can start heating up a hot-end you will have to select the appropriate tool. Read the _Tools and Temperature_ section below for more information.

## Default Tools

### K'Tana Tools

The K'Tana extruder head features two different filament inputs and outputs. This allows you to print with two different materials and switch while printing. This allows for some really neat and complicated prints. Below is a list of the predefined tools 1. Tool 0: "Ktana Single Left": Uses just the left extruder to print 2. Tool 1: "Ktana Single Right": Uses just the right extruder to print

### Compound Tools

The compound extruder allows you to mix two different filaments coming in. There are three different default tools for the mixing configuration. 1. Tool 0: "Mixing": A Tool that prints with both extruders at a 1:1 ratio. 2. Tool 1: "Mixing as Single Left": A tool that prints with just the left extruder. 3. Tool 2: "Mixing as Single Right": A tool that prints with just the right extruder.

## Tools & Temperature

The temperature table on the Duet Web Console includes textfields for both Active and Standby temperatures of the extruder. The active temperature represents the temperature, in degrees Celsius, that the tool will go to when it is selected. **If no tool is selected, no nozzle will heat up**. This is the case whenever a print is cancelled. The firmware will deselect all tools. To gain temperature control again, select your desired tool. The standby temperature is the temperature the tool will go to when it is not selected, but was previously selected. This is useful for printing with the K'tana to avoid long heat-up times in between filament switches or collisions with the print.

> Currently there is a bug in RepRap firmware with extruder movement. The feedrate of a 50/50 mixing extrude only move will extrude sqrt\(2\) slower than the given `F` parameter.

A Note about High Temp nozzles:

> High temp nozzles are NOT intended for use with low temp materials, like PLA. High temp nozzles are specifically designed for use with self-lubricating high temp materials, such as nylon. High temp nozzles differ from standard/low temp nozzles most importantly in the inner coating. The low temp nozzles have a coating to reduce friction of the low temp materials that is not compatible with the high heats of the high temp nozzles. High temp nozzles do not have this coating, and because of this, low temp materials will not print well and may clog frequently or flow poorly. In general, only use the high temp nozzles with materials that require a high temp for printing.

Continue on to the [Important G-Code Commands](https://m3d.gitbook.io/promega-docs/getting-started/important-g-code-commands), the next chapter in the [Getting Started](https://m3d.gitbook.io/promega-docs/getting-started) guide.





This guide serves as a brief introduction to G-code commands. It will list the most useful and important commands to allow proper control of the Promega.

## An Introduction to G-Code

G-code is frequently used programming language to control machine tools, such as a 3D printer. G-code is sent to the printer and promptly executed by a control board, in the Promega's case, the Duet Maestro. What each G-code command does depends on the firmware type the board is running. The Promega runs Reprap firmware, you can find an in-depth list of all supported G-code commands on the [Duet3D Wiki: G-code](https://duet3d.dozuki.com/Wiki/Gcode).

G-code commands are sent and interpreted one line at a time. G-code commands typically include a letter followed by a number. In RepRap firmware the first letter of a command will usually be a `G`, `M` or `T`. This letter will then be followed by a number. Together, a letter and number specify a command. For example, `G1` is the move command. However, there is little you can do with just the move command `G1`. So the initial command is typically followed by sequences of letters and numbers called parameters. For example `G1 X100 Y200`, which will move the printer to the 100mm X and 200mm Y position. `X100 Y200` are both parameters in this case. Use the guide below to get an introduction to the most important and useful G-code commands to have as a beginner. There are many more G-code commands that RepRap firmware supports. Be sure to use the link above to continue learning new G-code commands.

### Important G-Code Commands

* `M112`: Emergency stop, will stop all heaters and motors. A reset with `M999` or power cycle will be required.
* `M999`: Reset the board. This has to be done after the board is emergency stopped or an error has halted the boards operation.
* `G0 & G1`: Move motors or axes, these are the primary movement commands of many printers. There is currently no difference between `G1` and `G0` for RepRap firmware. These commands are followed by parameters to identify distance, feedrate and motors to drive. `G1 Xnnn Ynnn Znnn Ennn Fnnn Snnn`
  * `X, Y` and `Z` represent the different axes. `nnn` represents the distance to travel along that axis.
  * `E` represents an extruder motor. The extruder motor distance is specified just like the X, Y and Z parameters. `E50` will move the extruder to the 50mm position.
  * `F` Allows you to specify a feedrate in mm/s. Feedrates vary greatly depending on whether you are printing or travelling.
  * `S` Enables or disables the endstop check. If the endstop is toggled while moving the printer stops, the `S1` flag enables detection, `S0` disables detection.
* `Tnnn`: Tool select G-code. Where `nnn` defines the tool
* `M106 Snnn`: Turn on fans with speed `nnn`. `nnn`    can be a value between 0 and 255. For older versions of _config.g_ `M106 P2 Snnn` will enable fan control.
* `G30`: This command allows a single Z-probe at the current location. The z-probe should be properly configured before sending this command. Follow the [Z-Probe Calibration & Bed Leveling](https://promega.printm3d.com/~/edit/drafts/-LHcmtefoysyNAUG9AZG/getting-started/z-probe-calibration) guide for more explanation on this topic.
* `G29` : This command runs the bed leveling procedure. Please properly deploy the Z-probe prior to sending this command, use the link above.

