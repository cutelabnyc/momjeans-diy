# Programming

The Mom Jeans DIY kit should come with a pre-programmed board, and so you shouldn't need to program it yourself. However, we provide the firmware binary here, in case you want to reprogram Mom Jeans yourself. If we release a firmware update, you can also use this same method to put the latest firmware code on your module.

1. Mom Jeans is powered from the middle PCB, but the rear PCB has the STM32 chip that runs the firmware. This means that the two boards must be coonnected together for the STM32 to receive power. It's probably easiest to start with a fully assembled kit, but you will at least need to solder the 2x5 header and the two pairs of interconnects.
2. Connect the rear PCB to the middle PCB using the two interconnects.
3. Hold down the small button on the corner of the rear PCB labeled BOOT, and connect Mom Jeans to Eurorack power using the 2x5 connector. If you don't have small fingers, it might help to use a small tool.
4. Connect Mom Jeans to your computer using the USB C connection. 
5. If your computer asks you to allow the connection, click "Allow".
6. Make sure you have the `dfu-util` command line utility installed. 
7. From this directory, run the following command:

```
dfu-util -a 0 -s 0x08000000:leave -D mom-jeans-stm32h723vet6.bin
```

8. You should see command line output like the following. You can ignore the error and warnings.

```
 dfu-util -a 0 -s 0x08000000:leave -D mom-jeans-stm32h723vet6.bin
dfu-util 0.11

Copyright 2005-2009 Weston Schmidt, Harald Welte and OpenMoko Inc.
Copyright 2010-2021 Tormod Volden and Stefan Schmidt
This program is Free Software and has ABSOLUTELY NO WARRANTY
Please report bugs to http://sourceforge.net/p/dfu-util/tickets/

dfu-util: Warning: Invalid DFU suffix signature
dfu-util: A valid DFU suffix will be required in a future dfu-util release
Opening DFU capable USB device...
Device ID 0483:df11
Device DFU version 011a
Claiming USB DFU Interface...
Setting Alternate Interface #0 ...
Determining device status...
DFU state(2) = dfuIDLE, status(0) = No error condition is present
DFU mode device DFU version 011a
Device returned transfer size 1024
DfuSe interface name: "Internal Flash   "
Downloading element to address = 0x08000000, size = 58200
Erase   	[=========================] 100%        58200 bytes
Erase    done.
Download	[=========================] 100%        58200 bytes
Download done.
File downloaded successfully
Submitting leave request...
dfu-util: Error during download get_status
```

