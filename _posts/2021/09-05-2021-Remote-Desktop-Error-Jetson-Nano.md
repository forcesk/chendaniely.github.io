---
layout: post
title:  "Remote Desktop Error Jetson Nano"
date:   2021-05-09

categories: Tutorials

tags:
  - Jetson Nano
  - xrdp
  - Remote Desktop
---

### Trouble
Jetson nano black screen or shutdown at the begining in remote desktop.


### This solve the problem

#### Remove the old xrdp installation
* sudo systemctl stop xrdp
* sudo apt-get remove xrdp
* sudo apt-get purge xrdp

### Install new fresh
* sudo apt install xrdp 
* sudo adduser xrdp ssl-cert  
* sudo systemctl restart xrdp

### Install Xcfe Desktop 
* sudo apt install xfce4

### Firewall Permisions
* sudo apt install ufw
* sudo ufw allow 3389
* Or in IP range (This way is more safe) - sudo ufw allow from 192.168.33.0/24 to any port 3389

### Modify startwm.sh file
* sudo nano /etc/xrdp/startwm.sh
* comment the two last lines 
* *add this* startxfce4

### Restart xrdp
* sudo service xrdp restart

that solve the problem!


