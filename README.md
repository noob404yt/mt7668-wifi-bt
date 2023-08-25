# MT7668 WiFi & Bluetooth Drivers for Linux
WiFi &amp; Bluetooth Drivers for MT7668, found on certain models (Baikal, Belize) of PS4 Pro (7215/6) and some Android boxes. This repository along with the tutorial for building will help you setup and use WiFi and Bluetooth on your device with the MT7668 chipset. This code has been confirmed working with kernel 5.4.213 on PS4 (Baikal). But, this should work without further modifications on other 5.4.x kernels, though 5.15.x kernels for PS4 might require some change.

## Disclaimer
This is based on already existing work. Proper credits for the same have already been provided at the bottom of this page.

## How to build WiFi and Bluetooth drivers for MT7668
This is a concise tutorial. For a detailed tutorial, visit my [detailed article](https://ps4linux.com/mt7668-wifi-bluetooth-drivers-linux-compile/).

1. Build kernel-headers and image files with original kernel source. Leave `CONFIG_LOCALVERSION` empty.
2. Install them on your development distro.
3. Clone this git - `git clone https://github.com/noob404yt/mt7668-wifi-bt`.
4. Open the file - *MT7668-WiFi/Makefile.x86* and replace `kernel_version` with the corresponding folder's name, eg.- `5.4.213+`. Similarly, edit *MT7668-Bluetooth/Makefile*.
5. Open a terminal in the folder *MT7668-WiFi* and run `make EXTRA_CFLAGS="-w" CROSS_COMPILE= -f Makefile.x86`. Once complete, find the module - *wlan_mt76x8.ko* in *MT7668-WiFi/drv_wlan/MT6332/wlan*.
6. Open a terminal in the folder *MT7668-Bluetooth* and run `make`. Once complete, find the module - *bt_mt7668.ko* in *MT7668-Bluetooth*.
7. On the target system, copy everything in the folder *MT7668-WiFi/7668_firmware* to */usr/lib/firmware*. Them, install the kernel-headers and image. Load the module as you wish on your target system.

## Future of the project
This repo may be used to build driver modules. But, with a little more work, I believe this can be incorporated within the kernel, to load as a driver automatically than a module. I haven't had the time to look into it. But, with many other devs in the PS4 scene looking into it already, I am sure something along the lines is close. 

## Thanks to
1. *novice4321* (Sponsored the driver port to PS4)
2. *Reo Au In* (Helped in testing and has helped sponsor projects from the beginning)
3. [Khadas's Repo](https://github.com/khadas/android_hardware_wifi_mtk_drivers_mt7668/tree/Nougat)
4. Many others (will update as and when I remember)
