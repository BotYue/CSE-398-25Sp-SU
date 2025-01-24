# Week 4: GPIO and I2C

---------------
#### :dizzy: **Lab Date :**Feb 3, 5 
#### :alarm_clock: **Due Date :** 2:00 pm Feb 10   
#### :pencil: Every group member must be present for every check point.
-------------------

## Task List

------------------
## 1. GPIO - Simple LED
- [ ] **Explore command lines to check gpio info**
<br>Raspberry Pi OS defaultly installs a tool called **gpiod** 
<br>Scan thru its README markdown: https://github.com/brgl/libgpiod  and try its shell commands.
- [ ] **Simple LED in Python**
<br>In Python, you can use the **gpiod** tool by ```import gpiod```.
<br>Build a simple circuit connecting a LED, a resistor, a GPIO and GND.
<br>Write Python code using the gpiod to make the LED blinking.

🎉 **Check Point 1**

## 2. GPIO - Car Light System
- [ ] **Design a system based on following requirements**
  - [ ] **Hardware**:
    - [ ] **GPIO Inputs**: any hardware input in lab (push button/slider switch/keypad...)
    - [ ] **GPIO Outputs**: 2 LEDs to represent:
      - Left turning light.
      - Right turning light.
      - Hazard lights (both left and right blinking simultaneously).
    
  - [ ] **Software**:
    - [ ] You are free to use any extra Python libraries
    
      It is suggested using **gpiozero** , which offers some high-level interface.
    
      **gpiozero** is also default installed in Pi OS.
    
    - [ ] Your Python code needs to have object-oriented programming (OOP) concept.
      For example, create a ```class CarLightsSystem:``` and place it in a separate .py file.

🎉 **Check Point 2**

## 3. I2C - Basic set-up 
- [ ] **Hardware set-up**
  <br>You will play with a I2C based OLED display. 
  <br>It is this product:
  <br>0.96 Inch OLED I2C IIC Display Module 12864 128x64 Pixel SSD1306 Mini Self-Luminous OLED Screen 
  <br>https://www.amazon.com/dp/B09T6SJBV5?th=1 
  Connect it with your Pi using breadboard and jump wires.

- [ ] **Pi OS Configuration**
<br>You need to turn on the I2C in the Pi OS firstly.
<br>Go to your top left menu, you can find ```Preferences``` -> ```Raspberry Pi Configuration```.

- [ ] **I2C Detect**
<br>```i2cdetect``` is a tool defaultly install in Pi OS.
<br>It can quick check your I2C communication in the Terminal. 

```shell
cao@raspberrypiCao:~ $ i2cdetect -l
i2c-1	i2c       	Synopsys DesignWare I2C adapter 	I2C adapter
i2c-11	i2c       	107d508200.i2c                  	I2C adapter
i2c-12	i2c       	107d508280.i2c                  	I2C adapter
```
You should see ```i2c-1```, this is the i2c corresponding to your GPIO pins.
Then check if the device is in the correct address, 1 indicate the ```i2c-1```:
```shell
cao@raspberrypiCao:~ $ i2cdetect -y 1
```
You should see ```0x3C``` address is there.

🎉 **Check Point 3**

## 4. I2C - Design a Status Monitor 
**Overall, In the design, you need to realize a Status Monitor system:**
<br> This OLED displays the temprature of your PI and real time.

- [ ] **adafruit_ssd1306 package**
<br>To code that OLED in Python, you need to firstly install adafruit_ssd1306
```shell
cao@raspberrypiCao:~ $ pip3 install adafruit-circuitpython-ssd1306 --break-system-packages
```
- [ ] **Hello World Display**
Start from a simple one in Python - just display "Hello World" in your screen.
You can use these 2 packages for display.

```python
from PIL import Image, ImageDraw, ImageFont
import adafruit_ssd1306
```

As well as these two packages for I2C communication::
```python
import board
import busio
```
You are free to use extra packages in Python.

- [ ] **Display Real-Time Status**
Try to get the real-time status:
1. temperature of the Pi; 2. Time.

Display these info on the screen.

- [ ] **Add Emoji**
Plain text may look boring. You can add some emojis.
<br> Download Google Noto Emoji font
<br> https://fonts.google.com/noto/specimen/Noto+Emoji
<br> Un-zip and place the ```NotoEmoji-Regular.ttf``` in the same folder as your code file.
<br>You can then write emoji using Unicode and display it with PIL package on your screen.
<br>You can find the Unicode lookup here: https://www.unicode.org/charts/PDF/U1F300.pdf

```python
emoji_font_path = "NotoEmoji-Regular.ttf"  
emoji_font = ImageFont.truetype(emoji_font_path, 10)  # Adjust font size for readability

## Suppose your PIL ImageDraw object is named "draw"
draw.text((0, 15), "\U0001F319", font=emoji_font, fill=255)

```
You don't need to use the exact same emojis in the example figure..

- [ ] **Improve display**
Arrange your information and emojis for better visual appeal.
Feel free to adjust the layout as you want.
No need  to strictly follow the placement shown in the example figure.

🎉 **Check Point 4**



---
