# Setup Your Network

## Network Setup

Connecting to your Promega via your local network is very useful as you get access to the Duet Web Console. You can connect your Promega to your local network via the Ethernet port on the Duet Maestro. Once the network settings are properly configured, you should be able to connect to the Duet board and access the Duet Web Console. In order to configure your network settings you will need to edit files on the microSD card. The Promega microSD card has a configuration file called _config.g_ in the _sys/_ folder. This file contains all the necessary information in order to connect to your network.

### First-Time Start-up

If this is your first time starting up the printer, follow this section. The pre-configured Promega network settings, which are loaded onto every SD card when the printer goes out our door, utilize DHCP in order to get an IP address from your router. This should allow your printer to connect automatically to your network. If this is successful, you should be able to enter the machine name into your browser tab followed by a forward slash "/". This could look like this: **my\_promega\_name/**. If you are connecting to your Promega for the first time, you should be able to enter **promega/** into a browser URL textfield in order to connect.

### Configuring Network Settings

If the First-time start-up connection did not work, or you want to set-up your own network settings, you can follow the following section. It is also possible to set a static IP address for your Promega, this will allow you to connect to that IP address to connect to your printer. For example, a static IP address could be the following: _192.168.1.144_ or _10.0.0.214_. However, the type of IP address is dependent on your network. If you are unable to connect your Promega to your internal network by directly connecting an Ethernet cable to the router, follow the Network Bridging section below. Network bridging will allow you to access the Duet Web Console with the Ethernet cable directly connected to your computer.

### Changing the Network Settings via SD

1. Before removing your microSD card from your printer, we recommend you turn off your printer. This reduces the risk of damaging your Duet Maestro. Once the printer is powered off, press the SD card into the board in order to remove it. For more guidance on the SD card check out [this guide.](https://m3d.gitbook.io/promega-docs/getting-started/accessing-your-sd-card)
2. Insert the microSD card into your computer with the microSD card reader. Open the _machine\_access.g_ file. This file will be in the _sys/_ folder and configures the network settings of your Promega. It is best to open the file with a text editor like [Notepad++](https://notepad-plus-plus.org/download/v7.5.6.html) or WordPad \(Default Windows Accessory\). The default Windows Accessory _Notepad_ is not recommended as it does not separate the G-code commands into individual lines.
3. There are two options for configuring your network: DHCP and static IP. If you utilize DHCP, your network router will assign the control board an IP address. You will then be able to connect to the printer using the printer name you define in the configuration file. **DHCP is the recommended option if you are unfamiliar with networking.** Using a static IP means that you give the Promega a unique and free IP address on your network. You will then be able to connect to the Promega by entering that IP address into a browser tab. Choose the tab below \(DHCP or static IP\) depending on your choice.

{% tabs %}
{% tab title="DHCP" %}
Complete these steps if you want to connect to your Promega using the DHCP option.

a. Open the file _machine\_access.g_ and find the `M550` command located in this file. The `M550` command sets the machine name, this command syntax requires a P parameter before the machine name. Therefore, if you wanted to name your printer _unicorn_ you would type `M550 Punicorn`. Change the printer name to something you prefer, remember this name as you will use it to connect to your printer. By default the machine name is `promega` .

b. Find the `M552` command in the _machine\_access.g_ file. The `M552` command sets your IP address and enables or disables the network. In order to set your network setting to DHCP, the following command should be entered: `M552 P0.0.0.0 S1`. The P parameter allows you to define an IP address, entering `P0.0.0.0` enables DHCP. The S parameter enables \(`S1`\) or disables \(`S0`\) network, because you are setting up your network you should set the parameter to `S1`.

c. Ensure that the other `M552` command is commented out!

Your _machine\_access.g_ file network settings for connecting to a network using DHCP could look like this:

```text
 ; machine_access.g
 ; June 29, 2018

 ; Set the machine name and IP address in here

 M111 S0                       ; Debugging off
 M550 Punicorn                 ; Set machine name, in this case typing unicorn/ would connect you to the printer

 ; M551, No Machine Password
 ; M540 PBE:EF:DE:AD:FE:ED     ; Set MAC address, this can be used to assign a given IP in the DHCP
 M552 P0.0.0.0 S1             ; Use this to enable DHCP
 ; M552 P192.168.1.112 S1     ; This would set a static IP address but it is commented
```

In the example above your machine name would be _unicorn_. Continue to the step below.
{% endtab %}

{% tab title="Static IP" %}
**Static IP Address**  
Complete this if you want to connect to your Promega with a Static IP address.

a. Find the network section in the _machine\_access.g_ file. Find the `M552` command. This command sets your IP address and enables or disables the network. In order to set your network setting with a static IP the following command should be entered: `M552 Pnnn S1`. Where `nnn` is your preferred IP address. Your IP address depends on your local network. It could be in the form of \(_192.168.1.216_ or _10.0.0.216_\). The S parameter enables \(`S1`\) or disables \(`S0`\) network, because you are setting up your network, and want it enabled, you should set the parameter to`S1`.  
b. Choose an IP address on your network that is free. Typically "higher" IP addresses will work, such as `192.168.1.216` instead of `192.168.1.11` . It is best to log-in to your router in order to check which IP addresses are free.  
c.. Ensure that the other `M552` command is commented out!

Your _machine\_access.g_ file network settings for connecting to a network with a static IP address could look like this:

```scheme
 ; machine_access.g
 ; June 29, 2018

 ; Set the machine name and IP address in here

 M111 S0                       ; Debugging off
 M550 PPromega                 ; Set machine name, type promega/ in your browser!

 ; M551, No Machine Password
 ; M540 PBE:EF:DE:AD:FE:ED     ; Set MAC address, this can be used to assign a given IP in the DHCP
 ; M552 P0.0.0.0 S1             ; Use this to enable DHCP, in this case commented
 M552 P192.168.1.112 S1        ; Set Static IP address and enable networking
```

In the example above you should be able to connect to your printer by entering the IP address `192.168.1.112` in your browser tab.

If you want to find out the structure of your internal IP address, open a command prompt on a computer connected to the same network as the promega and enter the command `ipconfig`. \(Open a command prompt by pressing _Windows Key_ + _R_, type _cmd_ and press _Enter_\). This will print your network settings and status, look for the "IPv4 Address" number. That number represents an internal IP address on your network. Of course this IP address is occupied by your computer and therefore not a valid IP address for your Promega! ![kJe3IhIAIOE1puFU-ipv4address.PNG](../.gitbook/assets/kje3ihiaioe1pufu-ipv4address.PNG)

Continue to the step below.
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="DHCP" %}
1. When you have made the necessary changes to your network settings, save the _machine\_access.g_ file and safely eject the SD card. Insert the SD card back into the Duet board. Ensure that the Ethernet cable is connected properly to the Duet board and turn the board back on. It will take a while for your printer to boot and connect to the network \(~30 seconds\). When your Ethernet cable is properly connected to the board, the green LED should be flashing and the yellow LED should be solid.   ![1NXuMREA7qVlTdEd-flashingethernet.gif](../.gitbook/assets/1nxumrea7qvltded-flashingethernet.gif) 
2. Once your printer has had the time to start up, open a browser tab on a computer **connected to the same network as the printer**. In the browser URL textfield enter:
   * Your printer name followed by a forward slash "/" if you used DHCP. For example, `unicorn/`, if you named your printer "unicorn" \(nothing wrong with that!\). 
3. If the connection is successful the Duet Web Console should be shown. You have completed the network setup.
{% endtab %}

{% tab title="Static IP" %}
1. When you have made the necessary changes to your network settings, save the _machine\_access.g_ file and safely eject the SD card. Insert the SD card back into the Duet board. Ensure that the Ethernet cable is connected properly to the Duet board and turn the board back on. It will take a while for your printer to boot and connect to the network \(~30 seconds\). When your Ethernet cable is properly connected to the board, the green LED should be flashing and the yellow LED should be solid.   ![1NXuMREA7qVlTdEd-flashingethernet.gif](../.gitbook/assets/1nxumrea7qvltded-flashingethernet.gif) 
2. Once your printer has had the time to start up, open a browser tab on a computer **connected to the same network as the printer**. In the browser URL textfield enter:
   * Your printer's IP address set in the configuration file with the M552 command. It could look like this `192.168.1.216`. 
3. If the connection is successful the Duet Web Console should be shown. You have completed the network setup.
{% endtab %}
{% endtabs %}

**Continue on to the** [**Accessing Web Interface**](https://m3d.gitbook.io/promega-docs/getting-started/accessing-web-interface)**, the next chapter in the** [**Getting Started**](https://m3d.gitbook.io/promega-docs/getting-started) **guide.**

**Network Bridging**

If you are unable to connect your ProMega to your internal network it is possible to use the ethernet cable to connect the printer directly to your computer. In order to do this, complete the _Connecting to the Promega via SD: Static IP_ section, remember the static IP you give the printer, but instead of connecting the ethernet cable to your network, connect it to your computer and follow the guide below.

**Windows**

1. Open Network Connections, you can do this by opening the _Control Panel &gt; Network and Internet &gt; Network and Sharing Center &gt; Change adapter settings_

   ![ixszFpYVwOAR4Mn3-networkandsharing.PNG](../.gitbook/assets/ixszfpyvwoar4mn3-networkandsharing.PNG)

2. Once you have the _Network Connections_ window open. Here you will see your network adapters. The ethernet adapter represents your connection to the Duet board. Find your current network adapter, presumably a WiFi adapter. Ctrl + click both the Ethernet adapter as well as the current network you are using. Then right click on one of the selected adapters and select _Bridge Connections_.

   ![ztReV3zkFYeyGJ7s-networkbridge.png](../.gitbook/assets/ztrev3zkfyeygj7s-networkbridge.png)

3. This will create a new Network Adapter called _Network Bridge_. You should now be able to connect to the ProMega with the static IP address you determined earlier. Enter the static IP address into a browser URL textfield.

Continue on to the [Accessing Web Interface](https://m3d.gitbook.io/promega-docs/getting-started/accessing-web-interface), the next chapter in the [Getting Started](https://m3d.gitbook.io/promega-docs/getting-started) guide.

### Configuring Multiple Devices to the Same Network

If you are adding multiple different Promegas to the network it will change the procedure. This is because a network will require a unique machine name or IP address in order to work.

{% tabs %}
{% tab title="DHCP" %}
If you are using DHCP you will have to give the two different Promegas different unique machine names with the`M550` command. By default the Promega will be called Promega with `M550 PPromega` , so you will have to open _machine\_access.g_ and change the `M550` .
{% endtab %}

{% tab title="Static IP" %}
If you want to configure multiple Promegas with static IP addresses you will have to give the Promegas each a unique IP address that is free on your network with the `M552` command. The machine name does not have to be unique.
{% endtab %}
{% endtabs %}

Continue on to the [Accessing Web Interface](https://m3d.gitbook.io/promega-docs/getting-started/accessing-web-interface), the next chapter in the [Getting Started](https://m3d.gitbook.io/promega-docs/getting-started) guide.

For additional help connecting to the printer via USB and Network setup, visit the following links:

1. [Duet3D Network Setup](https://duet3d.dozuki.com/Guide/1.%29+Getting+Connected+to+your+Duet/7)
2. [RepRap Firmware G-Code Wiki](http://reprap.org/wiki/G-code)
3. [M3D Support](https://printm3d.com/support)
4. [Duet Forum](https://forum.duet3d.com/): For Duet and RepRap firmware specific questions

## The Web Interface

The Duet Maestro allows control via the Duet Web Console. We highly recommend connecting to your Promega via your network so that you can make use of this! Follow the guide below to learn more about the Duet Web Console. If you have not yet connected your printer to your network, follow the [Network Setup](https://m3d.gitbook.io/promega-docs/getting-started/network-setup) guide.

### The Duet Web Console

![Duet Web Console](../.gitbook/assets/emt1fnpmleipvcwg-dwchomepage.PNG)

The web console is divided into two halves. The top half features functions to monitor and analyze the status of your printer. The bottom half focuses on control of your printer and configuring its settings.

#### Status

The status part of the web page indicates various readings to describe the current state of your printer.

#### **Tools & Temperature**

On the left half is a table that allows you to monitor the temperature of the different tools as well as the bed. The temperature readings are important to keep track of. With the table as well as the graph you can keep track of all the temperatures of the components of your 3D printer.A value of 2000 C for any of the components in this table indicates problems with a temperature sensor.

![Temperature Readings](../.gitbook/assets/jm1k1cnqkqqtq02c-temperaturereadings.png)

By clicking on the textfields of the tools in the table you can change the temperature of the tools. Press enter to update the temperature. You should see a slow increase in temperature. The _Active_ column represents the temperature of a tool when it is **selected**, the _Standby_ column represents the temperature of a tool when it is **not selected ,** but was previously selected. It is best to have a low standby temperature for a tool, so it does not heat up unexpectedly.

By clicking on the tool names in the _Tool_ column you can change your currently selected tool.

![](../.gitbook/assets/selectedandnotselectedtools.png)

The temperature graph provides helpful insight of the temperature of your tools and bed over time. This can be helpful to spot oscillations in temperature, as seen in the image below, or heater faults and other issues.

![Temperature Chart](../.gitbook/assets/2yy87zxfggiujlap-temperaturechart.PNG)

**Machine Status**

The machine status tab includes the position information of the printer. The head position information displays where the printer currently thinks it is. This is very important to keep track of to minimize the risk of crashing the printer. The X, Y and Z values represent the different axes of the 3D printer. Normal values for these fields are listed below in this table.

|  | Axes Limits |  |
| :--- | :--- | :--- |
|  | Max \(mm\) | Min \(mm\) |
| X - Axis | 388 | 0 |
| Y - Axis | 388 | 0 |
| Z - Axis | 377 | 0 |

The extruder drive values can vary greatly as you perform prints. The voltage in value is helpful as it can help you figure out electrical problems. Optimally it should remain near 24V when none of the printer components are running. The Z-probe value is important as well. This value will change whenever either Z-probe, the limit switch or the IR probe, is toggled. Testing the Z-probe before running probing or leveling commands \(such as `G30`, `G32` or `G29`\) is extremely important and can prevent crashes. When the Z-probe is not toggled the value should rest near 0.

![Machine Status](../.gitbook/assets/38yr6g32ydtjmfdm-machinestatus.PNG)

### Control

In order to control your printer, the bottom half of the web console features 6 different tabs on the bottom left side with different features. These tabs allow you to visit different functions of the printer as well as send commands.

**Machine Control**

![Machine Control](../.gitbook/assets/z81qrjdadnqori0d-machinecontrol.PNG)

The Machine Control tab features different buttons in order to control different assemblies of the printer. This feature is helpful to load filament or move the extruder carriage to a specific point in the printer. Be careful with using these buttons as it can crash the printer. Remember the direction that you will send an assembly toward as you press these buttons. Pressing the positive Z buttons will send the bed downward, and pressing negative Z buttons will send the bed up.

**Print Status**

![Print Status Screen](../.gitbook/assets/jsgiizguus48ntax-printsettingsscreen.PNG)

The print status tab is helpful when printing. It includes all kinds of information to analyze during a print. Use the Z Baby Stepping window to change the offset of the nozzle to the bed during a print. Use the Speed and Extrusion factors to change the speed and extrusion rate of the print. These settings can be very helpful to get the first layer to stick, but be careful as these settings can damage your print quality. Use the pause button to temporarily stop the print. Once you pause the print you can resume or stop the print. This screen will also display other statistics during a print such as layer time and length of filament used.

**G-Code Console**

![G-code Console](../.gitbook/assets/levflucsim14bjh0-gcodescreen.PNG)

The G-code console is a vital to an experienced 3D printing user. This tab allows you to enter any RepRap Firmware supported command. The printer will execute any command entered here and print feedback and errors. Visit the [RepRap Firmware G-Code](https://reprap.org/wiki/G-code) website to learn more about all possible G-codes. Be careful when entering G-code commands as the printer will execute whatever you command you send it.

**G-code Files**

![G-code File Screen](../.gitbook/assets/vuhuksyxberfyakj-gcodefilescreen.PNG)

This tab is used to upload G-code files to the Duet board. Use the _Upload G-code File\(s\)_ button in order to upload a _.gcode_ file to the printer in order to print it. Click on an uploaded file in order to print it. You also have the ability to create directories here in order to organize your files. This is a great idea if you have a 8Gb microSD card.

**Macros**

![Macros Screen](../.gitbook/assets/fewjngk0vnk3rcgd-macrosscreen.PNG)

User defined macros are stored in this tab. Use the dark-blue _Upload Macro File\(s\)_ button to upload _.gcode_ macro files. Macros are useful when you find yourself repeatedly performing a sequence of G-code commands. You can easily put these commands into a macro file and upload it here. Click a macro file in order to execute it.

**Filaments**

![Filaments Screen](../.gitbook/assets/dlsuoxidsmtdjsar-filamentsscreen.PNG)

Utilize this tab in order to define printer filament settings. This can also be performed in Slicer Software.

**Settings**

![Settings Screen](../.gitbook/assets/726ggigphugtd2tt-settingsscreen.PNG)

**This tab is one of the most important**. This tab allows you to change the _sys/_ directory in your SD card and define other user settings. Whenever the guides in the future reference a change that is necessary to the system files such as _config.g_ or a _machine.g_ file, you can change the files in the settings tab. The Settings tab includes more tabs:

* General: Includes firmware and web console information
* User Interface: Change the look and feel of the Duet Web Console
* List Items: Includes web page suggested options
* System Editor: A very useful tab to change files in the _sys/_ directory of your microSD card. **You will find the** _**config.g**_ **file here as well as other system G-code files.**
* Machine properties: Defines properties of the different drives \(motors\) of the printer.
* Tools: Defines the properties of the tools.

### Additional Resources

* Duet3D Wiki: [Duet Web Control Manual](https://duet3d.dozuki.com/Wiki/Duet_Web_Control_Manual#main)
* [Duet Web Control GitHub Repository](https://github.com/chrishamm/DuetWebControl)

Continue on to the [SD Card Structure](https://m3d.gitbook.io/promega-docs/getting-started/sd-card-structure), the next chapter in the [Getting Started](https://m3d.gitbook.io/promega-docs/getting-started) guide.

