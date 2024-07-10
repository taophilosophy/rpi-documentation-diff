# The C/C++ SDK

## SDK Setup

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/microcontrollers/c_sdk/sdk_setup.adoc)

For a full walk-through of how to get going with the C/C++ SDK, you should read our '[getting started](https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf)' documentation. However, if you are intending to develop for Pico on a [Raspberry Pi](https://www.raspberrypi.com/documentation/computers/os.html), then you can set up the C/C++ toolchain quickly by running our [setup script](https://raw.githubusercontent.com/raspberrypi/pico-setup/master/pico_setup.sh) from the command line.

| NOTE | You should make sure the OS on your Raspberry Pi is [up to date](https://www.raspberrypi.com/documentation/computers/os.html#update-software) before running the setup script. |
| ------ | --------------------------------------------------------------------------------------- |

## Raspberry Pi Pico C/C++ SDK

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/microcontrollers/c_sdk/official_sdk.adoc)

Our official C SDK can be used from the command line, or from popular integrated development environments like Visual Studio Code, Eclipse, and CLion. To get started, download our C/C++ SDK and Examples, and take a look at our '[getting started](https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf)' documentation to get going. Or for a quick setup see the next section.

* The SDK [Github repository](https://github.com/raspberrypi/pico-sdk)
* The Examples [Github repository](https://github.com/raspberrypi/pico-examples)

You can find documentation around the C/C++ SDK at;

[Getting started with Raspberry Pi Pico](https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf)C/C++ development with Raspberry Pi Pico and other RP2040-based microcontroller boards

[Connecting to the Internet with Raspberry Pi Pico W](https://datasheets.raspberrypi.com/picow/connecting-to-the-internet-with-pico-w.pdf)Getting Raspberry Pi Pico W online with C/C++ or MicroPython

[Raspberry Pi Pico C/C++ SDK](https://datasheets.raspberrypi.com/pico/raspberry-pi-pico-c-sdk.pdf)Libraries and tools for C/C++ development on RP2040 microcontrollers

[API level documentation](https://www.raspberrypi.com/documentation/pico-sdk/index_doxygen.html)Documentation for the Raspberry Pi Pico C/C++ SDK

| NOTE | If you are building applications with the C/C++ SDK and targeting boards other than the Raspberry Pi Pico, you will need to pass `-DPICO_BOARD=boardname` to CMake. Here `boardname` is the name of your board, e.g. for the Adafruit Feather RP2040 you should pass `-DPICO_BOARD=adafruit_feather_rp2040`. See the [`boards/`](https://github.com/raspberrypi/pico-sdk/tree/master/src/boards)​[ directory](https://github.com/raspberrypi/pico-sdk/tree/master/src/boards) in the Raspberry Pi Pico SDK, and the [forums](https://forums.raspberrypi.com/viewtopic.php?f=147&t=304393), for more information. |
| ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |

| NOTE | Documentation introducing working with Wi-Fi and Bluetooth on Raspberry Pi Pico W with C/C++ or MicroPython is presented in the [Connecting to the Internet with Raspberry Pi Pico W](https://datasheets.raspberrypi.com/picow/connecting-to-the-internet-with-pico-w.pdf) book. |
| ------ | ---------------------------------------------------------------------------------------------------------------------------------------- |

| NOTE | If you are building applications with the C/C++ SDK for Raspberry Pi Pico W and, to connect to a network you will need to pass `-DPICO_BOARD=pico_w -DWIFI_SSID="Your Network" -DWIFI_PASSWORD="Your Password"` to CMake. If you only need to enable Bluetooth support then you do not need to pass a SSID and password, but still need to pass the `-DPICO_BOARD=pico_w` string to CMake. |
| ------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

## Your First Binaries

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/microcontrollers/c_sdk/your_first_binary.adoc)

| WARNING | If you are using an Apple Mac, and running macOS Ventura, there has been a change in how the Finder works which causes drag-and-drop to fail. Please see our [blog post](https://www.raspberrypi.com/news/the-ventura-problem/) for a full explanation, and workarounds, and our [Github issue](https://github.com/raspberrypi/pico-sdk/issues/1081) tracking the problem for the current status. |
| --------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

### Blink an LED

The first program anyone writes when using a new microcontroller is to blink an LED on and off. The Raspberry Pi Pico comes with a single LED on-board. The LED is connected to `GP25` on the board’s Raspberry Pi RP2040 for Pico, and `WL_GPIO0` on the Infineon 43439 wireless chip for Pico W.

![Blink an LED 640x360 v2](https://www.raspberrypi.com/documentation/microcontrollers/images/Blink-an-LED-640x360-v2.gif)

You can blink this on and off by,

1. Download the Blink UF2 [for Raspberry Pi Pico](https://datasheets.raspberrypi.com/soft/blink.uf2), or [for Pico W](https://datasheets.raspberrypi.com/soft/blink_picow.uf2).
2. Push and hold the BOOTSEL button and plug your Pico into the USB port of your Raspberry Pi or other computer.
3. It will mount as a Mass Storage Device called RPI-RP2.
4. Drag and drop the Blink UF2 binary onto the RPI-RP2 volume. Pico will reboot.

You should see the on-board LED blinking.

You can see the code on Github for the [Raspberry Pi Pico](https://github.com/raspberrypi/pico-examples/blob/master/blink/blink.c) and [Pico W](https://github.com/raspberrypi/pico-examples/blob/master/pico_w/wifi/blink/picow_blink.c) versions.

### Say "Hello World"

The next program anyone writes is to say 'Hello World' over a USB serial connection.

![Hello World 640x360 v2](https://www.raspberrypi.com/documentation/microcontrollers/images/Hello-World-640x360-v2.gif)

1. Download the [&apos;Hello World&apos; UF2](https://datasheets.raspberrypi.com/soft/hello_world.uf2).
2. Push and hold the BOOTSEL button and plug your Pico into the USB port of your Raspberry Pi or other computer.
3. It will mount as a Mass Storage Device called RPI-RP2.
4. Drag and drop the 'Hello World' UF2 binary onto the RPI-RP2 volume. Pico will reboot.
5. Open a Terminal window and type:

    ```
    $ sudo apt install minicom
    $ minicom -b 115200 -o -D /dev/ttyACM0
    ```

You should see 'Hello, world!' printed to the Terminal.

You can see the code [on Github](https://github.com/raspberrypi/pico-examples/blob/master/hello_world/usb/hello_usb.c)

## Quick-start your own project

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/microcontrollers/c_sdk/quick_start.adoc)

| NOTE | The following instructions are terse, and Linux-based only. For detailed steps, instructions for other platforms, and just in general, we recommend you see the [Getting started with Raspberry Pi Pico](https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf) and [Raspberry Pi Pico C/C++ SDK](https://datasheets.raspberrypi.com/pico/raspberry-pi-pico-c-sdk.pdf) books. |
| ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |

Install CMake (at least version 3.13), and GCC cross compiler

```
$ sudo apt install cmake gcc-arm-none-eabi libnewlib-arm-none-eabi libstdc++-arm-none-eabi-newlib
```

Set up your project to point to use the Raspberry Pi Pico SDK by cloning the SDK locally:

```
$ git clone https://github.com/raspberrypi/pico-sdk.git
```

Copy `external/pico_sdk_import.cmake` from the SDK into your project directory

Set `PICO_SDK_PATH` to the SDK location in your environment, or pass it (`-DPICO_SDK_PATH=`) to `cmake` later.

Setup a `CMakeLists.txt` like:

```
cmake_minimum_required(VERSION 3.13)

# initialize the SDK based on PICO_SDK_PATH
# note: this must happen before project()
include(pico_sdk_import.cmake)

project(my_project)

# initialize the Raspberry Pi Pico SDK
pico_sdk_init()

# rest of your project
```

Go ahead and write your code, see [pico-examples](https://github.com/raspberrypi/pico-examples) or the [Raspberry Pi Pico C/C++ SDK](https://datasheets.raspberrypi.com/pico/raspberry-pi-pico-c-sdk.pdf) book for more information on how to go about that.

About the simplest you can do is a single source file (e.g. `hello_world.c`)

```
#include <stdio.h>
#include "pico/stdlib.h"

int main() {
    setup_default_uart();
    printf("Hello, world!\n");
    return 0;
}
```

and add the following to your CMakeLists.txt:

```
add_executable(hello_world
    hello_world.c
)

# Add pico_stdlib library which aggregates commonly used features
target_link_libraries(hello_world pico_stdlib)

# create map/bin/hex/uf2 file in addition to ELF.
pico_add_extra_outputs(hello_world)
```

| NOTE | This example uses the default UART for stdout; if you want to use the default USB see the hello-usb example. |
| ------ | -------------------------------------------------------------------------------------------------------------- |

Setup a CMake build directory. For example, if not using an IDE:

```
$ mkdir build
$ cd build
$ cmake ..
```

When building for a board other than the Raspberry Pi Pico, you should pass `-DPICO_BOARD=board_name` to the cmake command above, e.g. cmake `-DPICO_BOARD=pico_w ..` to configure the SDK and build options accordingly for that particular board.

Doing so sets up various compiler defines (e.g. default pin numbers for UART and other hardware) and in certain cases also enables the use of additional libraries (e.g. wireless support when building for `PICO_BOARD=pico_w`) which cannot be built without a board which provides the requisite functionality.

For a list of boards defined in the SDK itself, look in [this directory](https://github.com/raspberrypi/pico-sdk/blob/master/src/boards/include/boards) which has a header for each named board.

Make your target from the build directory you created.

```
$ make hello_world
```

You now have `hello_world.elf` to load via a debugger, or `hello_world.uf2` that can be installed and run on your Raspberry Pi Pico via drag and drop.
