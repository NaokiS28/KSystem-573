# GN845-PWB(A) - Relay Board
This PCB is also known as the Relay board sometimes, it is used on DDR/Dancing Stage and possibly other BEMANI games like Drummania and Guitar Freaks. 

First used with DDR, it has space for two logic inverters for up to 8 channels (altough DDR only has pats for 6 channels) of high current outputs like the 12v halogen spotlamps on the marquee and the 501 lamps in the start and select buttons. The neon tube driver *does not* go through this board, it uses a separate solid-state relay (SSR) to drive the neon transformer.

The secondary logic chip and associated components are not used or populated in DDR. It drives the last two MOSFETs/Darlington pair transistors, a space for lower current drivers using NPN transistors and then finally two opto-isolator outputs. It's not known what these were originally intended for nor if any game would have ever likely used them.

The board is setup to use both N-Channel MOSFETs and NPN Darlington pair transistors, with R9-R16 being the only components needing to be changed. A straight link (0-ohm/wire) is used for MOSFETs and a resistor for NPN Darlington transistors. The board is only designed to handle 12V swtiching. It has an onboard 7805 5V regulator for the logic ICs.