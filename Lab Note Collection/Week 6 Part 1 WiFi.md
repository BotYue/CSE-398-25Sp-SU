# Week 6: Part 1 - WiFi

---------------
#### :dizzy: **Lab Date :** Feb 17, 19 
#### :alarm_clock: **Due Date :** 2:00 pm Feb 24   
#### :pencil: Every group member must be present for every check point.
-------------------

## Task List

------------------
## 1. HTTP server

**Task Overview: you will set-up a static file host in your Pi via Wifi**

- [ ] **Get your laptop and Pi both connected to the iot_lab WiFi**

In your laptop and Pi, use Terminal (Shell) commands to get IP addresses of both devices.

- [ ] **A folder to host files**

In your Pi, create a folder. Places some files into the folder, such as documents, pictures, videos.

In the Pi terminal

```shell
cd /path/to/your/folder
python3 -m http.server 8000
```

- [ ] **Access files from your laptop**

In your laptop, open a browser, enter such address

```
http://<your_pi_ip>:8080
```

You should be able to access and download files from the folder.

Observe what happened on the Pi Terminal at the same time.

After playing for a while, stop the http server in your Pi Terminal.



## 2. `socket` — Low-level networking interface
**Task Overview: Use ```socket```  to realize a file transfer system via WiFi. The file transfer is single-device-to-single-device**

```socket```  is already in the Pi's Python. It is a low-level tool and can realize simple client-server communication.

- [ ] **Design a file transfer system based on following requirements**
  - [ ] The only networking interface package used is ```import socket``` 
  - [ ] The file transfer system shall handle any file type.
  - [ ] Your Pi shall act as a server. Pi firstly specify a file to be transferred. Then Pi continuously listens for incoming connections from possible client.
  - [ ] Your laptop shall act as a client. It knows the IP of the server. It receives the file from the Pi. The received file keeps its original name and content.
  - [ ] Before establishing connection, the client should have no prior knowledge of the file name.

🎉 **Check Point 1**



## 3. `ZeroMQ` — High-level networking interface 
**Task Overview: Work with other groups, use ```ZeroMQ```  to realize a message broadcasting system via WiFi. The message broadcasting is single-device-to-many-device**

```ZeroMQ```  is a high-level networking interface. It can easily configure many-to-many communication. It has multiple communication modes: PUB/SUB, REQ/REP, PUSH/PULL, ...

Pi OS doesn't have ```ZeroMQ```. You need to install this package:

```shell
cao@raspberrypiCao:~ $ sudo apt install -y libzmq3-dev
```

```shell
cao@raspberrypiCao:~ $ pip3 install pyzmq --break-system-packages
```

Then go to your Python, check with a simple script
```python
import zmq
print(zmq.__version__)
```
- [ ] **Design a message broadcasting system based on following requirements**
  - [ ] The only networking interface package used is ```import zmq``` 
  - [ ] Use the PUB/SUB (Publisher/Subscriber) communication in ZeroMQ
  - [ ] Make arrangement with other groups. 2 Groups act as Publishers, 5 other groups act as Subscribers. 
  - [ ] Publishers connect Pi with DHT11 Sensor.  https://www.amazon.com/dp/B01DKC2GQ0 . The Publisher broadcasts their "Station ID: 1/2 " and "Environment Info: " every 10 seconds.
  - [ ] Subscribers receive message from one of the Publisher (Station 1 or 2).  Subscribers display the info on their OLED screen.

🎉 **Check Point 2**



---
