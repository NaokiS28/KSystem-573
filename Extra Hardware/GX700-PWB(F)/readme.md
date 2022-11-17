# GX700-PWB(F) - Analogue IO
This PCB is also known as the analogue IO board. Really speaking, it's just a 30 output driver board and has nothing to do with analogue data or audio. Given the code name, it was possibly designed at the same time the System 573 was (as the mainboard is labelled GX700-PWB(A-C)) so is not DDR specific, and has been used on other games like Fighting/Punch Mania.

It consists of a 16V8 PAL, 1x 74LS245 for converting the 3.3v PSX bus to 5v and 3x 74LS273s and a 74LS175 acting as output latches. It has a very basic function, you write a byte to a corrosponding point in memory and it gets latched to the outputs. (todo: add locations).

The logic chips drive PC817 opto-isolators which are protected by capacitors (10nf) and line filters (10nf LCL).

The PAL is not yet dumped, but on my todo list.

## Part Population
The IO board is almost never fully populated and most games will only have the output drivers populated for the outputs it needs.