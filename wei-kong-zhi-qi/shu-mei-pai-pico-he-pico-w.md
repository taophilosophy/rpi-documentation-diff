# Pico-series Microcontrollers

Pico-series devices are organised into **families** based on product generation.

The original Raspberry Pi Pico family, referred to as Pico or Pico 1, comes in four variants:

* Raspberry Pi Pico
* Raspberry Pi Pico H
* Raspberry Pi Pico W
* Raspberry Pi Pico WH

The second-generation Raspberry Pi Pico family is referred to as Pico 2. Pico 2 comes in two variants:

* Raspberry Pi Pico 2
* Raspberry Pi Pico 2 with headers

## Pico 2 family


![pico 2](https://www.raspberrypi.com/documentation/microcontrollers/images/pico-2.png?hash=c4b2ccf2504c98fdd111405dd95346b5)

The Raspberry Pi Pico 2 family consists of two boards; Raspberry Pi Pico 2, and Raspberry Pi Pico 2 with headers.

### Raspberry Pi Pico 2

Raspberry Pi Pico 2 is a low-cost, high-performance microcontroller board with flexible digital interfaces. Key features include:

* [RP2350](https://www.raspberrypi.com/documentation/microcontrollers/silicon.html#rp2350) microcontroller chip designed by Raspberry Pi in the United Kingdom
* Dual Cortex-M33 or Hazard3 processors at up to 150MHz
* 520KB of SRAM, and 4MB of on-board flash memory
* USB 1.1 with device and host support
* Low-power sleep and dormant modes
* Drag-and-drop programming using mass storage over USB
* 26× multi-function GPIO pins including 3 that can be used for ADC
* 2× SPI, 2× I2C, 2× UART, 3× 12-bit 500ksps Analogue to Digital Converter (ADC), 24× controllable PWM channels
* 2× Timer with 4 alarms, 1× AON Timer
* Temperature sensor
* 3 × Programmable IO (PIO) blocks, 12 state machines total for custom peripheral support

  * Flexible, user-programmable high-speed IO
  * Can emulate interfaces such as SD Card and VGA

The Raspberry Pi Pico 2 comes as a castellated module which allows soldering direct to carrier boards, while the Pico 2 *with headers* comes with pre-soldered headers.

| Note | Both boards have a three pin Serial Wire Debug (SWD) header. However, the Pico 2 with headers breaks this out into a small, keyed, [3-pin connector](https://datasheets.raspberrypi.com/debug/debug-connector-specification.pdf) while the Pico has three castellated through-hole pins adjacent to the edge of the board. |
| ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

### Pinout and design files

![pico 2 r4 pinout](https://www.raspberrypi.com/documentation/microcontrollers/images/pico-2-r4-pinout.svg)

* Download the [Pinout Diagram](https://datasheets.raspberrypi.com/pico/Pico-2-Pinout.pdf) (PDF)
* Download [Design Files](https://datasheets.raspberrypi.com/pico/RPi-Pico-2-PUBLIC-20240708.zip) (Cadence Allegro)
* Download [STEP File](https://datasheets.raspberrypi.com/pico/Pico-2-step-20240708.zip)
* Download [Fritzing Part](https://datasheets.raspberrypi.com/pico/Pico-2-Fritzing-20240708.fzpz) for Raspberry Pi Pico

| Note | More information on Fritzing is available on the [fritzing.org](https://fritzing.org/) website. |
| ------ | ------------------------------------------------------------ |

## Pico 1 family

![pico 1s](https://www.raspberrypi.com/documentation/microcontrollers/images/pico-1s.png?hash=37f90d0137e81859630d4f0943b6f3d5)

The Raspberry Pi Pico 1 family consists of four boards; Raspberry Pi Pico (far left), Pico H (middle left), Pico W (middle right), and Pico WH (far right).

### Raspberry Pi Pico and Pico H

Raspberry Pi Pico is a low-cost, high-performance microcontroller board with flexible digital interfaces. Key features include:

* [RP2040](https://www.raspberrypi.com/documentation/microcontrollers/silicon.html#rp2040) microcontroller chip designed by Raspberry Pi in the United Kingdom
* Dual-core Arm Cortex M0+ processor, flexible clock running up to 133 MHz
* 264KB of SRAM, and 2MB of on-board flash memory
* USB 1.1 with device and host support
* Low-power sleep and dormant modes
* Drag-and-drop programming using mass storage over USB
* 26 × multi-function GPIO pins
* 2 × SPI, 2 × I2C, 2 × UART, 3 × 12-bit ADC, 16 × controllable PWM channels
* Accurate clock and timer on-chip
* Temperature sensor
* Accelerated floating-point libraries on-chip
* 8 × Programmable I/O (PIO) state machines for custom peripheral support

The Raspberry Pi Pico comes as a castellated module which allows soldering direct to carrier boards, while the Pico H comes with pre-soldered headers.

| Note | Both boards have a three pin Serial Wire Debug (SWD) header. However, the Pico H has this broken out into a small, keyed, [3-pin connector](https://datasheets.raspberrypi.com/debug/debug-connector-specification.pdf) while the Pico has three castellated through-hole pins adjacent to the edge of the board. |
| ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

#### Pinout and design files

![pico pinout](https://www.raspberrypi.com/documentation/microcontrollers/images/pico-pinout.svg)

* Download the [Pinout Diagram](https://datasheets.raspberrypi.com/pico/Pico-R3-A4-Pinout.pdf) (PDF)
* Download [Design Files](https://datasheets.raspberrypi.com/pico/RPi-Pico-R3-PUBLIC-20200119.zip) (Cadence Allegro)
* Download [STEP File](https://datasheets.raspberrypi.com/pico/Pico-R3-step.zip)
* Download [Fritzing Part](https://datasheets.raspberrypi.com/pico/Pico-R3-Fritzing.fzpz) for Raspberry Pi Pico
* Download [Fritzing Part](https://datasheets.raspberrypi.com/pico/PicoH-Fritzing.fzpz) for Raspberry Pi Pico H

| Note | More information on Fritzing is available on the [fritzing.org](https://fritzing.org/) website. |
| ------ | ------------------------------------------------------------ |

### Raspberry Pi Pico W and Pico WH

Raspberry Pi Pico W adds on-board single-band 2.4GHz wireless interfaces (802.11n) using the Infineon CYW43439 while retaining the Pico form factor. The on-board 2.4GHz wireless interface has the following features:

* Wireless (802.11n), single-band (2.4 GHz)
* WPA3
* Soft access point supporting up to four clients
* Bluetooth 5.2

  * Support for Bluetooth LE Central and Peripheral roles
  * Support for Bluetooth Classic

The antenna is an onboard antenna licensed from ABRACON (formerly ProAnt). The wireless interface is connected via SPI to the [RP2040](https://www.raspberrypi.com/documentation/microcontrollers/silicon.html#rp2040) microcontroller.

Due to pin limitations, some of the wireless interface pins are shared. The CLK is shared with VSYS monitor, so only when there isn’t an SPI transaction in progress can VSYS be read via the ADC. The Infineon CYW43439 DIN/DOUT and IRQ all share one pin on the RP2040. Only when an SPI transaction isn’t in progress is it suitable to check for IRQs. The interface typically runs at 33MHz.

For best wireless performance, the antenna should be in free space. For instance, putting metal under or close by the antenna can reduce its performance both in terms of gain and bandwidth. Adding grounded metal to the sides of the antenna can improve the antenna’s bandwidth.

| Note | The CYW43439 wireless chip is connected via SPI to the RP2040.The CYW43439 supports both 802.11 wireless and Bluetooth over this interface. |
| ------ | --------------------------------------------------------------------------------------------------------------------------------------------- |

| Important | By default `libcyw43` is licensed for non-commercial use, but Pico W users, and anyone else who builds their product around RP2040 and CYW43439, benefit from a free [commercial-use license](https://github.com/georgerobotics/cyw43-driver/blob/195dfcc10bb6f379e3dea45147590db2203d3c7b/LICENSE.RP). |
| ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |

| Important | In addition to the [standard BTstack licensing](https://github.com/bluekitchen/btstack/blob/master/LICENSE) terms, a [supplemental licence](https://github.com/raspberrypi/pico-sdk/blob/master/src/rp2_common/pico_btstack/LICENSE.RP) which covers commercial use of BTstack with Raspberry Pi Pico W or Raspberry Pi Pico WH is provided. |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------ |

#### Pinout and design files

![picow pinout](https://www.raspberrypi.com/documentation/microcontrollers/images/picow-pinout.svg)

* Download the [Pinout Diagram](https://datasheets.raspberrypi.com/picow/PicoW-A4-Pinout.pdf) (PDF)
* Download [Design Files](https://datasheets.raspberrypi.com/picow/RPi-PicoW-PUBLIC-20220607.zip) (Cadence Allegro)
* Download [STEP File](https://datasheets.raspberrypi.com/picow/PicoW-step.zip)
* Download [Fritzing Part](https://datasheets.raspberrypi.com/picow/PicoW-Fritzing.fzpz) for Raspberry Pi Pico W

## Documentation


Documentation for Pico-series and other Raspberry Pi microcontroller-based boards.

### RP2350

[RP2350 Datasheet](https://datasheets.raspberrypi.com/rp2350/rp2350-datasheet.pdf)

A microcontroller by Raspberry Pi

[Hardware design with RP2350](https://datasheets.raspberrypi.com/rp2350/hardware-design-with-rp2350.pdf)

Using RP2350 microcontrollers to build boards and products

### RP2040

[RP2040 Datasheet](https://datasheets.raspberrypi.com/rp2040/rp2040-datasheet.pdf)

A microcontroller by Raspberry Pi

[Hardware design with RP2040](https://datasheets.raspberrypi.com/rp2040/hardware-design-with-rp2040.pdf)

Using RP2040 microcontrollers to build boards and products

### Raspberry Pi Pico 2

[Raspberry Pi Pico 2 Datasheet](https://datasheets.raspberrypi.com/pico/pico-2-datasheet.pdf)

An RP2350-based microcontroller board

[Getting started with Raspberry Pi Pico-series Microcontrollers](https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf)

C/C++ development with Raspberry Pi Pico-series devices and other Raspberry Pi microcontroller-based boards

### Raspberry Pi Pico

[Raspberry Pi Pico Datasheet](https://datasheets.raspberrypi.com/pico/pico-datasheet.pdf)

An RP2040-based microcontroller board

[Getting started with Raspberry Pi Pico](https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf)

C/C++ development with Raspberry Pi Pico and other RP2040-based microcontroller boards

### Raspberry Pi Pico W

[Raspberry Pi Pico W Datasheet](https://datasheets.raspberrypi.com/picow/pico-w-datasheet.pdf)

An RP2040-based microcontroller board with wireless

[Connecting to the Internet with Raspberry Pi Pico W](https://datasheets.raspberrypi.com/picow/connecting-to-the-internet-with-pico-w.pdf)

Getting Raspberry Pi Pico W online with C/C++ or MicroPython

| Note | Documentation introducing working with Wi-Fi and Bluetooth on Raspberry Pi Pico W with C/C++ or MicroPython is presented in the [Connecting to the Internet with Raspberry Pi Pico W](https://datasheets.raspberrypi.com/picow/connecting-to-the-internet-with-pico-w.pdf) book. |
| ------ | ---------------------------------------------------------------------------------------------------------------------------------------- |

### Software Development

[Raspberry Pi Pico C/C++ SDK](https://datasheets.raspberrypi.com/pico/raspberry-pi-pico-c-sdk.pdf)

Libraries and tools for C/C++ development on RP2040 microcontrollers

[Raspberry Pi Pico Python SDK](https://datasheets.raspberrypi.com/pico/raspberry-pi-pico-python-sdk.pdf)

A MicroPython environment for RP2040 microcontrollers

The API level Doxygen documentation for the Raspberry Pi Pico C/C++ SDK is also available [as a micro-site](https://rptl.io/pico-doxygen).

| Note | A [one-click installer](https://github.com/raspberrypi/pico-setup-windows/releases/latest/download/pico-setup-windows-x64-standalone.exe) for the Pico C/C++ SDK for Windows 10 and Windows 11 is available. |
| ------ | ----------------------------------------------------------------------- |

## Software Utilities


### What is on your Pico-series device?

If you are unsure what is programmed into your Raspberry Pi Pico-series device, and the program was built using the Pico C/C++ SDK, it will usually have a name and other useful information embedded into the binary. You can use the [Picotool](https://github.com/raspberrypi/picotool) command line utility to find out these details. Full instructions on how to use Picotool to do this are available in our '[getting started](https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf)' documentation.

* Go to the [Picotool Github repository](https://github.com/raspberrypi/picotool).

### Debugging using another Pico-series device

| Caution | Pico 2 is not yet supported by `debuprobe_on_pico` debugging software. |
| --------- | ----------------------------------------------------- |

You can use one Pico-series device to debug another Pico-series device. This is possible via `debugprobe`, an application that allows a Pico to act as a USB → SWD and UART converter.

You can find the latest release of the firmware in [the debugprobe GitHub repository](https://github.com/raspberrypi/debugprobe/releases/latest).

Download `debugprobe_on_pico.uf2` from the latest release.

Push and hold the BOOTSEL button as you plug the debugger device into your computer to mount a volume called "RPI-RP2".

Copy `debugprobe_on_pico.uf2` onto the volume. The volume will dismount automatically after the file finishes copying onto the device.

Your device will reboot and now runs an updated version of the `debugprobe` firmware. It is now ready for debugging.

| Tip | For instructions on how to use the debugger, see [Getting Started with Pico-series Microcontrollers](https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf). |
| ----- | ---------------------------------------------------- |

### Resetting Flash memory

Pico’s BOOTSEL mode lives in read-only memory inside the RP2040 chip, and can’t be overwritten accidentally. No matter what, if you hold down the BOOTSEL button when you plug in your Pico, it will appear as a drive onto which you can drag a new UF2 file. There is no way to brick the board through software. However, there are some circumstances where you might want to make sure your Flash memory is empty. You can do this by dragging and dropping a special UF2 binary onto your Pico when it is in mass storage mode.

* Download the [UF2 file](https://datasheets.raspberrypi.com/soft/flash_nuke.uf2)
* See the [code on Github](https://github.com/raspberrypi/pico-examples/blob/master/flash/nuke/nuke.c)