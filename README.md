# CameraLED
Pure python library to control Camera LED for RaspberryPi 3  
It is compatible with both python2 and python3  

# Background
I bought an [ArduCAM](http://www.arducam.com/) with motorized IR Cut Filter.  
The IR Cur filter is connected to the camera LED, so by controlling the LED you can control the IR filter.  
They provide a [precompiled library](http://www.arducam.com/downloads/modules/RaspberryPi_camera/piCamLed.zip) to control the LED but it wasn't working for me.  
So i decided to write my own pure python library to control the camera LED (and IR filter) on Raspberry 3.  
My library does exactly what their precompiled library does.  

# Prerequisites
You have to disable the automatic management of camera led in `/boot/config.txt`.  
```bash
$ sudo echo "disable_camera_led=1" >> /boot/config.txt
$ sudo reboot
```
# Installation
```bash
$ wget https://raw.githubusercontent.com/BigNerd95/CameraLED/master/CameraLED.py 
$ chmod 755 CameraLED.py
```

# Usage
You need to be root (or at least be able to use sudo).
### Standalone
You can use my library as a standalone command:
```bash
$ sudo ./CameraLED.py 
Usage: ./CameraLED.py (state|toggle|on|off)

$ sudo ./CameraLED.py state
State: 0

$ sudo ./CameraLED.py toggle
State: 1

$ sudo ./CameraLED.py toggle
State: 0

$ sudo ./CameraLED.py on    
State: 1

$ sudo ./CameraLED.py off
State: 0
```
### Python library
You can use my library in your Camera projects
```python
from CameraLED import CameraLED
led = CameraLED() # CameraLED(134)
led.on()
led.off()
led.toggle()
led.state()
```

# Photos
LED OFF = NO IR filter = Night vision  
![image](doc/led_off.jpg)  
LED ON = IR filter = Daily vision  
![image](doc/led_on.jpg)  
