# TurleBot3ISL
Some important details for our project FSU ISL 2021 Turtle Bots  
Here is where you will find the following instructions  
:bulb: This ReadMe will be constantly updated it is important to let Sean P. and Jon S. know if any other issues arise.  
# Setting up PC
The point of this guide is to act as a companion to the guide availiable [here](https://emanual.robotis.com/docs/en/platform/turtlebot3/overview/)    
  
You will begin by choosing Ubuntu 20.04 as your OS to run ROS Noetic. This should be reserved for your personal machines and Virtual Machines. **NOT THE NANOS!** 
  
The guide gives links to multiple articles on how to do this. If you are using a Nano the guide will be linked in the Nano section of this guide. Otherwise if you are using a virtual machine [this](https://brb.nci.nih.gov/seqtools/installUbuntu.html) is a helpful article for virtualbox.

Follow all of steps 3.1 on the guide. It should not give you any issues. If any issues were to arise contact Jon S. or Sean P.  
  
:rotating_light: Make sure to follow instructions to the T do not rush and troubleshoot any errors as they could pose problems in the future  
  
# Raspberry Pi and Network
If you have made it this far your PC should have ROS Noetic installed and ready to go. From here we will fill in the gaps on setting up the Raspberry Pi's that are on the TurtleBots. You should be Starting on section 3.2 in the guide. The first important step is to select the correct Noetic Image appears under the following heading:  
  
![ROSNoeticImage](https://user-images.githubusercontent.com/91296386/139104879-df30f7f0-7dbc-43e7-9ff0-6d19c122b124.PNG)  
Follow the instruction for the rapsberry Pi Imager. This is a crucial portion be sure to follow all instructions.  
  
  
### Alternate Instructions for 3.2.6:
  
First you need to generate a basic netplan file. It's important to use the following commands as they will ensure that the correct files and directories necessary for wifi are created.  By default these files and/or directories do not exist.


```sudo netplan generate```  
  
```sudo netplan apply```  

```sudo systemctl enable wpa_supplicant && systemctl enable wpa_supplicant```  

You will need to edit the 50-cloud-init.yaml text file on your pi. This file is used to connect to the school wifi. In order to edit enter the following:
  
```sudo nano /etc/netplan/50-cloud-init.yaml ```  
  
The next part is very important. Take into account that if you are working in the ISL lab you should be using the BRONCO_STUDENT. When creating the yaml file spacing matters. everything should be typed and spaced as follows.

  
```
network:
  version: 2
  renderer: networkd
  ethernets:
    eth0:
      dhcp4: true
      optional: true
  wifis:
    wlan0:
      dhcp4: yes
      dhcp6: yes
      access-points:
        "BRONCO-STUDENT": {}
 ```
 
  
From here you should be able to continue throught the rest of the instructions without any problems.
