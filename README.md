# GT911 DTS for RPi
## This is a Device Tree (DT) overlay for Goodix GT911 touch controllers connected to Raspberry Pi via I2C on GPIO pins. It was tested on Raspberry Pi 3 Model B

To use it, download the `.dts` file below or create one yourself and store it somewhere where you can find it. 
From the same directory run the following command to compile it:
```sh
sudo dtc -I dts -O dtb -o /boot/firmware/overlays/gt911.dtbo gt911_overlay.dts
```
This will compile the `gt911_overlay.dts` file into `gt911.dtbo` and store it under _/boot/firmware/overlays_.

Next you need to enable it in the _/boot/firmware/config.txt_ file using the following:
```sh
dtoverlay=gt9110
```
** Also do not forget to enable the I2C interface on your board:
```sh
dtparam=i2c_arm=on
```

## Pinout Table

This is how the pins are currently connected:

| Pin | GT911 | RPi GPIO | Pin |
| --- | ----- | -------- | --- | 
| 1  | SDA | GPIO 2   | 3  |
| 2  | SCL | GPIO 3   | 5  |
| 3  | RST | GPIO 23  | 16 |
| 4  | INT | GPIO 16  | 36 |
| 5  | VDD | 3V3      | 1  |
| 6  | GND | Ground   | 9  |


---
For more information about Device Trees, visit here:
https://www.raspberrypi.org/documentation/configuration/device-tree.md 

For a quick guide to all DT overlays used in Raspberry Pi, visit below:
https://github.com/raspberrypi/firmware/blob/master/boot/overlays/README
