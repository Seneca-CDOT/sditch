# sditch
sditch - (micro)SD (sw)itch - microSD card mux control script

This is a script designed to run on a linux computer to control
a microSD card MUX, switching a microSD card between a USB card
reader/writer and a single-board computer (such as a 96Boards 
device, Raspberry Pi, or similar). This allows the microSD card
to be (re)imaged or copied, and the SBC to be booted from that
card, without physical access -- good for automated testing (and
remote access during a pandemic!)

