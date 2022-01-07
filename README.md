# Install OpenCV and Realsense for RaspberryPi (32 bits)<br/>

## Setup Guidelines before installation<br/>

### EEPROM<br/>
The Raspberry Pi 4 is also partially booted from two EEPROMs. These EEPROMs are programmed after PCB assembly in the factory. <br/>
The Raspberry Pi foundation has recently released new and improved software for these EEPROMs. <br/>
This nothing to do with OpenCV, but all the more with heat dissipation. <br/>
In one of Qengineering vision applications, the heat of the CPU drops from 65 °C (149 °F) to 48 °C (118 °F) simply by updating the EEPROMs contents. <br/>
And, as you know, a low CPU temperature will prolong your Pi lifespan. For more information see this [article]( https://www.hackster.io/news/raspberry-pi-4-firmware-updates-tested-a-deep-dive-into-thermal-performance-and-optimization-2f22c78e7089 )
.<br/>
Check, and if needed update, the EEPROMs with the following commands. The screen dumps speak for there self.
- Get the current status
```
sudo rpi-eeprom-update
```
- If needed, to update the firmware
```
sudo rpi-eeprom-update -a
```
![output image]( https://qengineering.eu/images/EEPROM_9ag2gdtq.webp )

------------

### Version Check<br/>
- Do you have the 32-bit version, armv7l, please continue.
```
uname -a
```
![output image]( https://qengineering.eu/images/Version32_64.webp )

------------

### Swap Memory<br/>
The next step is to increase your swap space. OpenCV needs a lot of memory to compile. 
- Edit the swap configuration
```
sudo nano /etc/dphys-swapfile
```
Increase swap to 2GB by changing the file above to `CONF_SWAPSIZE=2048`
- Apply the change
```
sudo /etc/init.d/dphys-swapfile restart swapon -s
```

------------

### Operating System<br/>
The Raspberry Pi 4 has a 76 Mbyte GPU memory size. It can be somewhat small for vision projects, better to change this now to a 128 Mbyte. To increase the amount of memory for the GPU, use the following menu.<br/>
![output image]( https://qengineering.eu/images/Raspi_Configuration_v3xvndqr.webp )
![output image]( https://qengineering.eu/images/Raspi_Configuration_2_7eh7npud.webp )

------------

### Reboot
- Reboot to apply the changes above
```
sudo reboot
```

------------

## Installation
```
cd ~
wget https://github.com/lhkwok9/cv2_realsense/raw/main/cv2_realsense.sh
sudo chmod 755 ./cv2_realsense.sh
./cv2_realsense.sh
```

------------

OpenCV (and realsense) will be installed to the `/usr/local` directory, all files will be copied to following locations:<br/>

- `/usr/local/bin` - executable files<br/>
- `/usr/local/lib` - libraries (.so)<br/>
- `/usr/local/lib/cmake/opencv4` - cmake package<br/>
- `/usr/local/include/opencv4` - headers<br/>
- `/usr/local/share/opencv4` - other files (e.g. trained cascades in XML format)<br/>

------------

## Opencv Source: Copyright 2021 Qengineering
## Realsense Source:
### Ai_Demos_RPi

Example code for using different Raspberry Pi boards with various electronic and mechanical components in order to build fun, DIY projects!

#### Description

Most of these projects are featured in my YouTube channel:
   * https://youtube.com/acrobotic

As well as in my tutorials page:
   * https://learn.acrobotic.com

If you like my work, you can help me dedicate more time to building projects, 
writing code, and making videos about them:
   * https://patreon.com/acrobotic
   * https://paypal.me/acrobotic
   * https://buymeacoffee.com/acrobotic

You can also purchase products from my little online shops to help fund future 
Open-Source projects like these! I'll always put my best effort in every project, 
and release all my design files and code for you to use. 
   * https://acrobotic.com/
   * https://amazon.com/shops/acrobotic
