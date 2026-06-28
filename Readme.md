### ZTop ZT9101 vendor wireless driver, powertable modded...

## Disclaimer: I am not liable for anything that might result in issues related to the usage of this driver. Use at your own discretion

# Vanilla driver by: https://github.com/yjun123/ZT9101_vendor_linux_driver (uses ASU dns kinda slow) 

# This driver has been adopted for Linux kernel version 6.19, but it has not been tested yet.
Currently working: linux-headers-6.17.0-20-generic/   linux-hwe-6.17-headers-6.17.0-20/                                   
linux-headers-6.17.0-35-generic/   linux-hwe-6.17-headers-6.17.0-35/  (
ubuntu 24 lts
20 meter coverage(working range ~12m with 3 to 6 walls)

# requirements -
#               gcc13 (install this first), make, 
#               run:   sudo apt install -y git dkms build-essential linux-headers-$(uname -r)
#               * if still not working:
#                   sudo add-apt-repository ppa:kelebek333/kablosuz           
#                   sudo apt update                                                          
#                   sudo apt install rtl8812au-dkms
#                   a file should open afterwards choose your config settings but keep the blacklisted driver commented 
#
## changes:
#    prefered net rate ars_policy,(takes some time to adjust but best within 8 meter distance)
#    default dns resolver = 1.0.0.1 udhcp in script folder
#    powertables (binaries are encypted but there has been some improvement)
#    default Country Code = GL(GLOBAL?) from 12(CN) . grep -rn 0x58 should show 0x58 =CN or (similar) if not try 0x03), unzoned power table may have been removed
#    operating channel (use a wifi analyser to find the best one for your situation) (channel 1, and 6 are usually a golden rule @ BW40)
#    Notes.txt a rundown of changes available in wifi.cfg 
#
#
#          

               
## usage: install for current login session:
#          sudo insmod ./zt9101_ztopmac_usb.ko cfg=./wifi.cfg (for autoinstall on login gpt it but make sure it waits for a full login session and awaits user input from terminal, there are ways to bypass but boot times change and bugs ofc)
#       unload driver:
#          sudo rmmod zt9101_ztopmac_usb.ko
