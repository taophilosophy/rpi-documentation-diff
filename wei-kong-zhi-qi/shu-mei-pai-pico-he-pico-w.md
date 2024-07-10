# Raspberry Pi Pico and Pico W

## The family

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/microcontrollers/raspberry-pi-pico/about_pico.adoc)

![four picos](https://www.raspberrypi.com/documentation/microcontrollers/images/four_picos.jpg?hash=3f928dff64ab31c4f3b1caecf4fb83a4)

The Raspberry Pi Pico family currently consists of four boards; Raspberry Pi Pico (far left), Pico H (middle left), Pico W (middle right), and Pico WH (far right).

## Raspberry Pi Pico and Pico H

Raspberry Pi Pico is a low-cost, high-performance microcontroller board with flexible digital interfaces. Key features include:

* [RP2040](https://www.raspberrypi.com/documentation/microcontrollers/rp2040.html#welcome-to-rp2040) microcontroller chip designed by Raspberry Pi in the United Kingdom
* Dual-core Arm Cortex M0+ processor, flexible clock running up to 133 MHz
* 264kB of SRAM, and 2MB of on-board flash memory
* USB 1.1 with device and host support
* Low-power sleep and dormant modes
* Drag-and-drop programming using mass storage over USB
* 26 × multi-function GPIO pins
* 2 × SPI, 2 × I2C, 2 × UART, 3 × 12-bit ADC, 16 × controllable PWM channels
* Accurate clock and timer on-chip
* Temperature sensor
* Accelerated floating-point libraries on-chip
* 8 × Programmable I/O (PIO) state machines for custom peripheral support

The Raspberry Pi Pico comes as a castellated module allows soldering direct to carrier boards, while the Pico H comes with pre-soldered headers.

| NOTE | Both boards have a three pin Serial Wire Debug (SWD) header. However, the Pico H has this broken out into a small, keyed, [3-pin connector](https://datasheets.raspberrypi.com/debug/debug-connector-specification.pdf) while the Pico has three castellated through-hole pins adjacent to the edge of the board. |
| ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

### Pinout and design files

![pico pinout](https://www.raspberrypi.com/documentation/microcontrollers/images/pico-pinout.svg)

* Download the [Pinout Diagram](https://datasheets.raspberrypi.com/pico/Pico-R3-A4-Pinout.pdf) (PDF)
* Download [Design Files](https://datasheets.raspberrypi.com/pico/RPi-Pico-R3-PUBLIC-20200119.zip) (Cadence Allegro)
* Download [STEP File](https://datasheets.raspberrypi.com/pico/Pico-R3-step.zip)
* Download [Fritzing Part](https://datasheets.raspberrypi.com/pico/Pico-R3-Fritzing.fzpz) for Raspberry Pi Pico
* Download [Fritzing Part](https://datasheets.raspberrypi.com/pico/PicoH-Fritzing.fzpz) for Raspberry Pi Pico H

| NOTE | More information on Fritzing is available on the [fritzing.org](https://fritzing.org/) website. |
| ------ | ------------------------------------------------------------ |

## Raspberry Pi Pico W and Pico WH

Raspberry Pi Pico W adds on-board single-band 2.4GHz wireless interfaces (802.11n) using the Infineon CYW43439 while retaining the Pico form factor. The on-board 2.4GHz wireless interface has the following features:

* Wireless (802.11n), single-band (2.4 GHz)
* WPA3
* Soft access point supporting up to four clients
* Bluetooth 5.2

  * Support for Bluetooth LE Central and Peripheral roles
  * Support for Bluetooth Classic

The antenna is an onboard antenna licensed from ABRACON (formerly ProAnt). The wireless interface is connected via SPI to the [RP2040](https://www.raspberrypi.com/documentation/microcontrollers/rp2040.html#welcome-to-rp2040) microcontroller.

Due to pin limitations, some of the wireless interface pins are shared. The CLK is shared with VSYS monitor, so only when there isn’t an SPI transaction in progress can VSYS be read via the ADC. The Infineon CYW43439 DIN/DOUT and IRQ all share one pin on the RP2040. Only when an SPI transaction isn’t in progress is it suitable to check for IRQs. The interface typically runs at 33MHz.

For best wireless performance, the antenna should be in free space. For instance, putting metal under or close by the antenna can reduce its performance both in terms of gain and bandwidth. Adding grounded metal to the sides of the antenna can improve the antenna’s bandwidth.

| NOTE | The CYW43439 wireless chip is connected via SPI to the RP2040.The CYW43439 supports both 802.11 wireless and Bluetooth over this interface. |
| ------ | --------------------------------------------------------------------------------------------------------------------------------------------- |

| IMPORTANT | By default `libcyw43` is licensed for non-commercial use, but Pico W users, and anyone else who builds their product around RP2040 and CYW43439, benefit from a free [commercial-use license](https://github.com/georgerobotics/cyw43-driver/blob/195dfcc10bb6f379e3dea45147590db2203d3c7b/LICENSE.RP). |
| ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |

| IMPORTANT | In addition to the [standard BTstack licensing](https://github.com/bluekitchen/btstack/blob/master/LICENSE) terms, a [supplemental licence](https://github.com/raspberrypi/pico-sdk/blob/master/src/rp2_common/pico_btstack/LICENSE.RP) which covers commercial use of BTstack with Raspberry Pi Pico W or Raspberry Pi Pico WH is provided. |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------ |

### Pinout and design files

![picow pinout](https://www.raspberrypi.com/documentation/microcontrollers/images/picow-pinout.svg)

* Download the [Pinout Diagram](https://datasheets.raspberrypi.com/picow/PicoW-A4-Pinout.pdf) (PDF)
* Download [Design Files](https://datasheets.raspberrypi.com/picow/RPi-PicoW-PUBLIC-20220607.zip) (Cadence Allegro)
* Download [STEP File](https://datasheets.raspberrypi.com/picow/PicoW-step.zip)
* Download [Fritzing Part](https://datasheets.raspberrypi.com/picow/PicoW-Fritzing.fzpz) for Raspberry Pi Pico W

## Documentation

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/microcontrollers/microcontroller_docs.adoc)

Documentation for Raspberry Pi Pico and other RP2040-based boards.

### RP2040 Device

[RP2040 Datasheet](https://datasheets.raspberrypi.com/rp2040/rp2040-datasheet.pdf)A microcontroller by Raspberry Pi

[Hardware design with RP2040](https://datasheets.raspberrypi.com/rp2040/hardware-design-with-rp2040.pdf)Using RP2040 microcontrollers to build boards and products

### Raspberry Pi Pico

[Raspberry Pi Pico Datasheet](https://datasheets.raspberrypi.com/pico/pico-datasheet.pdf)An RP2040-based microcontroller board

[Getting started with Raspberry Pi Pico](https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf)C/C++ development with Raspberry Pi Pico and other RP2040-based microcontroller boards

### Raspberry Pi Pico W

[Raspberry Pi Pico W Datasheet](https://datasheets.raspberrypi.com/picow/pico-w-datasheet.pdf)An RP2040-based microcontroller board with wireless

[Connecting to the Internet with Raspberry Pi Pico W](https://datasheets.raspberrypi.com/picow/connecting-to-the-internet-with-pico-w.pdf)Getting Raspberry Pi Pico W online with C/C++ or MicroPython

| NOTE | Documentation introducing working with Wi-Fi and Bluetooth on Raspberry Pi Pico W with C/C++ or MicroPython is presented in the [Connecting to the Internet with Raspberry Pi Pico W](https://datasheets.raspberrypi.com/picow/connecting-to-the-internet-with-pico-w.pdf) book. |
| ------ | ---------------------------------------------------------------------------------------------------------------------------------------- |

### Software Development

[Raspberry Pi Pico C/C++ SDK](https://datasheets.raspberrypi.com/pico/raspberry-pi-pico-c-sdk.pdf)Libraries and tools for C/C++ development on RP2040 microcontrollers

[Raspberry Pi Pico Python SDK](https://datasheets.raspberrypi.com/pico/raspberry-pi-pico-python-sdk.pdf)A MicroPython environment for RP2040 microcontrollers

The API level Doxygen documentation for the Raspberry Pi Pico C/C++ SDK is also available [as a micro-site](https://rptl.io/pico-doxygen).

| NOTE | A [one-click installer](https://github.com/raspberrypi/pico-setup-windows/releases/latest/download/pico-setup-windows-x64-standalone.exe) for the Pico C/C++ SDK for Windows 10 and Windows 11 is available. |
| ------ | ----------------------------------------------------------------------- |

## Software Utilities

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/microcontrollers/raspberry-pi-pico/utilities.adoc)

### What is on your Pico?

If you have forgotten what has been programmed into your Raspberry Pi Pico, and the program was built using our Pico C/C++ SDK, it will usually have a name and other useful information embedded into the binary. You can use the [Picotool](https://github.com/raspberrypi/picotool) command line utility to find out these details. Full instructions on how to use Picotool to do this are available in our '[getting started](https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf)' documentation.

* Go to the [Picotool Github repository](https://github.com/raspberrypi/picotool).

### Debugging using another Raspberry Pi Pico

You can use one Raspberry Pi Pico to debug another Pico. This is possible via `debugprobe`, an application that allows a Pico to act as a USB → SWD and UART converter.

You can find the latest release of the firmware in [the debugprobe GitHub repository](https://github.com/raspberrypi/debugprobe/releases/latest).

Download `debugprobe_on_pico.uf2` from the latest release.

Push and hold the BOOTSEL button as you plug the debugger Pico into your computer to mount a volume called "RPI-RP2".

Copy `debugprobe_on_pico.uf2` onto the volume. The volume will dismount automatically after the file finishes copying onto the device.

Your Pico will reboot and now runs an updated version of the `debugprobe` firmware. It is now ready for debugging.

| TIP | For instructions on how to use the debugger, see [Getting Started with Pico](https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf). |
| ----- | ---------------------------------------------------- |

### Resetting Flash memory

Pico’s BOOTSEL mode lives in read-only memory inside the RP2040 chip, and can’t be overwritten accidentally. No matter what, if you hold down the BOOTSEL button when you plug in your Pico, it will appear as a drive onto which you can drag a new UF2 file. There is no way to brick the board through software. However, there are some circumstances where you might want to make sure your Flash memory is empty. You can do this by dragging and dropping a special UF2 binary onto your Pico when it is in mass storage mode.

* Download the [UF2 file](https://datasheets.raspberrypi.com/soft/flash_nuke.uf2)
* See the [code on Github](https://github.com/raspberrypi/pico-examples/blob/master/flash/nuke/nuke.c)
