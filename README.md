# sditch
sditch - (micro)SD (sw)itch - microSD card mux control script

This is a script designed to run on a Raspberry Pi to control
a microSD card MUX, switching a microSD card between a USB card
reader/writer and a single-board computer (SBC such as another Raspberry
Pi or similar). This allows the microSD card
to be (re)imaged or copied, and the SBC to be booted from that
card, without physical access -- good for automated testing (and
remote access during a pandemic!)

The actual MUX hardware consists of a pair of sn74sbt3257 chips
interfaced to the control computer through GPIO lines. One GPIO
controls the !OE (not output enable, i.e., output disable) line
and the other controls the S (select) line on the mux chips.
The A inputs on the chips are connected to the microSD card
socket, and the B1/B2 outputs are connected to two microSD 
outputs (we used the SparkFun microSD card sniffers to provide
the microSD card connectors to plug into the two devices; we
may produce a single thin PCB in the future, and will publish
the board design if we do so).

The script is also designed to manage a PDU controlling the 
SBC; it's set for a Raritan PDU at this point but this can be
readily adjusted.

These are the commands accepted by the script:

*   status -         status of the microSD mux
*   muxoff -        microSD card not connected (mux off)
*   pi -            microSD card connected to Pi
*   reader -        microSD card connected to reader
*   [re]boot -      microSD card connect to Pi, Pi started
*   poweron -       ...same as boot
*   poweroff -      shutdown and poweroff the Pi
*   shutdown -      ...same as poweroff
*   read file -     microSD card contents placed in file (.gz)
*   write file -    microSD card written from file (.gz)
*   writeon file -  ...write followed by poweron
*   mount -         microSD card partitions mounted under /mnt/sd
*   serial -        start minicom for serial console monitoring
