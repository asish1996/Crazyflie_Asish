# Crazyflie_Asish
This helps you in setting up enivronment for using crazyflie.

## Acknowledgements
This repository is built on top of Peter Jan's work. https://github.com/Peter-Jan/crazyflie_ws He helped Mark setup for his class in 2017. Also this takes reference from Kim Brian's work.

## Procedure

1. Install Ubuntu 16.04
Please ignore this if Ubuntu is already available on your PC

  https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop-1604#0

2. Clone Peter's repo
Peter Jan was previously a TA for the ACSI course. The repository contains Crazyflie firmware, Optitrack python code, along with other things
```
git clone https://github.com/Peter-Jan/crazyflie_ws.git
```
Now go to the the driectory and install all the required files according to the following steps
```
cd crazyflie_ws
./install2.sh
```
In case if anything doesn't work as expected, please try visiting following repositroy which has detailed steps for manual installation of required files.

https://github.com/briankim13/crazyflie_bk/blob/master/README.md

3. Working with Udev
  You need to be a member of udev group. Following sets udev permissions on Linux to use for USB radio without being root.
  ```
  cd ~
  sudo groupadd plugdev
  ```
  Now you need to write permissions to udev. Go to the directory
  ```
  cd /etc/udev/rules.d
  ```
  An appropriate app is required to write rules to a file. Leafpad is one such editor. For downloading it using following command in another terminal.
```
sudo apt-get install leafpad
```
In previous terminal, now type
```
sudo leafpad 99-crazyradio.rules
```
In the editor please paste
```
SUBSYSTEM=="usb", ATTRS{idVendor}=="1915", ATTRS{idProduct}=="7777", MODE="0664", GROUP="plugdev"
SUBSYSTEM=="usb", ATTRS{idVendor}=="0483", ATTRS{idProduct}=="5740", MODE="0664", GROUP="plugdev"
```
Save and close the editor. In case needed please visit the reference: https://github.com/bitcraze/crazyflie-lib-python#setting-udev-permissions

## Testing the crazyflie

Open a new terminal. "Hello World!" Let's fly the drone using Xbox controller. This would be a good way to check if everything is working fine. Connect Crazyradio PA to your computer and open terminal.
```
cd crazyflie_ws
roscore
```
Now run
```
roslaunch crazyflie_demo teleop_xbox360.launch
```



      
