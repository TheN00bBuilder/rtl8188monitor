# Realtek RTL8188CUS Monitor Mode Instructions

This will allow you to use your Realtek RTL8188CUS (common wireless chip
found in Edimax EDW-7811Un) in monitor mode _without_ recompiling the kernel.


### Install

1. Check the directory with the RTL8192CU drivers in them by typing `sudo ls /lib/modules/$(uname -r)/kernel/drivers/net/wireless/realtek.`
  * If it returns with an error or cannot find the driver (and it shouldn't), you will need to install the drivers that I have put on GitHub. Please see my profile for the repository.


2. Type `sudo modprobe rtl8192cu` to turn on the correct drivers, in case it is using the wrong ones.


3. Type the command `ifconfig` to list your wireless adaptors. 
  * Note which `wlan` the Realtek adaptor is on. 


4. Type `sudo iw $WLAN interface add mon0 type monitor` (where `$WLAN is the interface from the previous step) to add a monitor mode function to the adaptor. 
  * Don't type the pahrenthesis.


5. Try to start the monitor mode through `airmon-ng` with the command `sudo airmon-ng start (wlan of Realtek adaptor)`.
  * If it fails with `Error setting channel: command failed: Device or resource busy (-16)`, then run `sudo airmon-ng check kill` and try again.


That's it! Your RTL8188CUS should now work in monitor mode. 
