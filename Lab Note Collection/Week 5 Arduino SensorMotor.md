# Week 5: Arduino SensorMotor

---------------
#### :dizzy: **Lab Date :** Feb 10, 12 
#### :alarm_clock: **Due Date :** 2:00 pm Feb 17   
#### :pencil: Every group member must be present for every check point.
-------------------

## Task List

--------------
### **Introduction**

This week, we will integrate the IMU and servo motors with the Pi 5. While both the IMU and servo motors can be directly connected to the Pi 5, we decide to introduce an Arduino as an intermediate device. 

Using the Arduino as an intermediate has such advantages:

1. **Efficient Task Allocation:** The Arduino will handle real-time processing of IMU data and servo control. So that we can free PI to do some other heavily computational tasks.
2. **Better Timing:**  The Arduino has better timing mechanism than the Raspberry Pi, such as the ```millis()``` function for accurate time tracking.

------------------
## 1. Arduino IMU Basic
- [ ] **Get any Arduino board that is 3.3 V logic**
Connect Arduino to your own laptop
<br>Check Arduino uploading using the simplest example -- Blink

- [ ] **Set up MPU6050 IMU**
The IMU we purchased is: 
Pre-Soldered SHILLEHTEK MPU6050,
https://www.amazon.com/Pre-Soldered-Accelerometer-Raspberry-Compatible-Arduino/dp/B0BMY15TC4 
<br>The usage of this IMU is similar as the one on  the Adafruit website:
https://learn.adafruit.com/mpu6050-6-dof-accelerometer-and-gyro/overview 

- [ ] **Code the IMU**
In your Arduino IDE, code the IMU, print the sensor readings to the Serial Monitor.

Move your IMU around, see if the sensor readings are reasonble.

Here is an example I got:
```
Accelerometer (m/s^2): X=-8.67 Y=-0.67 Z=6.16
Gyroscope (°/s): X=-0.21 Y=-0.54 Z=0.45
---------------------------
Accelerometer (m/s^2): X=3.42 Y=-6.07 Z=5.14
Gyroscope (°/s): X=-2.05 Y=-3.40 Z=-2.05
---------------------------
Accelerometer (m/s^2): X=2.68 Y=-8.13 Z=-5.80
Gyroscope (°/s): X=-0.33 Y=0.79 Z=1.39
---------------------------
```
🎉 **Check Point 1**

## 2. Arduino to Pi: A Vibration Detector
- [ ] **Design a system based on following requirements**
  
  - [ ] **Hardware**:
    - [ ] IMU connected to Arduino
    - [ ] Arduino connected to Pi via USB 
    
  - [ ] **Software**:
    
    - [ ] Arduino continuously monitors the vibration level.
    - [ ] If in minimal vibration, send "OK" to the Pi.
    - [ ] If significant vibration happens, send detail sensor readings to the Pi.
    - [ ] On the Pi side, display the info on the Termination. 
    
  - [ ] **Extra Note 1**
   When sending sensor readings from Arduino to Pi, don't use multiple ```Serial.print```  or ```Serial.println```  in a main loop. 
    <br>Instead, get all sensor readings, combine them in a structed format (like a packet), then use a single ```Serial.println``` to send.
    Here is an example I did: ``<AX:0.02,AY:-9.81,AZ:0.03,GX:0.01,GY:-0.02,GZ:0.00>``
  
  You can use any other format, as far as: It is a structured format including all sensor info, and You format can be easily parsed on the Pi side.
	
  - [ ] **Extra Note 2**
  
    In terminal, you can check the name of the USB device.
  
    When coding, make sure the baud rate of your Pi and your Arduino are set as the same.
  ```shell
  ~ $ ls /dev/ttyACM*
  ```

🎉 **Check Point 2**



## 3. Arduino Servo Motor Basic 
- [ ] **Motor set-up**

  The servo motor we use is Smraza 9G Micro Servo Motor 

  The purchase link is https://www.amazon.com/dp/B07L2SF3R4?smid=AMIHZKLK542FQ&th=1 

  Each group gets 2 servo motors.

  Also screw the plastic blade to it, so that you can observe the rotating angle.

- [ ] **Power Supply set-up**


  Warning: Never use micro-controller's Pin (Arduino/Pi/...) to power up motors.

  You need to use an external Power Supply.

  You can use the dual-head screwdriver: i) one blade head to turn power supply supply; ii) the other Phillips head tighten jump-wire insertion 

- [ ] **Run the Motor**

Connect Arduino to 2 motors.

Code the Arduino. Such that you can turn 2 motors at different angles.

🎉 **Check Point 3**

## 4. Pi GUI to Control Servo Motor  
- [ ] **Design a system based on following requirements**
  
  - [ ] Users can use a GUI in **Pi** to control the movement of 2 servo motors
  - [ ] The control message is sent in this way: **Pi** ---> **Arduino** ---> **Servo Motor** 

- [ ] I played with ChatGPT 20 minutes. It gives me such GUI with the following import.

```python
from PyQt5.QtWidgets import QApplication, QWidget, QVBoxLayout, QLabel, QDial
from PyQt5.QtGui import QFont, QPainter, QColor
from PyQt5.QtCore import Qt
import sys
```

I expect your GUI is in better-looking than my simple work.

🎉 **Check Point 4**



---
