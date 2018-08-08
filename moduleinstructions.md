# Realtek RTL8188CUS Monitor Mode Instructions

This will allow you to use your Realtek RTL8188CUS (common wireless chip
found in Edimax EDW-7811Un) in monitor mode _without_ recompiling the kernel.


###Install.

1. In a blank terminal, type `uname -a' and note the kernel version.
..*Make sure to write it down, you will need it in the next step.

2. `cat` the directory with the RTL8192CU drivers in them by typing `sudo cat /lib/modules/_Kernel Version_/kernel/drivers/net/wireless/realtek.`
..*You should get something like `cat: /dir: Is a directory.`
...*If it returns with an error or cannot find the driver(and it shouldn't), you will need to install the drivers that I have put on GitHub. Please see my profile for the repository.

3. Type the command `ifconfig` to list your wireless adaptors. 
..*Note which `wlan` the Realtek adaptor is on. 

4. Type `sudo modprobe rtl8192cu` to turn on the correct drivers, in case it is using the wrong ones.

5. Type `sudo iw (wlan of Realtek adaptor) interface add mon0 type monitor` to add a monitor mode function to the adaptor. 
..*Don't type the pahrenthesis.

6. Try to start the monitor mode through `airmon-ng` with the command `sudo airmon-ng start (wlan of Realtek adaptor)`.
..*If it fails with `Error setting channel: command failed: Device or resource busy (-16)`, then run `sudo airmon-ng check kill` and try again.

That's it! Your RTL8188CUS should now work in monitor mode. 



 