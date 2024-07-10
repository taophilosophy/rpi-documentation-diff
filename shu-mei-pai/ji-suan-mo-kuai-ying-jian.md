# Compute Module hardware

## Compute Modules

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/computers/compute-module/introduction.adoc)

Raspberry Pi Compute Modules are **system-on-module** variants of the flagship Raspberry Pi models. Compute Modules are especially popular for industrial and commercial applications, including digital signage, thin clients, and process automation. Some of these applications use the flagship Raspberry Pi design, but many users want a more compact design or on-board eMMC storage.

Compute Modules come in multiple variants, varying both in memory and embedded Multi-Media Card (eMMC) flash storage capacity. The eMMC is similar to an SD card, but soldered onto the board. Unlike SD cards, eMMC is specifically designed to be used as a disk and includes extra features to improve reliability. **Lite** models have no on-board storage, and are sometimes referred to with the shorthand suffix **L**, e.g. "CM3L".

Compute Modules use the following Raspberry Pi SoCs:

* BCM2835 for CM1
* BCM2837 for CM3, CM3+
* BCM2711 for CM4, CM4S

### Compute Module 4

The latest version of the Compute Module is the Compute Module 4 (CM4). We recommend CM4 for all future development.

![Compute Module 4](https://www.raspberrypi.com/documentation/computers/images/cm4.jpg?hash=989dcf3efb7c9d59f463fe404a5e3820)

Compute Module 4

The Compute Module 4 (CM4) contains the internals of a Raspberry Pi 4 (the BCM2711 processor and 1GB, 2GB, 4GB, or 8GB of RAM) as well as an optional 0GB (Lite), 8GB, 16GB or 32GB of eMMC flash storage.

Unlike CM1, CM3, and CM3+, CM4 does not use the DDR2 SO-DIMM form factor. Instead, CM4 uses two 100-pin high density connectors in a smaller physical footprint. This change helped add the following interfaces:

* an additional second HDMI port
* PCIe
* Ethernet

The previous form factor could not have supported these interfaces.

### Compute Module 4S

![Compute Module 4S](https://www.raspberrypi.com/documentation/computers/images/cm4s.jpg?hash=4ec9821548515598adfe5a3cdc14789d)

Compute Module 4S

The Compute Module 4S (CM4S) contains the internals of a Raspberry Pi 4 (the BCM2711 processor and 1GB, 2GB, 4GB, or 8GB of RAM) as well as an optional 0GB (Lite), 8GB, 16GB or 32GB of eMMC flash storage. Unlike CM4, CM4S comes in same the DDR2 SO-DIMM form factor as CM1, CM3, and CM3+.

### Compute Module 3+

![Compute Module 3+](https://www.raspberrypi.com/documentation/computers/images/cm3-plus.jpg?hash=352ed6d3402586078299193abe8ba754)

Compute Module 3+

The Compute Module 3+ (CM3+) contains the internals of a Raspberry Pi 3 Model B+ (the BCM2837 processor and 1GB of RAM) as well as an optional 0GB (Lite), 8GB, 16GB or 32GB of eMMC flash storage.

### Compute Module 3

![Compute Module 3](https://www.raspberrypi.com/documentation/computers/images/cm3.jpg?hash=3a5ff7c853190d7a07c51bf67c1082b8)

Compute Module 3

The Compute Module 3 (CM3) contains the internals of a Raspberry Pi 3 (the BCM2837 processor and 1GB of RAM) as well as an optional 4GB of eMMC flash storage.

### Compute Module 1

![Compute Module 1](https://www.raspberrypi.com/documentation/computers/images/cm1.jpg?hash=725d6ee61d958098dc68dc7739deab88)

Compute Module 1

The Compute Module 1 (CM1) contains the internals of a Raspberry Pi (the BCM2835 processor and 512MB of RAM) as well as an optional 4GB of eMMC flash storage.

## IO Boards

Raspberry Pi IO Boards provide a way to connect a single Compute Module to a variety of I/O (input/output) interfaces. Compute Modules are, by nature, small. As a result, they lack ports and connectors. IO Boards provide a way to connect Compute Modules to a variety of peripherals.

IO Boards are breakout boards intended for development; in production, you should use a smaller, potentially custom board that provides only the ports and peripherals required for your use-case.

### Compute Module 4 IO Board

![Compute Module 4 IO Board](https://www.raspberrypi.com/documentation/computers/images/cm4io.jpg?hash=a69dcc715bfcacfd6dccc10c8d4922c2)

Compute Module 4 IO Board

Compute Module 4 IO Board provides the following interfaces:

* HAT footprint with 40-pin GPIO connector and PoE header
* Two HDMI ports
* Two USB 2.0 ports
* Gigabit Ethernet RJ45 with PoE support
* MicroSD card slot (only for use with Lite variants with no eMMC)
* PCIe Gen 2 socket
* 12V input via barrel jack (supports up to 26V if PCIe unused)
* 2 x MIPI DSI display FPC connectors (22-pin 0.5 mm pitch cable)
* 2 x MIPI CSI-2 camera FPC connectors (22-pin 0.5 mm pitch cable)
* Real-time clock with battery socket

### Compute Module IO Board

![Compute Module IO Board](https://www.raspberrypi.com/documentation/computers/images/cmio.jpg?hash=a6e2d5cd1e8845e0925ed00c15aef6a9)

Compute Module IO Board

Compute Module IO Board provides the following interfaces:

* 120 GPIO pins
* an HDMI port
* a USB-A port
* 2 x MIPI DSI display FPC connectors (22-pin 0.5 mm pitch cable)
* 2 x MIPI CSI-2 camera FPC connectors (22-pin 0.5 mm pitch cable)

The Compute Module IO Board comes in two variants: Version 1 and Version 3. Version 1 is only compatible with CM1. Version 3 is compatible with CM1, CM3, CM3+, and CM4S. Compute Module IO Board Version 3 is sometimes written as the shorthand CMIO3.

Compute Module IO Board Version 3 added a microSD card slot that did not exist in Compute Module IO Board Version 1.

### IO Board compatibility

Not all Compute Module IO Boards work with all Compute Module models. The following table shows which Compute Modules work with each IO Board:

| IO Board                                         | Compatible Compute Modules |
| -------------------------------------------------- | ---------------------------- |
| Compute Module IO Board Version 1 (CMIO)/(CMIO1) | * CM1                      |
| Compute Module IO Board Version 3 (CMIO)/(CMIO3) | * CM1* CM3* CM3+* CM4S     |
| Compute Module 4 IO Board (CM4IO)                | * CM4                      |

## Flash an image to a Compute Module

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/computers/compute-module/cm-emmc-flashing.adoc)

The Compute Module has an on-board eMMC device connected to the primary SD card interface. This guide explains how to flash (write) an operating system image to the eMMC storage of a single Compute Module.

| NOTE | **Lite** variants of Compute Modules do not have on-board eMMC. Instead, you can follow the procedure to flash a storage device for other Raspberry Pi devices at [Install an operating system](https://www.raspberrypi.com/documentation/computers/getting-started.html#installing-the-operating-system). |
| ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |

When flashing an image to multiple Compute Modules, consider using the Compute Module Provisioner instead:

##### [Mass Provision with the Compute Module Provisioner](https://pip.raspberrypi.com/categories/685-whitepapers-app-notes/documents/RP-003468-WP/Using-the-Compute-Module-Provisioner.pdf)

Mass Provision with the Compute Module Provisioner

The Compute Module Provisioner is a web application that helps developers program many Compute Module devices simultaneously.

It provides a database of kernel images and the ability to run scripts during the flashing process, in addition to automated label printing and firmware updating.

### Prerequisites

To flash the Compute Module eMMC, you need the following:

* Another computer, referred to in this guide as the **host device**. You can use Linux (Raspberry Pi OS or Ubuntu), Windows, or macOS.
* The Compute Module IO Board [that corresponds to your Compute Module model](https://www.raspberrypi.com/documentation/computers/compute-module.html#io-board-compatibility).
* A micro USB cable.

### Set up the IO Board

To begin, physically set up your IO Board. This includes connecting the Compute Module and host device to the IO Board.

#### with Compute Module 4 IO Board

To set up the Compute Module 4 IO Board:

1. Connect the Compute Module to the IO board. When connected, the Compute Module should lie flat.
2. Fit `nRPI_BOOT` to J2 (`disable eMMC Boot`) on the IO board jumper.
3. Connect a cable from micro USB slave port J11 on the IO board to the host device.

#### with Compute Module IO Board

To set up the Compute Module IO Board:

1. Connect the Compute Module to the IO board. When connected, the Compute Module should lie parallel to the board, with the engagement clips firmly clicked into place.
2. Set J4 (`USB SLAVE BOOT ENABLE`) to 1-2 = (`USB BOOT ENABLED`)
3. Connect a cable from micro USB slave port J15 on the IO board to the host device.

### Set up the host device

Next, let’s set up software on the host device.

#### on Linux

To set up software on a Linux host device:

1. Run the following command to install `rpiboot`:

    ```
    $ sudo apt install rpiboot
    ```
2. Connect the IO Board to power.
3. Then, run `rpiboot`:

    ```
    $ sudo rpiboot
    ```
4. After a few seconds, the Compute Module should appear as a mass storage device. Check the `/dev/` directory, likely `/dev/sda` or `/dev/sdb`, for the device. Alternatively, run `lsblk` and search for a device with a storage capacity that matches the capacity of your Compute Module.

| TIP | Alternatively, you can [build ](https://github.com/raspberrypi/usbboot)​[`rpiboot`](https://github.com/raspberrypi/usbboot)​[ from source](https://github.com/raspberrypi/usbboot). |
| ----- | -------------------------- |

#### on macOS

To set up software on a macOS host device:

1. First, [build ](https://github.com/raspberrypi/usbboot?tab=readme-ov-file#macos)​[`rpiboot`](https://github.com/raspberrypi/usbboot?tab=readme-ov-file#macos)​[ from source](https://github.com/raspberrypi/usbboot?tab=readme-ov-file#macos).
2. Connect the IO Board to power.
3. Then, run the `rpiboot` executable with the following command:

    ```
    $ sudo ./rpiboot
    ```
4. When the command finishes running, you should see a message stating "The disk you inserted was not readable by this computer." Click **Ignore**. Your Compute Module should now appear as a mass storage device.

#### on Windows

To set up software on a Windows host device:

1. Download the [Windows installer](https://github.com/raspberrypi/usbboot/raw/master/win32/rpiboot_setup.exe)
2. Double-click on the installer to run it. This installs the drivers and boot tool.
3. Connect the IO Board to power. Windows should discover the hardware and configure the required drivers.
4. Double-click on `RPiBoot.exe` to run it. After a few seconds, the Compute Module eMMC should appear as a USB mass storage device.

| TIP | Alternatively, you can [build ](https://github.com/raspberrypi/usbboot)​[`rpiboot`](https://github.com/raspberrypi/usbboot)​[ from source](https://github.com/raspberrypi/usbboot). |
| ----- | -------------------------- |

### Flash the eMMC

You can use [Raspberry Pi Imager](https://www.raspberrypi.com/documentation/computers/getting-started.html#raspberry-pi-imager) to flash an operating system image to a Compute Module.

Alternatively, use `dd` to write a raw OS image (such as [Raspberry Pi OS](https://www.raspberrypi.com/documentation/computers/os.html#introduction)) to your Compute Module. Run the following command, replacing `/dev/sdX` with the path to the mass storage device representation of your Compute Module and `raw_os_image.img` with the path to your raw OS image:

```
$ sudo dd if=raw_os_image.img of=/dev/sdX bs=4MiB
```

Once the image has been written, disconnect and reconnect the Compute Module. You should now see two partitions (for Raspberry Pi OS):

```
/dev/sdX    <- Device
/dev/sdX1   <- First partition (FAT)
/dev/sdX2   <- Second partition (Linux filesystem)
```

You can mount the `/dev/sdX1` and `/dev/sdX2` partitions normally.

### Boot from eMMC

#### with Compute Module 4 IO Board

Disconnect `nRPI_BOOT` from J2 (`disable eMMC Boot`) on the IO board jumper.

#### with Compute Module IO Board

Set J4 (`USB SLAVE BOOT ENABLE`) to 2-3 (`USB BOOT DISABLED`).

#### Boot

Disconnect the USB slave port. Power-cycle the IO board to boot the Compute Module from the new image you just wrote to eMMC.

### Known issues

* A small percentage of CM3 experienced booting problems. We have traced these back to the method used to create the FAT32 partition; we believe the problem is due to a difference in timing between the CPU and eMMC. If you have trouble booting your CM3, create the partitions manually with the following commands:

  ```
  $ sudo parted /dev/<device>
  (parted) mkpart primary fat32 4MiB 64MiB
  (parted) q
  $ sudo mkfs.vfat -F32 /dev/<device>
  $ sudo cp -r <files>/* <mountpoint>
  ```
* The CM1 bootloader returns a slightly incorrect USB packet to the host. Most USB hosts ignore it, but some USB ports don’t work due to this bug. CM3 fixed this bug.

## Compute Module EEPROM bootloader

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/computers/compute-module/cm-bootloader.adoc)

Since Compute Module 4, Compute Modules use an EEPROM bootloader. This bootloader lives in a small segment of on-board storage instead of the boot partition. As a result, it requires different procedures to update. Before using a Compute Module with an EEPROM bootloader in production, always follow these best practices:

* Select a specific bootloader release. Verify that every Compute Module you use has that release. The version in the `usbboot` repo is always a recent stable release.
* Configure the boot device by [setting the ](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#raspberry-pi-bootloader-configuration)​[`BOOT\_ORDER`](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#raspberry-pi-bootloader-configuration)​[ ](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#raspberry-pi-bootloader-configuration).
* Enable hardware write-protection on the bootloader EEPROM to ensure that the bootloader can’t be modified on inaccessible products (such as remote or embedded devices).

### Flash Compute Module bootloader EEPROM

To flash the bootloader EEPROM:

1. Set up the hardware as you would when [flashing the eMMC](https://www.raspberrypi.com/documentation/computers/compute-module.html#flash-compute-module-emmc), but ensure `EEPROM_nWP` is *not* pulled low.
2. Run the following command to write `recovery/pieeprom.bin` to the bootloader EEPROM:

    ```
    $ ./rpiboot -d recovery
    ```
3. Once complete, `EEPROM_nWP` may be pulled low again.

### Flash storage devices other than SD cards

The Linux-based [`mass-storage-gadget`](https://github.com/raspberrypi/usbboot/blob/master/mass-storage-gadget/README.md) supports flashing of NVMe, eMMC and USB block devices. `mass-storage-gadget` writes devices faster than the firmware-based `rpiboot` mechanism, and also provides a UART console to the device for debugging.

`usbboot` also includes a number of [extensions](https://github.com/raspberrypi/usbboot/blob/master/Readme.md#compute-module-4-extensions) that enable you to interact with the EEPROM bootloader on a Compute Module.

### Update the Compute Module bootloader

On Compute Modules with an EEPROM bootloader, ROM never runs `recovery.bin` from SD/eMMC. These Compute Modules disable the `rpi-eeprom-update` service by default, because eMMC is not removable and an invalid `recovery.bin` file could prevent the system from booting.

You can override this behaviour with `self-update` mode. In `self-update` mode, you can update the bootloader from USB MSD or network boot.

| WARNING | `self-update` mode does not update the bootloader atomically. If a power failure occurs during an EEPROM update, you could corrupt the EEPROM. |
| --------- | ----------------------------------------------------------------------------------------------------------------------------------- |

### Modify the bootloader configuration

To modify the Compute Module EEPROM bootloader configuration:

1. Navigate to the `usbboot/recovery` directory.
2. If you require a specific bootloader release, replace `pieeprom.original.bin` with the equivalent from your bootloader release.
3. Edit the default `boot.conf` bootloader configuration file to define a [`BOOT\_ORDER`](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#BOOT_ORDER):

    * For network boot, use `BOOT_ORDER=0xf2`.
    * For SD/eMMC boot, use `BOOT_ORDER=0xf1`.
    * For USB boot failing over to eMMC, use `BOOT_ORDER=0xf15`.
    * For NVMe boot, use `BOOT_ORDER=0xf6`.
4. Run `./update-pieeprom.sh` to generate a new EEPROM image `pieeprom.bin` image file.
5. If you require EEPROM write-protection, add `eeprom_write_protect=1` to `/boot/firmware/config.txt`.

    * Once enabled in software, you can lock hardware write-protection by pulling the `EEPROM_nWP` pin low.
6. Run the following command to write the updated `pieeprom.bin` image to EEPROM:

    ```
    $ ../rpiboot -d .
    ```

## Wire peripherals

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/computers/compute-module/cm-peri-sw-guide.adoc)

This guide helps developers wire up peripherals to the Compute Module pins. Additionally, this guide explains how to make changes to the software to enable these peripherals.

Most of the pins of the SoC (GPIO, two CSI camera interfaces, two DSI display interfaces, HDMI, etc.) are available for wiring. You can can usually leave unused pins disconnected.

Compute Modules with the DDR2 SODIMM form factor can use any DDR2 SODIMM socket. However, the pinout is not the same as SODIMM memory modules.

To use a Compute Module, a user must design a motherboard that:

* provides power to the Compute Module (3.3V and 1.8V at minimum)
* connects the pins to the required peripherals for the user’s application

Raspberry Pi’s IO Boards provide the following functionality:

* powers the module
* wires the GPIO to pin headers
* wires the camera and display interfaces to FFC connectors
* wires HDMI to an HDMI port
* wires USB to USB ports
* wires activity monitoring to an 'ACT' LED
* eMMC programming over USB

This guide first explains the boot process and how Device Tree describes attached hardware.

Then, we’ll explain how to attach an I2C and an SPI peripheral to an IO Board. Finally, we’ll create the Device Tree files necessary to use both peripherals with Raspberry Pi OS.

### BCM283x GPIOs

BCM283x has three banks of general-purpose input/output (GPIO) pins: 28 pins on Bank 0, 18 pins on Bank 1, and 8 pins on Bank 2, for a total of 54 pins. These pins can be used as true GPIO pins: software can set them as inputs or outputs, read and/or set state, and use them as interrupts. They also can run alternate functions such as I2C, SPI, I2S, UART, SD card, and others.

You can use Bank 0 or Bank 1 on any Compute Module. Don’t use Bank 2: it controls eMMC, HDMI hot plug detect, and ACT LED/USB boot control.

Use `pinctrl` to check the voltage and function of the GPIO pins to see if your Device Tree is working as expected.

### BCM283x boot process

BCM283x devices have a VideoCore GPU and Arm CPU cores. The GPU consists of a DSP processor and hardware accelerators for imaging, video encode and decode, 3D graphics, and image compositing.

In BCM283x devices, the DSP core in the GPU boots first. It handles setup before booting up the main Arm processors.

Raspberry Pi BCM283x devices have a three-stage boot process:

* The GPU DSP comes out of reset and executes code from the small internal boot ROM. This code loads a second-stage bootloader via an external interface. This code first looks for a second-stage boot loader on the boot device called `bootcode.bin` on the boot partition. If no boot device is found or `bootcode.bin` is not found, the boot ROM waits in USB boot mode for a host to provide a second-stage boot loader (`usbbootcode.bin`).
* The second-stage boot loader is responsible for setting up the LPDDR2 SDRAM interface and other critical system functions. Once set up, the second-stage boot loader loads and executes the main GPU firmware (`start.elf`).
* `start.elf` handles additional system setup and boots up the Arm processor subsystem. It contains the GPU firmware. The GPU firmware first reads `dt-blob.bin` to determine initial GPIO pin states and GPU-specific interfaces and clocks, then parses `config.txt`. It then loads a model-specific Arm device tree file and any Device Tree overlays specified in `config.txt` before starting the Arm subsystem and passing the Device Tree data to the booting Linux kernel.

### Device Tree

[Linux Device Tree for Raspberry Pi](https://www.raspberrypi.com/documentation/computers/configuration.html#device-trees-overlays-and-parameters) encodes information about hardware attached to a system as well as the drivers used to communicate with that hardware.

The boot partition contains several binary Device Tree (`.dtb`) files. The Device Tree compiler creates these binary files using human-readable Device Tree descriptions (`.dts`).

The boot partition contains two different types of Device Tree files. One is used by the GPU only; the rest are standard Arm Device Tree files for each of the BCM283x-based Raspberry Pi products:

* `dt-blob.bin` (used by the GPU)
* `bcm2708-rpi-b.dtb` (Used for Raspberry Pi 1 Models A and B)
* `bcm2708-rpi-b-plus.dtb` (Used for Raspberry Pi 1 Models B+ and A+)
* `bcm2709-rpi-2-b.dtb` (Used for Raspberry Pi 2 Model B)
* `bcm2710-rpi-3-b.dtb` (Used for Raspberry Pi 3 Model B)
* `bcm2708-rpi-cm.dtb` (Used for Raspberry Pi Compute Module 1)
* `bcm2710-rpi-cm3.dtb` (Used for Raspberry Pi Compute Module 3)

During boot, the user can specify a specific Arm Device Tree to use via the `device_tree` parameter in `config.txt`. For example, the line `device_tree=mydt.dtb` in `config.txt` specifies an Arm Device Tree in a file named `mydt.dtb`.

You can create a full Device Tree for a Compute Module product, but we recommend using **overlays** instead. Overlays add descriptions of non-board-specific hardware to the base Device Tree. This includes GPIO pins used and their function, as well as the devices attached, so that the correct drivers can be loaded. The bootloader merges overlays with the base Device Tree before passing the Device Tree to the Linux kernel. Occasionally the base Device Tree changes, usually in a way that will not break overlays.

Use the `dtoverlay` parameter in `config.txt` to load Device Tree overlays. Raspberry Pi OS assumes that all overlays are located in the `/overlays` directory and use the suffix `-overlay.dtb`. For example, the line `dtoverlay=myoverlay` loads the overlay `/overlays/myoverlay-overlay.dtb`.

To wire peripherals to a Compute Module, describe all hardware attached to the Bank 0 and Bank 1 GPIOs in an overlay. This allows you to use standard Raspberry Pi OS images, since the overlay is merged into the standard base Device Tree. Alternatively, you can define a custom Device Tree for your application, but you won’t be able to use standard Raspberry Pi OS images. Instead, you must create a modified Raspberry Pi OS image that includes your custom device tree for every OS update you wish to distribute. If the base overlay changes, you might need to update your customised Device Tree.

### `dt-blob.bin`

When `start.elf` runs, it first reads `dt-blob.bin`. This is a special form of Device Tree blob which tells the GPU how to set up the GPIO pin states.

`dt-blob.bin` contains information about GPIOs and peripherals controlled by the GPU, instead of the SoC. For example, the GPU manages Camera Modules. The GPU needs exclusive access to an I2C interface and a couple of pins to talk to a Camera Module.

On most Raspberry Pi models, I2C0 is reserved for exclusive GPU use. `dt-blob.bin` defines the GPIO pins used for I2C0.

By default, `dt-blob.bin` does not exist. Instead, `start.elf` includes a built-in version of the file. Many Compute Module projects provide a custom `dt-blob.bin` which overrides the default built-in file.

`dt-blob.bin` specifies:

* the pin used for HDMI hot plug detect
* GPIO pins used as a GPCLK output
* an ACT LED that the GPU can use while booting

[`minimal-cm-dt-blob.dts`](https://datasheets.raspberrypi.com/cm/minimal-cm-dt-blob.dts) is an example `.dts` device tree file. It sets up HDMI hot plug detection, an ACT LED, and sets all other GPIOs as inputs with default pulls.

To compile `minimal-cm-dt-blob.dts` to `dt-blob.bin`, use the [Device Tree compiler](https://www.raspberrypi.com/documentation/computers/configuration.html#device-trees-overlays-and-parameters) `dtc`. To install `dtc` on a Raspberry Pi, run the following command:

```
$ sudo apt install device-tree-compiler
```

Then, run the follow command to compile `minimal-cm-dt-blob.dts` into `dt-blob.bin`:

```
$ dtc -I dts -O dtb -o dt-blob.bin minimal-cm-dt-blob.dts
```

For more information, see our [guide to creating ](https://www.raspberrypi.com/documentation/computers/configuration.html#change-the-default-pin-configuration)​[`dt-blob.bin`](https://www.raspberrypi.com/documentation/computers/configuration.html#change-the-default-pin-configuration).

### Arm Linux Device Tree

After `start.elf` reads `dt-blob.bin` and sets up the initial pin states and clocks, it reads [`config.txt`](https://www.raspberrypi.com/documentation/computers/config_txt.html), which contains many other options for system setup.

After reading `config.txt`, `start.elf` reads a model-specific Device Tree file. For instance, Compute Module 3 uses `bcm2710-rpi-cm.dtb`. This file is a standard Arm Linux Device Tree file that details hardware attached to the processor. It enumerates:

* what and where peripheral devices exist
* which GPIOs are used
* what functions those GPIOs have
* what physical devices are connected

This file sets up the GPIOs by overwriting the pin state in `dt-blob.bin` if it is different. It will also try to load drivers for the specific devices.

The model-specific Device Tree file contains disabled entries for peripherals. It contains no GPIO pin definitions other than the eMMC/SD Card peripheral which has GPIO defs and always uses the same pins.

### Device Tree source and compilation

The Raspberry Pi OS image provides compiled `dtb` files, but the source `dts` files live in the [Raspberry Pi Linux kernel branch](https://github.com/raspberrypi/linux/tree/rpi-6.6.y/arch/arm/boot/dts/broadcom). Look for `rpi` in the file names.

Default overlay `dts` files live at [`arch/arm/boot/dts/overlays`](https://github.com/raspberrypi/linux/tree/rpi-6.6.y/arch/arm/boot/dts/overlays). These overlay files are a good starting point for creating your own overlays. To compile these `dts` files to `dtb` files, use the [Device Tree compiler](https://www.raspberrypi.com/documentation/computers/configuration.html#device-trees-overlays-and-parameters) `dtc`.

When building your own kernel, the build host requires the Device Tree compiler in `scripts/dtc`. To build your overlays automatically, add them to the `dtbs` make target in `arch/arm/boot/dts/overlays/Makefile`.

### Device Tree debugging

When booting the Linux kernel, the GPU provides a fully assembled Device Tree created using the base `dts` and any overlays. This full tree is available via the Linux `proc` interface in `/proc/device-tree`. Nodes become directories and properties become files.

You can use `dtc` to write this out as a human readable `dts` file for debugging. To see the fully assembled device tree, run the following command:

```
$ dtc -I fs -O dts -o proc-dt.dts /proc/device-tree
```

`pinctrl` provides the status of the GPIO pins. If something seems to be going awry, try dumping the GPU log messages:

```
$ sudo vclog --msg
```

| TIP | To include even more diagnostics in the output, add `dtdebug=1` to `config.txt`. |
| ----- | ----------------------------------------------------------- |

Use the [Device Tree Raspberry Pi forum](https://forums.raspberrypi.com/viewforum.php?f=107) to ask Device Tree-related questions or report an issue.

### Examples

The following examples use an IO Board with peripherals attached via jumper wires. We assume a CM1+CMIO or CM3+CMIO3, running a clean install of Raspberry Pi OS Lite. The examples here require internet connectivity, so we recommend a USB hub, keyboard, and wireless LAN or Ethernet dongle plugged into the IO Board USB port.

#### Attach an I2C RTC to Bank 1 pins

In this example, we wire an NXP PCF8523 real time clock (RTC) to the IO Board Bank 1 GPIO pins: 3V3, GND, I2C1_SDA on GPIO44 and I2C1_SCL on GPIO45.

Download [`minimal-cm-dt-blob.dts`](https://datasheets.raspberrypi.com/cm/minimal-cm-dt-blob.dts) and copy it to the boot partition in `/boot/firmware/`.

Edit `minimal-cm-dt-blob.dts` and change the pin states of GPIO44 and 45 to be I2C1 with pull-ups:

```
$ sudo nano /boot/firmware/minimal-cm-dt-blob.dts
```

Replace the following lines:

```
pin@p44 { function = "input"; termination = "pull_down"; }; // DEFAULT STATE WAS INPUT NO PULL
pin@p45 { function = "input"; termination = "pull_down"; }; // DEFAULT STATE WAS INPUT NO PULL
```

With the following pull-up definitions:

```
pin@p44 { function = "i2c1"; termination = "pull_up"; }; // SDA1
pin@p45 { function = "i2c1"; termination = "pull_up"; }; // SCL1
```

We could use this `dt-blob.dts` with no changes, because the Linux Device Tree re-configures these pins during Linux kernel boot when the specific drivers load. However, if you configure `dt-blob.dts`, the GPIOs reach their final state as soon as possible during the GPU boot stage. In some cases, pins must be configured at GPU boot time so they are in a specific state when Linux drivers are loaded. For example, a reset line may need to be held in the correct orientation.

Run the following command to compile `dt-blob.bin`:

```
$ sudo dtc -I dts -O dtb -o /boot/firmware/dt-blob.bin /boot/firmware/minimal-cm-dt-blob.dts
```

Download [`example1-overlay.dts`](https://datasheets.raspberrypi.com/cm/example1-overlay.dts), copy it to the boot partition in `/boot/firmware/`, then compile it with the following command:

```
$ sudo dtc -@ -I dts -O dtb -o /boot/firmware/overlays/example1.dtbo /boot/firmware/example1-overlay.dts
```

The `-@` flag compiles `dts` files with external references. It is usually necessary.

Add the following line to [`/boot/firmware/config.txt`](https://www.raspberrypi.com/documentation/computers/config_txt.html#what-is-config-txt):

```
dtoverlay=example1
```

Finally, reboot with `sudo reboot`.

Once rebooted, you should see an `rtc0` entry in `/dev`. Run the following command to view the hardware clock time:

```
$ sudo hwclock
```

#### Attach an ENC28J60 SPI Ethernet controller on Bank 0

In this example, we use an overlay already defined in `/boot/firmware/overlays` to add an ENC28J60 SPI Ethernet controller to Bank 0. The Ethernet controller uses SPI pins CE0, MISO, MOSI and SCLK (GPIO8-11 respectively), GPIO25 for a falling edge interrupt, in addition to GND and 3.3V.

In this example, we won’t change `dt-blob.bin`. Instead, add the following line to `/boot/firmware/config.txt`:

```
dtoverlay=enc28j60
```

Reboot with `sudo reboot`.

You should now see an `rtc0` entry in `/dev`. Run the following command to view the hardware clock time:

```
$ sudo hwclock
```

You should also have Ethernet connectivity. Run the following command to test your connectivity:

```
$ ping 8.8.8.8
```

Run the following command to show GPIO functions; GPIO8-11 should now provide ALT0 (SPI) functions:

```
$ pinctrl
```

## Attach a Camera Module

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/computers/compute-module/cmio-camera.adoc)

The Compute Module has two CSI-2 camera interfaces: CAM1 and CAM0. This section explains how to connect one or two Raspberry Pi Cameras to a Compute Module using the CAM1 and CAM0 interfaces with a Compute Module I/O Board.

### Update your system

Before configuring a camera, [ensure that your Raspberry Pi firmware is up-to-date](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#update-the-bootloader-configuration).:

```
$ sudo apt update
$ sudo apt full-upgrade
```

### Connect one camera

To connect a single camera to a Compute Module, complete the following steps:

1. Disconnect the Compute Module from power.
2. Connect the Camera Module to the CAM1 port using a RPI-CAMERA board or a Raspberry Pi Zero camera cable.
    ![Connecting the adapter board](https://www.raspberrypi.com/documentation/computers/images/CMIO-Cam-Adapter.jpg?hash=e283b8867e93491c0a21b11de82c84e4)
3. *(CM1, CM3, CM3+, and CM4S only)* : Connect the following GPIO pins with jumper cables:

    * `0` to `CD1_SDA`
    * `1` to `CD1_SCL`
    * `2` to `CAM1_I01`
    * `3` to `CAM1_I00`
      ![GPIO connection for a single camera](https://www.raspberrypi.com/documentation/computers/images/CMIO-Cam-GPIO.jpg?hash=6918226529340146f2468d25027df9f0)
4. Reconnect the Compute Module to power.
5. Remove (or comment out with the prefix `#`) the following lines, if they exist, in `/boot/firmware/config.txt`:

    ```
    camera_auto_detect=1
    ```

    ```
    dtparam=i2c_arm=on
    ```
6.  *(CM1, CM3, CM3+, and CM4S only)* : Add the following directive to `/boot/firmware/config.txt` to accommodate the swapped GPIO pin assignment on the I/O board:

    ```
    dtoverlay=cm-swap-i2c0
    ```
7.  *(CM1, CM3, CM3+, and CM4S only)* : Add the following directive to `/boot/firmware/config.txt` to assign GPIO 3 as the CAM1 regulator:

    ```
    dtparam=cam1_reg
    ```
8. | Add the appropriate directive to `/boot/firmware/config.txt` to manually configure the driver for your camera model: |  |
    | camera model | directive |
    | ------------------------------------------------------------------------------------------- | -- |
    | v1 camera                                                                                 | `dtoverlay=ov5647,cam1` |
    | v2 camera                                                                                 | `dtoverlay=imx219,cam1` |
    | v3 camera                                                                                 | `dtoverlay=imx708,cam1` |
    | HQ camera                                                                                 | `dtoverlay=imx477,cam1` |
    | GS camera                                                                                 | `dtoverlay=imx296,cam1` |
9. Reboot your Compute Module with `sudo reboot`.
10. Run the following command to check the list of detected cameras:

     ```
     $ rpicam-hello --list
     ```

     You should see your camera model, referred to by the driver directive in the table above, in the output.

### Connect two cameras

To connect two cameras to a Compute Module, complete the following steps:

1. Follow the single camera instructions above.
2. Disconnect the Compute Module from power.
3. Connect the Camera Module to the CAM0 port using a RPI-CAMERA board or a Raspberry Pi Zero camera cable.
    ![Connect the adapter board](https://www.raspberrypi.com/documentation/computers/images/CMIO-Cam-Adapter.jpg?hash=e283b8867e93491c0a21b11de82c84e4)
4. *(CM1, CM3, CM3+, and CM4S only)* : Connect the following GPIO pins with jumper cables:

    * `28` to `CD0_SDA`
    * `29` to `CD0_SCL`
    * `30` to `CAM0_I01`
    * `31` to `CAM0_I00`
      ![GPIO connection with additional camera](https://www.raspberrypi.com/documentation/computers/images/CMIO-Cam-GPIO2.jpg)
5.  *(CM4 only)* : Connect the J6 GPIO pins with two vertical-orientation jumpers.
    ![Connect the J6 GPIO pins in vertical orientation](https://www.raspberrypi.com/documentation/computers/images/j6_vertical.jpg)
6. Reconnect the Compute Module to power.
7.  *(CM1, CM3, CM3+, and CM4S only)* : Add the following directive to `/boot/firmware/config.txt` to assign GPIO 31 as the CAM0 regulator:

    ```
    dtparam=cam0_reg
    ```
8. | Add the appropriate directive to `/boot/firmware/config.txt` to manually configure the driver for your camera model: |  |
    | camera model | directive |
    | ------------------------------------------------------------------------------------------- | -- |
    | v1 camera                                                                                 | `dtoverlay=ov5647,cam0` |
    | v2 camera                                                                                 | `dtoverlay=imx219,cam0` |
    | v3 camera                                                                                 | `dtoverlay=imx708,cam0` |
    | HQ camera                                                                                 | `dtoverlay=imx477,cam0` |
    | GS camera                                                                                 | `dtoverlay=imx296,cam0` |
9. Reboot your Compute Module with `sudo reboot`.
10. Run the following command to check the list of detected cameras:

     ```
     $ rpicam-hello --list
     ```

     You should see both camera models, referred to by the driver directives in the table above, in the output.

### Software

Raspberry Pi OS includes the `libcamera` library to help you take images with your Raspberry Pi.

#### Take a picture

Use the following command to immediately take a picture and save it to a file in PNG encoding using the `MMDDhhmmss` date format as a filename:

```
$ rpicam-still --datetime -e png
```

Use the `-t` option to add a delay in milliseconds. Use the `--width` and `--height` options to specify a width and height for the image.

#### Take a video

Use the following command to immediately start recording a ten-second long video and save it to a file with the h264 codec named `video.h264`:

```
$ rpicam-vid -t 10000 -o video.h264
```

#### Specify which camera to use

By default, `libcamera` always uses the camera with index `0` in the `--list-cameras` list. To specify a camera option, get an index value for each camera from the following command:

```
$ rpicam-hello --list-cameras
Available cameras
-----------------
0 : imx477 [4056x3040] (/base/soc/i2c0mux/i2c@1/imx477@1a)
    Modes: 'SRGGB10_CSI2P' : 1332x990 [120.05 fps - (696, 528)/2664x1980 crop]
           'SRGGB12_CSI2P' : 2028x1080 [50.03 fps - (0, 440)/4056x2160 crop]
                             2028x1520 [40.01 fps - (0, 0)/4056x3040 crop]
                             4056x3040 [10.00 fps - (0, 0)/4056x3040 crop]

1 : imx708 [4608x2592] (/base/soc/i2c0mux/i2c@0/imx708@1a)
    Modes: 'SRGGB10_CSI2P' : 1536x864 [120.13 fps - (768, 432)/3072x1728 crop]
                             2304x1296 [56.03 fps - (0, 0)/4608x2592 crop]
                             4608x2592 [14.35 fps - (0, 0)/4608x2592 crop]
```

In the above output:

* `imx477` refers to a HQ camera with an index of `0`
* `imx708` refers to a v3 camera with an index of `1`

To use the HQ camera, pass its index (`0`) to the `--camera` `libcamera` option:

```
$ rpicam-hello --camera 0
```

To use the v3 camera, pass its index (`1`) to the `--camera` `libcamera` option:

```
$ rpicam-hello --camera 1
```

### I2C mapping of GPIO pins

By default, the supplied camera drivers assume that CAM1 uses `i2c-10` and CAM0 uses `i2c-0`. Compute module I/O boards map the following GPIO pins to `i2c-10` and `i2c-0`:

| I/O Board Model                | `i2c-10` pins       | `i2c-0` pins       |
| -------------------------------- | ------------- | ------------- |
| CM4 I/O Board                  | GPIOs 44,45 | GPIOs 0,1   |
| CM1, CM3, CM3+, CM4S I/O Board | GPIOs 0,1   | GPIOs 28,29 |

To connect a camera to the CM1, CM3, CM3+ and CM4S I/O Board, add the following directive to `/boot/firmware/config.txt` to accommodate the swapped pin assignment:

```
dtoverlay=cm-swap-i2c0
```

Alternative boards may use other pin assignments. Check the documentation for your board and use the following alternate overrides depending on your layout:

| Swap                               | Override |
| ------------------------------------ | ---------- |
| Use GPIOs 0,1 for i2c0             | `i2c0-gpio0`         |
| Use GPIOs 28,29 for i2c0 (default) | `i2c0-gpio28`         |
| Use GPIOs 44&45 for i2c0           | `i2c0-gpio44`         |
| Use GPIOs 0&1 for i2c10 (default)  | `i2c10-gpio0`         |
| Use GPIOs 28&29 for i2c10          | `i2c10-gpio28`         |
| Use GPIOs 44&45 for i2c10          | `i2c10-gpio44`         |

#### GPIO pins for shutdown

For camera shutdown, Device Tree uses the pins assigned by the `cam1_reg` and `cam0_reg` overlays.

The CM4 IO board provides a single GPIO pin for both aliases, so both cameras share the same regulator.

The CM1, CM3, CM3+, and CM4S I/O boards provides no GPIO pin for `cam1_reg` and `cam0_reg`, so the regulators are disabled on those boards. However, you can enable them with the following directives in `/boot/firmware/config.txt`:

* `dtparam=cam1_reg`
* `dtparam=cam0_reg`

To assign `cam1_reg` and `cam0_reg` to a specific pin on a custom board, use the following directives in `/boot/firmware/config.txt`:

* `dtparam=cam1_reg_gpio=<pin number>`
* `dtparam=cam0_reg_gpio=<pin number>`

For example, to use pin 42 as the regulator for CAM1, add the directive `dtparam=cam1_reg_gpio=42` to `/boot/firmware/config.txt`.

These directives only work for GPIO pins connected directly to the SoC, not for expander GPIO pins.

## Attach the official 7-inch display

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/computers/compute-module/cmio-display.adoc)

Update your system software and firmware to the latest version before starting. Compute Modules mostly use the same process, but sometimes physical differences force changes for a particular model.

### Connect a display to DISP1

| NOTE | The Raspberry Pi Zero camera cable cannot be used as an alternative to the RPI-DISPLAY adapter. The two cables have distinct wiring. |
| ------ | -------------------------------------------------------------------------------------------------------------------------------------- |

To connect a display to DISP1:

1. Disconnect the Compute Module from power.
2. Connect the display to the DISP1 port on the Compute Module IO board through the 22W to 15W display adapter.
3. *(CM1, CM3, CM3+, and CM4S only)* : Connect the following GPIO pins with jumper cables:

    * `0` to `CD1_SDA`
    * `1` to `CD1_SCL`
4. Reconnect the Compute Module to power.
5. Add the following line to [`/boot/firmware/config.txt`](https://www.raspberrypi.com/documentation/computers/config_txt.html#what-is-config-txt):

    ```
    dtoverlay=vc4-kms-dsi-7inch
    ```
6. Reboot your Compute Module with `sudo reboot`. Your device should detect and begin displaying output to your display.

### Connect a display to DISP0

To connect a display to DISP0:

1. Connect the display to the DISP0 port on the Compute Module IO board through the 22W to 15W display adapter.
2. *(CM1, CM3, CM3+, and CM4S only)* : Connect the following GPIO pins with jumper cables:

    * `28` to `CD0_SDA`
    * `29` to `CD0_SCL`
3. Reconnect the Compute Module to power.
4. Add the following line to `/boot/firmware/config.txt`:

    ```
    dtoverlay=vc4-kms-dsi-7inch
    ```
5. Reboot your Compute Module with `sudo reboot`. Your device should detect and begin displaying output to your display.

### Disable touchscreen

The touchscreen requires no additional configuration. Connect it to your Compute Module, and both the touchscreen element and display should work once successfully detected.

To disable the touchscreen element, but still use the display, add the following line to `/boot/firmware/config.txt`:

```
disable_touchscreen=1
```

### Disable display

To entirely ignore the display when connected, add the following line to `/boot/firmware/config.txt`:

```
ignore_lcd=1
```

## Specifications

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/computers/compute-module/datasheet.adoc)

### Compute Module 4 datasheet

To learn more about Compute Module 4 (CM4) and its corresponding IO Board, see the following documents:

* [CM4 datasheet](https://datasheets.raspberrypi.com/cm4/cm4-datasheet.pdf)

##### [Configure the Compute Module 4](https://pip.raspberrypi.com/categories/685-whitepapers-app-notes/documents/RP-003470-WP/Configuring-the-Compute-Module-4.pdf)

Configure the Compute Module 4

The Compute Module 4 is available in a number of different hardware configurations. Some use cases disable certain features that aren’t required.

This document describes how to disable various hardware and software interfaces.

### Compute Module 4 IO Board datasheet

Design data for the Compute Module 4 IO Board (CM4IO) can be found in its datasheet:

* [CM4IO datasheet](https://datasheets.raspberrypi.com/cm4io/cm4io-datasheet.pdf)

We also provide a KiCad PCB design set for the CM4 IO Board:

* [CM4IO KiCad files](https://datasheets.raspberrypi.com/cm4io/CM4IO-KiCAD.zip)

### Compute Module 4S datasheet

Compute Module 4S (CM4S) offers the internals of CM4 in the DDR2-SODIMM form factor of CM1, CM3, and CM3+. To learn more about CM4S, see the following documents:

* [CM4S datasheet](https://datasheets.raspberrypi.com/cm4s/cm4s-datasheet.pdf)

### Compute Module 3+ datasheet

Compute Module 3+ (CM3+) is a supported product with an end-of-life (EOL) date no earlier than January 2028. To learn more about CM3+ and its corresponding IO Board, see the following documents:

* [CM3+ datasheet](https://datasheets.raspberrypi.com/cm/cm3-plus-datasheet.pdf)

### Compute Module 1 and Compute Module 3 datasheet

Raspberry Pi Compute Module 1 (CM1) and Compute Module 3 (CM3) are supported products with an end-of-life (EOL) date no earlier than January 2026. To learn more about CM1 and CM3, see the following documents:

* [CM1 and CM3 datasheet](https://datasheets.raspberrypi.com/cm/cm1-and-cm3-datasheet.pdf)
* [Schematics for CM1](https://datasheets.raspberrypi.com/cm/cm1-schematics.pdf)
* [Schematics for CM3](https://datasheets.raspberrypi.com/cm/cm3-schematics.pdf)

##### [Transition from Compute Module 1 or Compute Module 3 to Compute Module 4](https://pip.raspberrypi.com/categories/685-whitepapers-app-notes/documents/RP-003469-WP/Transitioning-from-CM3-to-CM4.pdf)

Transition from Compute Module 1 or Compute Module 3 to Compute Module 4

This white paper helps developers migrate from Compute Module 1 or Compute Module 3 to Compute Module 4.

### Compute Module IO Board schematics

The Compute Module IO Board (CMIO) provides a variety of interfaces for CM1, CM3, CM3L, and CM3+. The Compute Module IO Board comes in two variants: Version 1 and Version 3. Version 1 is only compatible with CM1. Version 3 is compatible with CM1, CM3, CM3+, and CM4S. Compute Module IO Board Version 3 is sometimes written as the shorthand CMIO3. To learn more about CMIO1 and CMIO3, see the following documents:

* [Schematics for CMIO](https://datasheets.raspberrypi.com/cmio/cmio-schematics.pdf)
* [Design documents for CMIO Version 1.2 (CMIO/CMIO1)](https://datasheets.raspberrypi.com/cmio/RPi-CMIO-R1P2.zip)
* [Design documents for CMIO Version 3.0 (CMIO3)](https://datasheets.raspberrypi.com/cmio/RPi-CMIO-R3P0.zip)

### Compute Module Camera/Display Adapter Board schematics

The Compute Module Camera/Display Adapter Board (CMCDA) provides camera and display interfaces for Compute Modules. To learn more about the CMCDA, see the following documents:

* [Schematics for the CMCDA](https://datasheets.raspberrypi.com/cmcda/cmcda-schematics.pdf)
* [Design documents for CMCDA Version 1.1](https://datasheets.raspberrypi.com/cmcda/RPi-CMCDA-1P1.zip)

### Under-voltage detection

The following schematic describes an under-voltage detection circuit, as used in older models of Raspberry Pi:

![Under-voltage detect](https://www.raspberrypi.com/documentation/computers/images/under_voltage_detect.png?hash=3cbc75b81e54c6b8caabfa4b29edcc0d)
