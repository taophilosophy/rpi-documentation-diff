# Raspberry Pi Debug Probe

## About the Debug Probe

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/microcontrollers/debug-probe/introduction.adoc)

![debug probe](https://www.raspberrypi.com/documentation/microcontrollers/images/debug-probe.jpg?hash=5a67801105b1ed0d696230a41a13832a)

The Raspberry Pi Debug Probe is a USB device that provides both a UART serial port and a standard Arm Serial Wire Debug (SWD) interface. The probe is designed for easy, solderless, plug-and-play debugging. It has the following features:

* USB to ARM [Serial Wire Debug](https://developer.arm.com/documentation/ihi0031/a/The-Serial-Wire-Debug-Port--SW-DP-/Introduction-to-the-ARM-Serial-Wire-Debug--SWD--protocol) (SWD) port
* USB to UART bridge
* Compatible with the [CMSIS-DAP](https://developer.arm.com/documentation/101451/0100/About-CMSIS-DAP) standard
* Works with [OpenOCD](https://openocd.org/) and other tools supporting CMSIS-DAP
* Open source, easily upgradeable firmware

| NOTE | For more information on the Raspberry Pi three-pin debug connector see the [specification](https://rptl.io/debug-spec). |
| ------ | ------------------------------------------------------------------------------ |

This makes it easy to use a Raspberry Pi Pico on platforms such as Windows, macOS, and Linux that lack a GPIO header to connect directly to the Pico’s serial UART or SWD port.

### The Debug Probe

The probe operates at 3.3V nominal I/O voltage.

![the probe](https://www.raspberrypi.com/documentation/microcontrollers/images/the-probe.png)

Included with the Debug Probe is a USB power cable and three debug cables:

* three-pin JST-SH connector to 3-pin JST-SH connector cable
* three-pin JST-SH connector to 0.1-inch header (female)
* three-pin JST-SH connector to 0.1-inch header (male)

The two 0.1-inch header cables — intended for breadboard (male) or direct connection to a board with header pins (female) — are coloured as below:

OrangeTX/SC (Output from Probe)

BlackGND

YellowRX/SD (Input to Probe or I/O)

While the cable with three-pin JST-SH connectors is intended to be used with the [standard three-pin connector](https://rptl.io/debug-spec) which newer Raspberry Pi boards use for the SWD debug port and UART connectors.

The Debug Probe has five LEDs, a red LED to indicate power, and four more activity indicator LEDs

![debug leds](https://www.raspberrypi.com/documentation/microcontrollers/images/debug-leds.png?hash=4d2f83f6e80803242416c5b43fe32ae8)

| NOTE | OpenOCD switches both DAP LEDs on when the target is connected, and turns them off when it calls `DAP_DISCONNECT`. |
| ------ | ---------------------------------------------------------------------------------------------------- |

## Getting started

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/microcontrollers/debug-probe/getting-started.adoc)

![labelled wiring](https://www.raspberrypi.com/documentation/microcontrollers/images/labelled-wiring.jpg)

Depending on your setup, there are several ways to wire the Debug Probe to a [Raspberry Pi Pico](https://www.raspberrypi.com/documentation/microcontrollers/raspberry-pi-pico.html). Below, we connect the Debug Probe to a Raspberry Pi Pico H which has the newer three-pin JST-SH connector for SWD.

Connect the following:

* The Debug Probe "D" port to Pico H SWD JST-SH connector
* The Debug Probe "U" port, with the three-pin JST-SH connector to 0.1-inch header (male):

  * Debug Probe `RX` connected to Pico H `TX` pin
  * Debug Probe `TX` connected to Pico H `RX` pin
  * Debug Probe `GND` connected to Pico H `GND` pin

| NOTE | If you have a non-H Pico or Pico W (without a JST-SH connector) you can still connect it to a Debug Probe. Solder a male connector to the `SWCLK`, `GND`, and `SWDIO` header pins on the board. Using the alternate 3-pin JST-SH connector to 0.1-inch header (female) cable included with the Debug Probe, connect to the Debug Probe "D" port. Connect `SWCLK`, `GND`, and `SWDIO` on the Pico or Pico W to the `SC`, `GND`, and `SD` pins on the Debug Probe, respectively. |
| ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

![wiring](https://www.raspberrypi.com/documentation/microcontrollers/images/wiring.png)

## Install tools

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/microcontrollers/debug-probe/installing-tools.adoc)

To use the Debug Probe, install the following tools.

### Install OpenOCD

You need to install OpenOCD.

To install OpenOCD, run the following command in a terminal:

```
$ sudo apt install openocd
```

To run OpenOCD, use the `openocd` command in your terminal.

#### Install OpenOCD on macOS

First, install the [Homebrew](https://brew.sh/) package manager:

```
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

To install OpenOCD on macOS, run the following commands:

```
$ brew install openocd
```

To run OpenOCD, use the `openocd` command in your terminal.

### Install GDB

We also need to install the GNU debugger (GDB).

#### Linux

Install `gdb-multiarch`:

```
$ sudo apt install gdb-multiarch
```

#### macOS

Run the following command to install `gdb`:

```
$ brew install gdb
```

You can safely ignore the request for "special privileges" messages on installation.

| IMPORTANT | GDB does not support `gdb` Arm-based Macs. Instead, either [install ](https://gist.github.com/m0sys/711d0ec5e52102c6ba44451caf38bd38)​[`gdb`](https://gist.github.com/m0sys/711d0ec5e52102c6ba44451caf38bd38)​[ from source](https://gist.github.com/m0sys/711d0ec5e52102c6ba44451caf38bd38) or use `lldb` instead of `gdb`. There is [no official support](https://inbox.sourceware.org/gdb/3185c3b8-8a91-4beb-a5d5-9db6afb93713@Spark/) from the developers for running GDB on Arm-based Macs. Support for GDB can be found on the [GDB mailing list](https://inbox.sourceware.org/gdb/) on Sourceware.org. `lldb` is installed as part of the Xcode Command Line Tools. |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

#### MS Windows

GDB is available as part of our [Pico setup for Windows installer](https://github.com/raspberrypi/pico-setup-windows/releases/latest). It is also included in the [Arm GNU Toolchain Downloads](https://developer.arm.com/downloads/-/arm-gnu-toolchain-downloads).

Alternatively information about manual installation can be found in Chapter 9 and Appendix A of our [Getting Started with Raspberry Pi Pico](https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf) book.

| NOTE | Manual installation of GDB on Windows is not recommended. |
| ------ | ----------------------------------------------------------- |

## Serial Wire Debug (SWD)

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/microcontrollers/debug-probe/swd-connection.adoc)

Serial Wire Debug (SWD) is a two-pin interface ([SWDIO and SWCLK](https://developer.arm.com/documentation/101761/1-0/Debug-and-trace-interface/Serial-Wire-Debug-signals)) alternative to the JTAG four- or five-pin debugging interface standard.

### Uploading new programs to your Pico

The Pico Debug Probe will let you load binaries via the SWD port and OpenOCD: you will not need to unplug, and then push-and-hold, the BOOTSEL button every time you push a new binary to your Pico. Using the Debug Probe uploading new binaries is an entirely hands off affair.

Once you have built a binary:

```
$ sudo openocd -f interface/cmsis-dap.cfg -f target/rp2040.cfg -c "adapter speed 5000" -c "program blink.elf verify reset exit"
```

| NOTE | When you use the Debug Probe to upload a binary the ELF version of the file is used, not the UF2 file that you would use when you drag-and-drop. |
| ------ | -------------------------------------------------------------------------------------------------------------------------------------------------- |

### Debugging with SWD

It’ll also let you use `openocd` in server mode, and connect GDB, which gives you break points and "proper" debugging.

```
$ cd ~/pico/pico-examples/
$ rm -rf build
$ mkdir build
$ cd build
$ export PICO_SDK_PATH=../../pico-sdk
$ cmake -DCMAKE_BUILD_TYPE=Debug ..
$ cd blink
$ make -j4
```

<br /><br />In a debug build you will get more information when you run it under the debugger, as the compiler builds your program with the information to tell GDB what your program is doing.<br /><br />See Chapter 6 of [Getting started with Raspberry Pi Pico](https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf) for more information.

To start an OpenOCD server, run the following command:

```
$ sudo openocd -f interface/cmsis-dap.cfg -f target/rp2040.cfg -c "adapter speed 5000"
```

Then open a second terminal window, switch to the directory containing your built binary, and start a debugger to attach it to the OpenOCD server:

```
$ gdb blink.elf
> target remote localhost:3333
> monitor reset init
> continue
```

GDB doesn’t work on all platforms. Use one of the following alternatives instead of `gdb`, depending on your operating system and device:

* On Linux devices that are *not* Raspberry Pis, use `gdb-multiarch`.
* On Arm-based macOS devices, use `lldb`.

## Serial connections

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/microcontrollers/debug-probe/uart-connection.adoc)

Ensure that the Debug Probe is connected to the UART pins of your Raspberry Pi Pico.

![wiring](https://www.raspberrypi.com/documentation/microcontrollers/images/wiring.png)

The default pins for Raspberry Pi Pico UART0 are as follows:

| Default UART0 | Physical Pin | GPIO Pin |
| --------------- | -------------- | ---------- |
| GND           | 3            | N/A      |
| UART0\_TX  | 1            | GP0      |
| UART0\_RX  | 2            | GP1      |

Once connected, traffic over the Raspberry Pi Pico’s UART will be relayed to your computer by the Debug Probe and exposed as a CDC UART. On a Raspberry Pi this will show up as `/dev/ttyACM0`; on other platforms this serial port will show up differently (e.g. on macOS it will appear as `/dev/cu.usbmodemXXXX`).

If you have not already done so you should install minicom:

```
$ sudo apt install minicom
```

and open the serial port:

```
$ minicom -b 115200 -o -D /dev/ttyACM0
```

| TIP | To exit `minicom`, use CTRL-A followed by X. |
| ----- | ------------------------------------- |

To test serial communication you can build and upload the "Hello World" example application.

Change directory into the `hello_world` directory inside the `pico-examples` tree, and run `make`. Afterwards, you can upload it to your Raspberry Pi Pico using `openocd`. For a full walkthrough of building the `hello_serial` example program, see Chapter 4 of [Getting started with Raspberry Pi Pico](https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf).

```
$ cd pico-examples
$ mkdir build
$ cd build
$ export PICO_SDK_PATH=../../pico-sdk
$ cmake ..
$ cd hello_world/serial
$ make -j4
$ sudo openocd -f interface/cmsis-dap.cfg -f target/rp2040.cfg -c "adapter speed 5000" -c "program hello_serial.elf verify reset exit"
$ minicom -b 115200 -o -D /dev/ttyACM0
```

On opening `minicom` you should see "Hello, world!" printed to the console.

For terminal programs that support it, a description of the USB serial UART is advertised in the USB device description.

![description](https://www.raspberrypi.com/documentation/microcontrollers/images/description.jpg?hash=c86c87f5ca55b3f8baf45709ba83f2d0)

The unique serial number in this description means that on Windows your COM port numbering is "sticky" per device, and will allow you to write `udev` rules to associate a named device node with a particular Debug Probe.

## Updating the firmware on the Debug Probe

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/microcontrollers/debug-probe/updating-firmware.adoc)

Firmware for the Debug Probe is available as a UF2 file distributed by Raspberry Pi.

The latest version of the Debug Probe firmware is version 2. If you’re running an older version, or if you have accidentally overwritten the firmware on your Debug Probe, you can find the latest release of the firmware in [the debugprobe GitHub repository](https://github.com/raspberrypi/debugprobe/releases/latest).

Download `debugprobe.uf2` from the latest release.

Pinch to remove the top of the Debug Probe enclosure.

Push and hold the BOOTSEL button as you plug the Debug Probe into your computer to mount a volume called "RPI-RP2".

Copy `debugprobe.uf2` onto the "RPI-RP2" volume. The volume will dismount automatically after the file finishes copying onto the device.

Your Debug Probe will reboot and now runs an updated version of the Debug Probe firmware. It is now ready for debugging.

## Schematics

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/microcontrollers/debug-probe/schematics.adoc)

Schematics and mechanical drawing of the Debug Probe are available:

* [Schematics](https://datasheets.raspberrypi.com/debug/raspberry-pi-debug-probe-schematics.pdf) (PDF)
* [Mechanical Diagram](https://datasheets.raspberrypi.com/debug/raspberry-pi-debug-probe-mechanical-drawing.pdf) (PDF)

The test point (TP) shown on the schematics are located as shown in the diagram below.

![debug probe tps](https://www.raspberrypi.com/documentation/microcontrollers/images/debug-probe-tps.jpg?hash=a093fce11fd83c5292aec0cd49817c60)
