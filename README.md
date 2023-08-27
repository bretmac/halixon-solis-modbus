# Halixon Solis Modbus Data Logger - Introducing the HAL-100

A data logger for the Solis Inverter that allows you to send data to Home Assistant via MQTT for realtime monitoring whilst keeping your existing data logger for remote configuration and SolisCloud.

See the [Wiki](https://github.com/bretmac/halixon-solis-modbus/wiki) and take part in the [Discussions](https://github.com/bretmac/halixon-solis-modbus/discussions).  Your feedback is appreciated.

![image](https://github.com/bretmac/halixon-solis-modbus/assets/44399243/86cea2ff-dac8-430c-b084-92027842754d)

## Why the HAL-100?

There are numerous Solis Data Logger projects out there, so why choose the HAL-100?

Here are a few key features to whet your appetite:

- It's a single board solution.  No fragile connections.  No masses of wires.  Plug in a data cable, a Micro USB Power Supply and that's it.  Really.

- The prototype PCB is tiny:
  
![PXL_20230827_132815711](https://github.com/bretmac/halixon-solis-modbus/assets/44399243/e72f43f9-5c7e-43f8-82d5-1380596a6228)

It has to grow a little larger, of course, in order to accomodate holes for mounting into an enclosure, for example.  However, the board pictured above is a fully functional prototype (*see Features and Roadmap) and can be used as-is.

- The HAL-100 aims to be simple to install, setup and configure.

- It is tested!  Development has had a strong focus on unit testing.

- It is low power.   The device only consumes around 1W of power.

- You choose the data polling interval.  Say goodbye to the SolisCloud **five minute** updates.  The prototype is sending sensor data every five **seconds**.

- Automatic Inverter time setting.  Never set your inverter time again!

- Seemlessly works with SolisCloud and Solis logger, if you wish.

- Sends JSON sensor data to Home Assistant via its MQTT Broker.

- Any potential Cloud security issues disappear - you can enjoy local telemety without exposing your system to the internet.

- Over-the-Air firmware updates.  No need to reflash with your computer.

 
## Features and Roadmap


Feature|Description|Status
---|---|---
Configuration|The device provides a responsive Single Page Web Application written in React for device configuration.|Planned.<br><br>Proof of concept completed.<br><br>Required for V1.0
Initial Setup|Upon first boot, factory reset, or pressing the configuration button within 10 seconds of startup the device will configure itself as an Access Point.  You can then connect with your phone or PC to use the web configurator.|Planned.<br><br>Proof of concept completed.<br><br>Required for V1.0
Modbus Client Interface|
Modbus Server Interface|
Modbus Switch|The modbus switch allows multiple clients to access the server-side modbus.  This allows, for example, an S3 Wi-Fi stick to access the inverter and also the internal firmware to access the inverter.|Completed
Modbus Filter V1|The S3 data logger requires a lot of modbus time every five minutes as it scans for server IDs 1 thru 10.  This causes an unwanted blocking effect on the internal logger.  This component filters out invalid requests and requests for server IDs not equal to one.|  This component requires the configuration interface, but is otherwise complete.
Inverter Time Setter|The device synchrises its time from an internet time server.  Inverter time drift is checked and corrected as required.|90% Complete.<br><br>Required Configuration component to specify time server and time zone.<br><br>Requires further logic to detect transition to and from Daylight Savings Time to correct the inverter's time straight away.
Sensor MQTT Output
Client Eavesdropper
Diagnostics MQTT Output|
Over-the-Air Firmware Updates|The device retrieves new firmware versions from an internet server.|Proof of concept complete.<br><br>Requires Configuration front-end.<br><br>Required for V1.0
MQTT Autodiscovery|Autoconfigure Sensors in Home Assistant|Planned for V2.0
Backup Wi-Fi|If Wi-Fi #1 fails connect to Wi-Fi #2|Planned for V2.0
Modbus TCP Server|Allow clients to sent commands to the server bus via Modbus TCP|Needs some research.  This would be a great feature to allow inverter configuration.

## Some Home Assistant Dashboards

![image](https://github.com/bretmac/halixon-solis-modbus/assets/44399243/88bc1e2e-1869-4257-a952-f50e442fe143)

![image](https://github.com/bretmac/halixon-solis-modbus/assets/44399243/40d064ba-f5d9-4137-9d57-fc75ebe5cbee)

![image](https://github.com/bretmac/halixon-solis-modbus/assets/44399243/f13c9e1e-b10f-4937-84f1-ec0e4db0a6b9)

![image](https://github.com/bretmac/halixon-solis-modbus/assets/44399243/999cf053-e936-4011-abbc-5887a81cffcd)

![image](https://github.com/bretmac/halixon-solis-modbus/assets/44399243/44ea2ccc-f743-4f4e-be24-03ad1a887011)


The logger itself has a rich set of diagnostics data:

![image](https://github.com/bretmac/halixon-solis-modbus/assets/44399243/3e173829-5933-4615-9041-bc07f55b4fda)

