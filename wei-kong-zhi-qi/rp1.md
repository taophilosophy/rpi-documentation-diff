# RP1

## About RP1

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/microcontrollers/rp1/about_rp1.adoc)

![Architecture diagram of the RP1](https://www.raspberrypi.com/documentation/microcontrollers/images/rp1.jpg?hash=330f99964282731d76eaffa153a62261)

Architecture

RP1 is a 12×12mm, 0.65mm-pitch BGA southbridge, which provides the majority of the I/O capabilities for Raspberry Pi 5.

It provides:

* 4-lane PCIe 2.0 endpoint
* Gigabit Ethernet MAC
* 2× USB 3 host controllers

  * Each has 1× USB 3 and 1× USB 2 port
  * More than twice the usable USB bandwidth vs. Raspberry Pi 4
* 2× SDIO ports/eMMC (not used on Raspberry Pi 5)
* 2× MIPI transceivers (4-lane, supporting DSI and CSI-2)
* Video DAC (3-channel, supporting PAL/NTSC and VGA)

  * Only one channel (composite) used on Raspberry Pi 5
* Low-speed peripherals (SPI, UART, I2C, PWM, GPIO, I2S)
* Delta-sigma PWM audio out

More information on RP1 can be found in the [RP1 Peripherals](https://datasheets.raspberrypi.com/rp1/rp1-peripherals.pdf) document.
