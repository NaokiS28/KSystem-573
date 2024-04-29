# Konami 573 Digital Audio I/O Board (GX894)

This is the IO board that is mostly used with Bemani rhythm games. It uses a SPARTAN FPGA, Xilinx XC9536 CPLD and MAS3507D MP3 audio decoder IC withh a bunch of RAM, opto-isolators and trasceivers thrown in for good measure. The board is practically useless without an FPGA binary blob uploaded to it as nothing is accessible otherwise. This is uploaded by the game at the game's boot (and will show "Digital I/O init failure" if it can't.).

There's a dual RS232 port on the board but it seeminly went unused. There's also I2S audio output so it would be possible to capture the digital audio from the cab (and from the mainboard too) and convert to SPDIF or TOSLINK.

FWIW, the FPGA Blob that Konami uses is stored in 128k of SRAM and has a decryption engine built in that feeds data to the MAS chip, so you would need to encrypt any audio to be played back to use Konami's blob. Otherwise you could create a alternate blob that didn't require this and just use MP3 data stored in the 12 megabytes (!) of EDO RAM on the board.

There is Konami's multidrop networking bus and interface present on the board but more needs to be understood about this before it can be documented fully.