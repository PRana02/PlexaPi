# USB-Microphone
## Based on Microphones


## Table of Contents
1. [Introduction](#introduction)
2. [Bill of Materials/Budget](#bill-of-materialsbudget)
3. [Time Commitment](#time-commitment)
4. [Mechanical Assembly](#mechanical-assembly)
5. [Soldering](#soldering)
6. [Power up](#power-up)
7. [Unit Testing](#unit-testing)
8. [Production Testing](#production-testing)
9. [Is it Reproducible?](#reproducible)


### Introduction

Welcome to the introduction part of my Project i.e. USB-Microphone(Alexa-Skills Based).USB-Microphone is basically a microphone that we plug into the raspberry pi and it is being used for the Voice Recognition. 

The motive of this project is to replicate the skills of Alexa and make a device that reads your audio and give feedback accordingly. I have added speakers to my Project materials as we want the audible and clear feedback. This Project provides step-by-step instructions for setting up AVS on a Raspberry Pi. It also demonstrates how to access and test AVS using Java sample app (running on a Raspberry Pi), a Node.js server, and a third-party wake word engine. You will use the Node.js server to obtain a Login with Amazon (LWA) authorization code by visiting a website using your Raspberry Pi's web browser.

For extra credit, I have posted the link below on how to connect Raspberry PI to LAPTOP using Ethernet cable, eliminating the need for a monitor, keyboard and mouse.
* [Remote Connection](https://www.youtube.com/watch?v=AJ7skYS5bjI)

#### System Diagram

![System Diagram](https://github.com/PRana02/USB-Microphone-Alexa-Skills-Based-/blob/master/system%20diagram%20alexa.jpg)


### Bill of Materials/Budget
The materials required to build the USB-Microphone are Raspberry Pi 3, SunFounder USB 2.0 Mini Microphone for Raspberry Pi 3 and Logitech Z130 Compact Computer Speakers.

1) Raspberry Pi 3 (CanaKit Starter Kit):

* [Amazon](https://www.amazon.ca/CanaKit-Raspberry-Complete-Starter-Kit/dp/B01CCF6V3A/ref=sr_1_2?s=electronics&ie=UTF8&qid=1516549400&sr=1-2&keywords=rapberry+pi) CAD $99.99

2) USB 2.0 Mini Microphone:
 
* [Amazon](https://www.amazon.ca/SunFounder-Microphone-Raspberry-Recognition-Software/dp/B01KLRBHGM/ref=sr_1_1?s=electronics&ie=UTF8&qid=1516549033&sr=8-1&keywords=sunfounder+usb+microphone) CAD $39.46 
* [Ebay](https://www.ebay.ca/itm/SunFounder-USB-2-0-Mini-Microphone-for-Raspberry-Pi-3-2-Module-B-RPi-1-Model/232430660307?hash=item361df26ad3:g:bYIAAOSwySFZf1pf) US $8.62

3) Logitech Z130 Compact Computer Speakers:

* [The Source](https://www.thesource.ca/en-ca/computers-and-tablets/computer-accessories/computer-speakers/logitech-z130-compact-computer-speakers/p/108008204) CAD $39.99

* Apart from above hardware, a USB Keyboard & Mouse, and an external HDMI Monitor. I also recommend having a USB keyboard and mouse as well as an HDMI monitor handy if you're unable to remote(SSH) into your Pi.
* When I was planning my budget, the prices of the materials were slightly different from the present. 

### Time Commitment
* Time to complete this project would be around 3 days if you have everything handy with the build instruction. It took me couple of weeks to complete this project.In the first week,I had to research about my project, plan my budget accordingly and wait for the items to be delivered. During that time I learned how to connect my Raspberry Pi remotely and researched about Alexa Skills provided by Amazon.

* Well, if you are free for couple of days and want to make something interesting, I would suggest you to try this and let me know if you have any questions. My email address is piyushr97@gmail.com. Feel free to contact me.

### Mechanical Assembly

* Since this Project requires no more than two components, we just have to connect them to Raspberry Pi. Below is picture of my connection.

![Connections](https://github.com/PRana02/USB-Microphone-Alexa-Skills-Based-/blob/master/Inkedproject_LI.jpg)

### Soldering
There was no soldering required with the sunlight sensor. The sunlight sensor is connected by using the Grove Cable to the connector interface on the raspberry pi.

### Power Up
Before power up the Raspberry pi, check the micro SD card to see if it has the contents of NOOBS operation system installer which contains Raspbian. If not, you can download, unzip and copy the folder contents of [NOOBS](https://downloads.raspberrypi.org/NOOBS_latest) into the root directory of the micro SD card.
On the first boot you will be prompted to install the operating system and configure the wifi setting. Once the raspberry pi is done installing the operating system. The first thing is to enable I2C because by default it is not enable. I2C bus allows the devices like the sunlight sensor to be connected and detected on to the Raspberry Pi.
To enable I2C: from the Start Menu -> Preferences -> Raspberry Pi configuration -> Interface set I2C to Enabled. 

Next on the terminal type the following command to check that you have i2c-tools utility installed.
```
sudo apt-get install -y python-smbus
sudo apt-get install -y i2c-tools
```

### Unit Testing

To check if the raspberry pi is detecting the sunlight sensor:
Open the terminal and type the command 
```
sudo i2cdetect -y 1
```

If you see this, it means that the raspberry pi is detecting the sunlight sensor and you connected the sensor to the raspberry pi correctly.

![sunlight i2c detect](https://raw.githubusercontent.com/RaphaelNajera/Sunlight_Sensor/master/documentation/Sunlight%20sensor%20i2c%20detect.png)

0x60 is the Sunlight Sensor.

The next step is to install the APscheduler. The Advanced Python Scheduler is a task scheduler that lets you schedule functions to be executed at times of your choosing.

On the terminal type the follow command to install APscheduler.
```
Sudo pip install setuptools –upgrade
Sudo pip install apscheduler
```

Next is to install the software and download the code to run the sunlight sensor
You can download the files required to run the sunlight sensor [here](https://minhaskamal.github.io/DownGit/#/home?url=https:%2F%2Fgithub.com%2FRaphaelNajera%2FSunlight_Sensor%2Ftree%2Fmaster%2Ffirmware).

Unzip the file and save it on the root directory on your raspberry pi. 

On the terminal type the following command:
```
cd firmware/Adafruit_Python_PureIO
sudo python setup.py install
```

To run the code, enter the follow command:
```
cd firmware
python SunIOT.py
```
The program will execute.


https://www.youtube.com/watch?v=ZI2hxuOw9OU&feature=youtu.be


### Production Testing:
Once the program successfully executes the output will display the Vis (visible light), IR (infrared light) and UV Index (UV-Light) from the sunlight sensor. 

Pictures of the sunlight sensor project and the code running:

![sunlight powering up](https://raw.githubusercontent.com/RaphaelNajera/Sunlight_Sensor/master/documentation/sunlight%20sensor%20powered%20up.jpg)


![sunlight sensor output](https://raw.githubusercontent.com/RaphaelNajera/Sunlight_Sensor/master/documentation/Sunlight%20sensor%20output.png)

### Reproducible?
By following this build instruction, I believe you will be able to reproduce the sunlight sensor project. I have provided in my GitHub, budget, instruction on how to build and setup the code.
