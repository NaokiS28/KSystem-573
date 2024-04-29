# Konami System 573 Security Carts
This folder lists the security carts that were used in the System 573. The security cart port could be considered as a GPIO bus for the 573, having an 8-bit input port, 8-bit output port, semaphore signaling, bitbanged I2C and SPI and a UART port. As a result, a lot of security cartridges tended to be dual purpose and add extra IO to the 573 without using the internal expansion bus.

There are a few types of case styles with the cartridges:
* No case - Bare PCB, sometimes covered with a seperate cover that screws into the 573's silver metal case or has a bespoke metal case covering bother the 573 and cartridge.
* Small case - Small retangular cartridge with a 45 degree angled top. Used on games that only used basic cartridges. Is the same height as the 573 when installed.
* T-Cart - A larger cartridge that extends taller than the 573 when installed and uses most of the width to the side of the cartridge. Typically used on games requiring extra IO.

## Notes:
* It seems almost all cartridges bridge the 573-RTS and 573-CTS UART port lines. If you require the serial port on the 573, just install any old cart and this is done for you.
* Like a lot of Konami parts, they are typically only populated for what the game needs. This means despite the fact that Dancing Stage EuroMIX 2 uses a GE949-PWB(D)A cartridge, none of the extra parts to support the AMP control or RS232 ports (except the RTS-CTS link) are present. DDR 3rdMIX seems to be a rare exception in this case.
* All carts a fully reprogramable to have *any* other cart data. The only exception is that carts using a Xicor EEPROM can only be used on games expecting a Xicor cart and vice versa with the PIC16C carts, also known as ZS01 carts - That said, some games might be able to use both cart types, but this is not confirmed. Dancing Stage EuroMIX has strange behavoir in that it will inform the operator to label the cart like it would on ZS01 carts, but it does not actually marry the cart.