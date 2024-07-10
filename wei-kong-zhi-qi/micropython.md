# MicroPython

## What is MicroPython?

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/microcontrollers/micropython/what-is-micropython.adoc)

MicroPython is a full implementation of the Python 3 programming language that runs directly on embedded hardware like Raspberry Pi Pico. You get an interactive prompt (the REPL) to execute commands immediately via USB Serial, and a built-in filesystem. The Pico port of MicroPython includes modules for accessing low-level chip-specific hardware.

* The [MicroPython Wiki](https://github.com/micropython/micropython/wiki)
* The [MicroPython Forums](https://forum.micropython.org/)

## Drag-and-Drop MicroPython

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/microcontrollers/micropython/drag-and-drop.adoc)

You can program your Pico by connecting it to a computer via USB, then dragging and dropping a file onto it so we’ve put together a downloadable UF2 file to let you install MicroPython more easily.

![MicroPython 640x360 v2](https://www.raspberrypi.com/documentation/microcontrollers/images/MicroPython-640x360-v2.gif)

Download the correct MicroPython UF2 file for your board:

* [Raspberry Pi Pico](https://micropython.org/download/rp2-pico/rp2-pico-latest.uf2)
* [Raspberry Pi Pico W](https://micropython.org/download/rp2-pico-w/rp2-pico-w-latest.uf2) with Wi-Fi and Bluetooth LE support

To work with Wi-Fi and Bluetooth on Raspberry Pi Pico W with C/C++ or MicroPython, see the [Connecting to the Internet with Raspberry Pi Pico W](https://datasheets.raspberrypi.com/picow/connecting-to-the-internet-with-pico-w.pdf) book. For details about [supported Bluetooth protocols and profiles](https://github.com/bluekitchen/btstack#supported-protocols-and-profiles), see the Blue Kitchen [BTStack](https://github.com/bluekitchen/btstack) Github repository.

| NOTE | MicroPython distributions for other RP2040-based boards are available on the [MicroPython download page](https://micropython.org/download/). |
| ------ | -------------------------------------------------------------------------------- |

To program your device, follow these steps:

1. Push and hold the BOOTSEL button while connecting your Pico with a USB cable to a computer. Release the BOOTSEL button once your Pico appears as a Mass Storage Device called RPI-RP2.
2. Drag and drop the MicroPython UF2 file onto the RPI-RP2 volume. Your Pico will reboot. You are now running MicroPython.
3. Access the REPL via USB Serial.

The [Raspberry Pi Pico Python SDK](https://datasheets.raspberrypi.com/pico/raspberry-pi-pico-python-sdk.pdf) book contains step-by-step instructions for connecting to your Pico and programming it in MicroPython using both the command line and the [Thonny](https://thonny.org/) IDE.

## Where can I find documentation?

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/microcontrollers/micropython/micropython-documentation.adoc)

You can find information on the MicroPython port to RP2040 at;

[Raspberry Pi Pico Python SDK](https://datasheets.raspberrypi.com/pico/raspberry-pi-pico-python-sdk.pdf)A MicroPython environment for RP2040 microcontrollers

[Connecting to the Internet with Raspberry Pi Pico W](https://datasheets.raspberrypi.com/picow/connecting-to-the-internet-with-pico-w.pdf)Getting Raspberry Pi Pico W online with C/C++ or MicroPython

[RP2 Quick Reference](https://docs.micropython.org/en/latest/rp2/quickref.html)The official documentation around the RP2040 port of MicroPython

[RP2 Library](https://docs.micropython.org/en/latest/library/rp2.html)The official documentation about the `rp2` module in MicroPython

### Further reading

![micropython book](https://www.raspberrypi.com/documentation/microcontrollers/images/micropython_book.png?hash=0cedc967a40584b41bd815d9f3382012)

Check out *[Get Started with MicroPython on Raspberry Pi Pico](https://store.rpipress.cc/collections/getting-started/products/get-started-with-micropython-on-raspberry-pi-pico-2nd-edition)* to learn how your Pico can interact with the world around it using the MicroPython programming language. Fully updated for Raspberry Pi Pico W and the latest version of MicroPython, this book shows you how to:

* set up your Pico or Pico W and start using it
* start writing programs using MicroPython
* control and sense electronic components
* discover how to use Pico’s unique Programmable IO
* turn Raspberry Pi Pico W into a network-connected node for the Internet of Things
* link your Pico W to your smartphone, tablet, or another Pico W with Bluetooth Low Energy (BLE)

## Which hardware am I running on?

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/microcontrollers/micropython/what-board.adoc)

There is no direct method for software written in MicroPython to discover whether it is running on a Raspberry Pi Pico or a Pico W by looking at the hardware. However, you can tell indirectly by looking to see if network functionality is included in your particular MicroPython firmware:

```
import network
if hasattr(network, "WLAN"):
   # the board has WLAN capabilities
```

Alternatively, you can inspect the MicroPython firmware version to check whether it was compiled for Raspberry Pi Pico or for Pico W using the `sys` module.

```
>>> import sys
>>> sys.implementation
(name='micropython', version=(1, 19, 1), _machine='Raspberry Pi Pico W with RP2040', _mpy=4102)
```

If the 'Pico W' string is present and in `sys.implementation._machine`, your firmware was compiled for Pico W.
