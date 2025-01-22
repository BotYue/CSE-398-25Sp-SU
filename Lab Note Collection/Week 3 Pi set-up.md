# Week 3: Pi set-up

---------------
#### :dizzy: **Lab Date :** Jan 27, 29  
#### :alarm_clock: **Due Date :** 2:00 pm Feb 3   
#### :pencil2: Every group member must be present for every check point.
-------------------

## Task List

------------------
## 1. Preparation
- [ ] **Unpack your Pi 5**

- [ ] **Install Pi cooling fan**  
  search YouTube videos to check how to install
  
## 2. Set MicroSD card 
- [ ] **Image Raspberry Pi OS into microSD card**
<br>Follow the official guide:<br>
https://www.raspberrypi.com/documentation/computers/getting-started.html#installing-the-operating-system 
<br><br>You need to use your own laptop to image. The lab desktop has no admin authorization.
<br><br>Our lab micrcSD card, Samsung EVO Select 128 GB, is in fast speed. It won't take too much time to install.

    <img src="Pic/pi install.png" width="600"/>


- [ ] **Insert MicroSD card into the slot of your Pi**

## 3. Connect and Start your Pi 
- [ ] **Connect mouse, keyboard**
  <br>Connect them to the slow USB ports (USB 2.0). <br>
  Leave fast USB ports (USB 3.0) later for camera, microphone, ...

- [ ] **Connect monitor**
  <br>use the HDMI port on the desk Monitor. <br>Keep the VGA still connected to the desktop.

- [ ] **Connect power adapter**

- [ ] **Power on your Pi and finish use name/password set up**
  <br>Every group member must save a copy of your username/password

- [ ] **Connect the iot Wifi**
  <br>Wifi password is provided on Blackboard > Lab Info folder

🎉 **Check Point 1**
<br>Show lab staff once you successfully enter the Desktop screen of the Pi.

## 4. Check Software in your Pi 
- [ ] **Install Pi-Apps**
<br>You can consider Pi-Apps as something like Play Store in Android or App Store in IOS.
<br>It offers a sets of software that can be easily installed.
<br>follow the command line at this link to install Pi-Apps:
<br> https://pi-apps.io/install/ 

- [ ] **Install any Markdown software**
<br>Obsidian is default offered in Pi-Apps.
<br>It can be installed without command line.  
<br>You can also install Typora or something else.

:pushpin: Start from now, every thing you conduct need to be recorded in your Markdown.

## 5. Check Terminal 
- [ ] **Pinout**
<br>When working in hardware connection, one very useful command line is
```shell
pinout
```
  <img src="Pic/shell pinout.png" width="600"/>
  
- [ ] **config.txt**
<br>Read thru https://www.raspberrypi.com/documentation/computers/config_txt.html
<br>In the terminal, check your Pi's core temperature and power supply voltage.


🎉 **Check Point 2**
<br>Show lab staff the output in the terminal. And Briefly explain it.

## 6. Check Python
- [ ] **Open Python Editor**
<br>Python is default installed in Pi OS.  
<br>Code editor "Thonny" is also default installed in Pi OS.  
<br>You may also install other code editor such as VS Code (in Pi-Apps) if you prefer.

- [ ] **Write simple Python code**
  Write a simple Python code in the editor to meet requirements:
  - [ ] Use shebang (Unix) format
  - [ ] Prints the storage size and IP address of your Pi 5

  Then execute the code in the terminal.  


🎉 **Check Point 3**
<br>Show lab staff the output in the terminal. And Briefly explain your code.

🎉 **Check Point 4**
<br>Show your Markdown record to lab staff..


---
