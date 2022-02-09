# E765B1 PAL

------

The E765B1 PAL is a 16V8 PAL found on the GE765-PWB(B) IO board. It serves as an output transistor driver with a PWM like functionality. It changes where in the clock cycle the transistor will turn on an off in a 8-step cycle. It also has an auxilary output which is not used on the IO board.

There are two on the GE765-PWB(B) board, one at 10D and the other at 7B. They are used to drive the C3567 transistors (also has the part number 2SC2242 by them on the silkscreen) which drive the outputs to the reel controller. One seems to be an output for a 5V device (using the NRPS circuit breaker), the other is an output for a 12V device. They each connected to a 74LS175 Flip-Flop which are connected to D0-D4 on the expansion data bus. The 74LS175 clock pulse comes from the E765B2 PAL at 8D.

Here is the pin mapping for these PALs:

```
1: Clock input (Either 157Hz for PAL at 10D or 104khz on PAL at 7B)
2-4: PWM setting input from 0-15 (2: B2, 3: B1, 4: B0)
5: Aux output setting (High: Aux output high for 4 counts, Low: High for when counter = 0)
6-11: Ground
12-14: 3-Bit counter out (Unused, 12: B2, 13: B1, 14: B0)
15-17: N/C, Unused
18: Aux output (Not sure if this is used in main output)
19: Transistor PWM output
```

The counter is rising edge triggered and increments the counter by 1. The PAL uses a 3-bit counter for 8 steps (0-7 on output pins in BCD). The PWM input will set how long the transistor output (19) will be high for, IE a setting of B101 (5) in MSBFIRST will mean that the output is on from counter = 0 to counter = 4. The max setting is 7 and this will turn the output off for 1 count when the counter is at 7.

The auxilary output, whilst not used, will either be on for one count (counter = 0) or can be set to be at 50% duty cycle, or from counter = 0 to counter = 3. I do not know if this pin is used with the transistor output but neither pin 18 nor input 5 seem to have any effect on the transistor output.

Finally, pins 6-9 and pins 15-17 do not appear to be used for anything. The outputs are low and the inputs are tied to GND.

## Circuit Schematic and functional simulation

In this folder is the schematic of the PAL deduced by the output of the chip. It is likely not 100% correct to the internal truth table. To view the simulated version, load the "E765B1 PAL" file into the excelent Circuit Simulator by Paul Falstad at the following URL: http://falstad.com/circuit/circuitjs.html.