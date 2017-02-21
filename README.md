# Modification-of-keyboard-device-driver

In this project changes have been made to the Linux USB Keyboard driver(see http://lxr.free-‐‐ electrons.com/source/drivers/hid/usbhid/usbkbd.c)
to change the way the CAPSLOCK led is turned on. Normally, the CAPSLOCK led is on when that key is pressed the first time
and is turned off when it pressed again, and is on again when it is pressed the next time, and so on. 
Change has been made to the code such that when the driver is in MODE1, CAPSLOCK will be handled as usual.
However, when in MODE2, CAPSLOCK led will be off when CAPSLOCK is pressed the first time after transitioning to MODE2 
and will be on when it is pressed the next time, and so on. 

MODE2 will be activated when NUMLOCK is pressed, CAPSLOCK is not pressed, and CAPSLOCK is not on at the moment. 
When transitioning to MODE2, the CAPSLOCK led will be turned onautomatically. MODE2 will be active until NUMLOCK is
pressed again. At this point the driver leaves the CAPSLOCK led status in a way that will be compatible with MODE1,
e.g, whether the input layer thinks the CAPSLOCK is on or not.
