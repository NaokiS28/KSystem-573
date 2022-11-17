# GN845-PWB(B) - Stage IO
This PCB is also known as the Stage IO board. It lives in either the top right or top left corner of the stage pads in Dance Dance Revolution/Dancing Stage and serves as a multiplexor and driver board for the stage neons. It's only used in DDR doubles cabs, DDR Solo does not use a multiplexor as it only uses two sensors per pad (vs DDR doubles' 4) and directly connects all sensors to the JAMMA connector. The JAMMA stick UDLR pins are connected to the Stage IO board, with U and R serving as inputs for the multiplexor data as well during boot and diagnostics.

Curiosly, the Stage IO is only ever populated for 4 arrows but an entire 5th section is on the PCB and routed out, so maybe DDR might have been a 5 panel game? This was before Pump-It-Up was released so it's interesting that perhaps the center panel might have originally been an input.

Power wise, the board receives a 12V input which is then connected to a 7805 to get local 5V regulated power.

## Function
The Stage IO is not exactly required in the sense that normal gameplay in DDR does not use nor care for the multiplexing of the Stage IO, it uses the direct JAMMA stick inputs for the arrows. That said the game *does* clock the Stage IO's serial bus during gameplay but it's not fully known why as grounding one of the pins (todo: which?) will enable the pad output anyway.

### Arrow Sections
Each arrow has it's own NPN darlington pair transistor, 74HC14 inverter and passives. The transistor is used for the neon drivers that light up the arrow panel. All sensors and the NPN transistor go through the logic inverter and then into the CPLD.

### CPLD
The CPLD has pullups on it's inputs after line filters (10nf LCL filters) that go through a resistor network. The inputs are also protected by a zener diode arrays to ground and to power. The outputs are protected by opto-isolators, the same PC817 chips that Konami used everywhere else.

The CPLD itself is not yet fully understood. It's known that all Stage IOs use a synchronous serial bus over 4 wires, two of which are inputs and driven by the System 573's opto-isolated outputs on the analogue or digital IO board. The other two lines share the U and R pins with the JAMMA connector. 

The serial protocol is **ludicrously slow**, it takes about 200ms(!) to transmit a complete message. The bus is full-duplex, like SPI, the 573 will receive data as it is being sent. The first packet is a mirror of what the 573 sends, the latter half has all of the sensor data (4x4 so 16 sensors) and the 573 can optionally disable individual sensors from use, probably to avoid a stuck input but this isn't used in gameplay.

The protocol will be documented here when it is more fully understood.