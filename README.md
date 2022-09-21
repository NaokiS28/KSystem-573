# KSystem-573
 Schematics and pinout information for the Konami System 573
 
 **Please note a lot of this data is not 100% complete and might be incorrect in places.** Also this repository needs to be generally organised better.
 
## Schematics
 Schematics are in KiCad format and are preliminary. Currently known issues:
 * The PSX portion is not mapped out. This is the same as the regular PS1 CPU, GPU and SPU schematics with the exception of more work and GPU RAM.
 * The CPLD is mostly but not fully mapped out.
 * The security cart needs verifying and labeling correctly.
 * In general the schematics need tidying up.
 * The Konami 056789 ASIC needs a symbol creating. It's a 6x 16-Bit input and 1x 8-bit output latch really, probably has some 74 series dies on the inside.
 * IO boards are somewhat documented but in varying stages of completeness.

## PCB Layout
 The mother PCB is not laid out. The intention with this project was not to make a new repro motherboard but to define the schematics and wiring. The outline *should* be correct but it is not 100%. If you feel like creating a PCB layout, submit a PR!
 
