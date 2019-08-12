# D.I.Y SMART RGB MATRIX 8x16

_Captured: 2018-11-09 at 13:12 from [www.instructables.com](https://www.instructables.com/id/DIY-SMART-RGB-MATRIX-8x16/)_

![](https://cdn.instructables.com/F2B/83T5/JNSR99AT/F2B83T5JNSR99AT.LARGE.jpg?auto=webp&width=580)

![](https://cdn.instructables.com/FHC/8UB1/JNSR9C8Y/FHC8UB1JNSR9C8Y.LARGE.jpg?auto=webp&width=620)

![Picture of PARTS LIST & TOOL](https://cdn.instructables.com/FUL/TZVJ/JNMRTYIB/FULTZVJJNMRTYIB.LARGE.jpg?auto=webp&width=560)

![Picture of SHEMATIC DIAGRAM](https://cdn.instructables.com/F7N/K403/JNMRTYD3/F7NK403JNMRTYD3.LARGE.jpg?auto=webp&width=1002)

![](https://cdn.instructables.com/FM3/V1R9/JNOVGTTZ/FM3V1R9JNOVGTTZ.LARGE.jpg)

![](https://www.instructables.com/files/deriv/F9S/GXJ7/JNSR8UK6/F9SGXJ7JNSR8UK6.LARGE.jpg)

![](https://www.instructables.com/files/deriv/FIK/94OO/JNSR8UVA/FIK94OOJNSR8UVA.LARGE.jpg)

![](https://cdn.instructables.com/FZD/1POP/JNNF3C3Q/FZD1POPJNNF3C3Q.LARGE.jpg)

![](https://cdn.instructables.com/F6X/7RWD/JNNF3CKH/F6X7RWDJNNF3CKH.LARGE.jpg)

![](https://cdn.instructables.com/FO2/SKPX/JNNF3CKK/FO2SKPXJNNF3CKK.LARGE.jpg)

## Step 4: BUILD DRIVER BOARD

Driver Boards, including: column (layer) scanning (74HC138 + Transistor A1013), row scanning (74HC595 + ULN2803) and Arduino Uno/ Nano. Led Matrix is a shield that it can be plugged on top of the Driver Board.

  * Prepare the horizontal & vertical female header at Driver Board. At this time, I also soldered 16 x A1013 transistors with its outputs is aligned with corresponding columns of Led Matrix.
![](https://cdn.instructables.com/FYZ/66FJ/JNNF3D94/FYZ66FJJNNF3D94.LARGE.jpg)

  * Testing whether male header of Led Matrix & female of Driver Board is matching together or not to correct it.
![](https://cdn.instructables.com/FIA/LGKG/JNNF3DCT/FIALGKGJNNF3DCT.LARGE.jpg)

  * Visually checked the contacting between male and female.Well, it is matching together like that.
![](https://cdn.instructables.com/F34/FXTO/JNM87NKH/F34FXTOJNM87NKH.LARGE.jpg)

  * Following schematic below, I installed 3x 74HC595, 3 x ULN2803, 24 x 100Ω Resistors, 3 x 0.1uF Capacitors on prototype board and did soldering work. Each shift register 74HC595 will control one color so we have totally 3 shift registers for handling: Red, Green, Blue colors. Arduino pins assigned for SPI controlling:

**\- BLANK PIN (ENABLE) -----> 3 (PD2)  
**

**\- LATCH PIN -----------------> 2 (PD3)**

**\- CLOCK PIN (SCK) ----------> 13 **

**\- DATA PIN (MOSI)------------> 11 **

![](https://www.instructables.com/files/deriv/FGH/VD8Y/JNNF2TT3/FGHVD8YJNNF2TT3.LARGE.jpg)

![](https://cdn.instructables.com/F3G/WAKK/JNNF3FBM/F3GWAKKJNNF3FBM.LARGE.jpg)

  * For column circuit, I use 4 signals from Arduino Nano for multiplexing 2 x 74HC138 to control 16 RGB led's columns through 16 x A1013 transistors circuit. It is need to connect 560Ω resistor between pole B of transistor and 74HC138 for polarization. Arduino PORTD pins were used for multiplexing as follows:

**\- D4 (PD4) connect to A0.**

**\- D5 (PD5) connect to A1.**

**\- D6 (PD6) connect to A2.**

**\- D7 (PD7) connect to A3.**

**![](https://www.instructables.com/files/deriv/FGZ/J6AT/JNMRTYFC/FGZJ6ATJNMRTYFC.LARGE.jpg)**

**_Note_**: 74HC138 has active low outputs, it means this chip sets the selected pin low and all others high. Below is Truth table for this combination:

![](https://cdn.instructables.com/F95/CAJ1/JNMRTY12/F95CAJ1JNMRTY12.LARGE.jpg)

![](https://cdn.instructables.com/FF6/OB28/JNNF3FEE/FF6OB28JNNF3FEE.LARGE.jpg)

![](https://cdn.instructables.com/FVS/O9AQ/JNNF3FFZ/FVSO9AQJNNF3FFZ.LARGE.jpg)

**_Note_: Back side of above picture is the 1st version that I test with Arduino Uno with some male headers. **

\- Soldering DC female jack for power supply and female header for Arduino Nano.

![](https://www.instructables.com/files/deriv/F3Z/ZQOS/JNOVIJ95/F3ZZQOSJNOVIJ95.LARGE.jpg)

\- Installing Arduino Nano on prototype board. I also reserved space for NodeMCU for further future extension. This nodeMCU communicate to Arduino Nano through I2C protocol and it is pre-connected.

![](https://www.instructables.com/files/deriv/F2H/I94P/JNOVIJAD/F2HI94PJNOVIJAD.LARGE.jpg)

\- Cleaning the boards, check again all RGB leds on Matrix board, continuity checking with a Multimeter. And then, connecting Led Matrix & Driver Board together. Here is the final results that I achieved.

![](https://www.instructables.com/files/deriv/FNP/RPZ1/JNOVIJTN/FNPRPZ1JNOVIJTN.LARGE.jpg)

![](https://www.instructables.com/files/deriv/FP8/RI4X/JNOVIJTM/FP8RI4XJNOVIJTM.LARGE.jpg)

![](https://www.instructables.com/files/deriv/F66/VXWE/JNSR9C7P/F66VXWEJNSR9C7P.LARGE.jpg)

![](https://www.instructables.com/files/deriv/FQO/CP20/JNSR99BK/FQOCP20JNSR99BK.LARGE.jpg)

![](https://www.instructables.com/files/deriv/F6J/O2XA/JNSR9I5S/F6JO2XAJNSR9I5S.LARGE.jpg)

![](https://www.instructables.com/files/deriv/F8F/12TW/JNSR9I5T/F8F12TWJNSR9I5T.LARGE.jpg)

![](https://www.instructables.com/files/deriv/F34/SENA/JNSR8Z6C/F34SENAJNSR8Z6C.LARGE.jpg)

![](https://cdn.instructables.com/F2H/I94P/JNOVIJAD/F2HI94PJNOVIJAD.LARGE.jpg)

![](https://www.instructables.com/files/deriv/FQY/X688/JNUL8K8X/FQYX688JNUL8K8X.LARGE.jpg)

![Picture of BECOME AUTO-ROTATE MATRIX](https://cdn.instructables.com/F3U/C9Y7/JO4NH9ZZ/F3UC9Y7JO4NH9ZZ.LARGE.jpg?auto=webp&crop=3:2)

![](https://www.instructables.com/files/deriv/FVR/L2H0/JO4NH8CU/FVRL2H0JO4NH8CU.LARGE.jpg)
