---
author: grumptronix
date: 2019-07-09 
draft: false
title: ATmega
type: page
---

## Overview

The ATmega is a microcontroller series by Atmel. It is an 8-bit architecture, with chip variants depending on the needed memory, peripherals and package size. Below are code examples for the ATmega range of microcontrollers.

{{< figure src="/images/2011/09/atmel-avr-atmega168-ic-photo-www-wolfpaulus-com.jpeg" width="426px" caption="A photo of the Atmel AVR ATmega168 microcontroller. Image from https://wolfpaulus.com."  >}}

## References
[Atmel ISP app note]("http://ww1.microchip.com/downloads/en/AppNotes/Atmel-0943-In-System-Programming_ApplicationNote_AVR910.pdf")
[AVRISP mk2 datashet]("http://ww1.microchip.com/downloads/en/DeviceDoc/Atmel-42093-AVR-ISP-mkII_UserGuide.pdf")

## Toolchains
Linux: `sudo aptitude install avrdude avrdude-doc binutils-avr avr-libc gcc-avr gdb-avr`  
Mac: https://www.obdev.at/products/crosspack/index.html

## Arduino

You can use Arduino hardware as a standard AVR dev board. You can use the Arduino as a flash programmer, and you can use the Arduino IDE to write code in regular old C.

### Write C in Arduino IDE

1. copy https://github.com/hexagon5un/AVR-Programming/tree/master/AVR-Programming-Library to your arduino libraries folder.
2. Withing the Arduino IDE with your sketch open, Sketch->Include Library->AVR-Programming-Library (this just adds all the #include directives)
3. copy your C code into the newly created directory (with the .ino file) or in a new tab Cmd-Shift-N  

## Registers

```
DDRx  # 8 bit data direction register for port x: 1 = output, 0 = input, for the x bank
PORTx # 8 bit write register for port x output: 1 = high, 0 = low. input: 1 = pullup enabled 0 = high-z
PINx  # 8 bit read register for port x: read input state 1 = high, 0 = low
```

## Gotchas

Atmega168 (and probably others) ship with an internal oscillator running at 8MHz, with the CLKDIV8 fuse bit set for a 1MHz clock. If your hello world blinky sketch seems off by a factor of ten, it is likely really a factor of 8 because the CLKDIV8 isn't set. Solution is to fix your makefile F_CPU to 8000000UL (or of course, set the CLKDIV8 fuse).

## Old Content

### Code Examples

One annoyance with the ATmega series is that Atmel wrote all the code to compile with IAR Compiler, a paid for IDE, and not their own proprietary and free AVR Studio. This means that you have to port the code to work with the Win-AVR compiler if you want to use ATMEL's code examples. The main differences between the two compilers are precompiler directives (e.g. #pragma), delay functions, and the handling of variables that are stored in flash.

### Code Compatibility

ATMEL has done a good job at keeping code as similar as possible between microcontrollers in the ATmega family. One point to note is that at some point, they decided to add a '0' to all peripheral register descriptions, even when there was only one of these peripherals present in the chip (e.g. `USART0` instead of `USART`). This generally applies to all the registers that are associated with the peripheral (e.g. RX0 and TX0 instead of RX and TX). You may have to add these before code will compile when using older source code with the newer avr libraries.
