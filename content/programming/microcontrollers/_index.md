---
author: gbmhunter
categories: [ "Programming", "Microcontrollers" ]
date: 2011-09-07
draft: false
tags: [ "programming", "microcontrollers" ]
title: Microcontrollers
type: page
---

## Overview
Microcontrollers are:  
-self contained computers on a chip  
-with additional interface hardware features ("peripherals")  
-resource constrained  
-programmed to run without operating systems  
-typically programmed in C   

## CPU

## Clocks

## Memory

### Flash
### RAM
### EEPROM

## Inputs/Outputs

GPIO are typically organized in banks that can be written to simultaneously, and potentially run off of different I/O voltages. In addition to being useable as inputs and outputs, they often have secondary special functions, such as ADC, clock inputs, etc. Internal to the chip this is handled by muxing the pins signal off to different circuitry.

//insert image of typical GPIO structure


Pins are typically assigned direction before being used, and optionally internal pullups.
### ESD

Pins can have a variety of ESD structures, some of which are pictured below. It's important that if a pin is tied to a rail via an esd diode, that that rail remains powered, otherwise it will become forward biased if another signal attempts to drive it. If you observe a signal being stuck at 0.7v or some intermediate voltage, this may be the reason.

## Peripherals

### Timers/Counters

### ADCs

### USART

### Interrupts
