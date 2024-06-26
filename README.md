# prusa_mk25s_bear_klipper_config
This repository contains a customized klipper configuration for klipper for mk2.5s with ramps board

# Install

Clone this config with command git clone https://github.com/Paliddo86/prusa_mk25s_bear_klipper_config ~/printer_data/klipper-mk25sk
If you are adding this configuration after installing Klipper via KIAUH, the directory might be different - typically following ~/[printer_name]/printer_data/config, where [printer_name] is the name you selected during the Kiauh installation

# Moonraker config
Add the following to the to moonraker.conf to enable automatic updates
```
[update_manager mk25sk]
type: git_repo
origin: https://github.com/Paliddo86/prusa_mk25s_bear_klipper_config.git
path: ~/printer_data/config/klipper-mk25sk
primary_branch: master
is_system_service: False
managed_services: klipper
```
Copy https://github.com/Paliddo86/prusa_mk25s_bear_klipper_config/printer.template.cfg to printer.cfg in your klipper config  
Adjust config to your hardware  
Flash Klipper to your printer https://www.klipper3d.org/Installation.html#building-and-flashing-the-micro-controller  
You will still need a USB cable as you cannot flash via an internal serial port. You can also use any other computer to compile your firmware.  

To use this config, the firmware should be compiled for the AVR atmega2560.  
To use via serial, in "make menuconfig" select "Enable extra low-level configuration options" and back without select anything.

Launch the following command for get the current id of the serial connected and use it for flash device
```
ls /dev/serial/by-id/*
```
To flash:
```
make flash FLASH_DEVICE=/dev/serial/by-id/[serial address founded]
```
# OrangePi Zero Plus Uart Configuration
If you want to connect Arduino Mega / ramps with the serial connection and reserve the USB port for use a webcam enable with the command:
armbian-config in system setting the uart 1, reboot the orangepi and use the ttyS1 on printer configuration of klipper.

Happy Print!!!
