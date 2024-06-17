# tequ-iot-datalogger
Building and setup of a IoT datalogger.

## Hardware
The design features a 3D printed case, which can be found in the repository files
| Hardware               | Model            | Link           |
| -------------          |:-------------:   | :-------------:|
| Main computer          | SparkFun DataLogger IoT 9DoF   | <a href="https://www.sparkfun.com/products/20594">Link</a>|
| 4x Thermocouple amplifier          |  SparkFun Qwiic Thermocouple Amplifier    | <a href="https://www.sparkfun.com/products/16295">Link</a>|
| Battery  | 3.7V 2000mAh LiPo   | |
| 4x K-Type thermocouple receiver          |    | |
| 4x K-Type thermocouple          |    | |
| SD card          | FAT32 formatted SD Card   | |
| Optional, 2x User picked I2C devices |    | |

## Connections
Connections of the hardware used. The thermocouple amplifiers are to be connected with the Qwiic connectors to each other and to the DataLogger board. 
Remember to also insert the SD card into the devices SD card port.
| Device                        | PIN            | Device             | PIN            | 
| ----------------------------- |:--------------:| :-----------------:| :-------------:|
| SparkFun DataLogger IoT 9DoF  | 3V3 SW         | I2C_1 and I2C_2    | 3V3  |
| SparkFun DataLogger IoT 9DoF  | GND            | I2C_1 and I2C_2    | GND  |
| SparkFun DataLogger IoT 9DoF  | SDA            | I2C_1 and I2C_2    | SDA  |
| SparkFun DataLogger IoT 9DoF  | SCL            | I2C_1 and I2C_2    | SCL  |
| SparkFun DataLogger IoT 9DoF  | On-board battery connector | Battery  | Battery connector  |
| 4x Thermocouple amplifier  | +    | K-Type thermocouple receiver    | + |
| 4x Thermocouple amplifier  | -    | K-Type thermocouple receiver    | - |

## Setup

### SparkFun DataLogger configuration
Connect the DataLogger via a USB-C cable to your computer and open its corresponding serial port into a terminal. The default baud rate should be 115200.

Once open, wait for the device to load and the press any key to enter settings.
Here you should check that the firmware is up-to-date, at the time of writing the build `01.02.00 Version 1.2` is the latest. Depending on your firmware version, the following steps may differ, as they are written for the aforementioned build.

If your devices firmware is outdated, it needs to be updated. To do this, you can either install the new version via the SD Card or WiFi. We'll cover the WiFi method.

#### Updating firmware
Enter into the main settings window and from there System settings -> WiFi Network. From here enable Wifi and add a network for the device to connect to. Upon completion, exit out of the settings menu to the datalogging view. 
You should have seen a line reading `[I] Saving System Settings`, indicating that the settigns were saved successfully. If not, check that the SD card has been installed correctly and is found by the device during bootup.

Then enter back into System settings and then System Update. From here, select the Update Firmware - OTA option, after which it should automatically update the firmware.

#### Primary configuration
Once you have an updated firmware and a WiFi connection established, you can configure the rest of the system. 

1. Enter into `System Settings -> Time Setup` and modify `The Time Zone` to `EET-2EEST,M3.5.0/3,M10.5.0/4`
2. `System Settings -> Logger` and change `Timestamp Mode` to the `ISO8601 Timestamp` option
3. `System Settings -> HTTP IoT`, enable HTTP IoT and add your URL, in format: `http://ipaddress:port/exampleaddress`
4. You may also configure the connected devices to output the desired values from `Devices Settings` from the main settings window

Once completed, restart your device and check that it is working properly.
