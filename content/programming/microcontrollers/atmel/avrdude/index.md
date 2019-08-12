---
author: gbmhunter
categories: [ "Programming", "Embedded", "Microcontrollers" ]
date: 2017-10-06
draft: false
tags: [ "AVR", "AVRDUDE", "Atmel", "microcontroller", "programmer", "embedded", "baudrate" ]
title: AVRDUDE
type: page
---

## Overview

[AVRDUDE](http://www.nongnu.org/avrdude/) (or avrdude) is a popular, open-source, third-party (i.e. non-Atmel) command-line utility for programming Atmel microcontrollers.

## Commands

[AVRDUDE command examples](https://www.nongnu.org/avrdude/user-manual/avrdude_6.html#Example-Command-Line-Invocations)

```
man avrdude # rtfm
avrdude -c ? # list supported programmers
avrdude -p ? # list supported targets
avrdude -c avrisp2 -p m168 -n # test connection, read fuse values -n means write nothing
avrdude -c avrisp2 -p m168 -t # -t enters terminal mode, help for more info, quit to get back
avrdude -v # verbose mode, prints useful config info
avrdude -c avrisp2 -p m168 -U flash:r:rawdump:r # dump the flash contents as raw binary into a file called "rawdump"
```
