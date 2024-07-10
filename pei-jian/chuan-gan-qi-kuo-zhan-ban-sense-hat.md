# Sense HAT

## Introducing the Sense HAT

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/accessories/sense-hat/intro.adoc)

The [Raspberry Pi Sense HAT](https://www.raspberrypi.com/products/sense-hat/) is an add-on board that gives your Raspberry Pi an array of sensing capabilities. The on-board sensors allow you to monitor pressure, humidity, temperature, colour, orientation, and movement. The bright 8×8 RGB LED matrix allows you to visualise data from the sensors, and the five-button joystick lets users interact with your projects.

![Sense HAT](https://www.raspberrypi.com/documentation/accessories/images/Sense-HAT.jpg?hash=e095672e700544fc89a62dad3d9fc164)

The Sense HAT was originally developed for use on the International Space Station, as part of the educational [Astro Pi](https://astro-pi.org/) programme run by the [Raspberry Pi Foundation](https://raspberrypi.org/) in partnership with the [European Space Agency](https://www.esa.int/). It is well suited to many projects that require position, motion, orientation, or environmental sensing. The Sense HAT is powered by the Raspberry Pi computer to which it is connected.

An officially supported [Python library](https://www.raspberrypi.com/documentation/accessories/sense-hat.html#use-the-sense-hat-with-python) provides access to all of the on-board sensors, the LED matrix, and the joystick. The Sense HAT is compatible with any Raspberry Pi computer with a 40-pin GPIO header.

## Installation

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/accessories/sense-hat/software.adoc)

In order to work correctly, the Sense HAT requires an up-to-date kernel, I2C to be enabled, and a few libraries to get started.

Ensure your APT package list is up-to-date:

```
$ sudo apt update
```

Next, install the sense-hat package, which will ensure the kernel is up to date, enable I2C, and install the necessary libraries and programs:

```
$ sudo apt install sense-hat
```

Finally, a reboot may be required if I2C was disabled or the kernel was not up-to-date prior to the install:

```
$ sudo reboot
```

## Getting started

After installation, example code can be found under `/usr/src/sense-hat/examples`.

### Further reading

![](https://www.raspberrypi.com/documentation/accessories/images/experiment-with-the-sense-hat.png)[https://github.com/raspberrypipress/released-pdfs/raw/main/experiment-with-the-sense-hat.pdf](https://github.com/raspberrypipress/released-pdfs/raw/main/experiment-with-the-sense-hat.pdf)

You can find more information on how to use the Sense HAT in the Raspberry Pi Press book [Experiment with the Sense HAT](https://github.com/raspberrypipress/released-pdfs/raw/main/experiment-with-the-sense-hat.pdf). Written by The Raspberry Pi Foundation’s Education Team, it is part of the MagPi Essentials series published by Raspberry Pi Press. The book covers the background of the Astro Pi project, and walks you through how to make use of all the Sense HAT features using the [Python library](https://www.raspberrypi.com/documentation/accessories/sense-hat.html#use-the-sense-hat-with-python).

You can [download this book](https://github.com/raspberrypipress/released-pdfs/raw/main/experiment-with-the-sense-hat.pdf) as a PDF file for free, it has been released under a Creative Commons [Attribution-NonCommercial-ShareAlike](https://creativecommons.org/licenses/by-nc-sa/3.0/) 3.0 Unported (CC BY NC-SA) licence.

### Use the Sense HAT with Python

`sense-hat` is the officially supported library for the Sense HAT; it provides access to all of the on-board sensors and the LED matrix.

Complete documentation for the library can be found at [sense-hat.readthedocs.io](https://sense-hat.readthedocs.io/en/latest/).

### Use the Sense HAT with C++

[RTIMULib](https://github.com/RPi-Distro/RTIMULib) is a C++ and Python library that makes it easy to use 9-dof and 10-dof IMUs with embedded Linux systems. A pre-calibrated settings file is provided in `/etc/RTIMULib.ini`, which is also copied and used by `sense-hat`. The included examples look for `RTIMULib.ini` in the current working directory, so you may wish to copy the file there to get more accurate data.

The RTIMULibDrive11 example comes pre-compiled to help ensure everything works as intended. It can be launched by running `RTIMULibDrive11` and closed by pressing `Ctrl C`.

| NOTE | The C/C++ examples can be compiled by running `make` in the appropriate directory. |
| ------ | ------------------------------------------------------------------------------ |

## Sense HAT hardware

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/accessories/sense-hat/hardware.adoc)

The Sense HAT has an 8×8 RGB LED matrix and a five-button joystick, and includes the following sensors:

* Gyroscope
* Accelerometer
* Magnetometer
* Temperature
* Barometric pressure
* Humidity
* Colour and brightness

Schematics and mechanical drawings for the Sense HAT and the Sense HAT V2 are available for download.

* [Sense HAT V1 schematics](https://datasheets.raspberrypi.com/sense-hat/sense-hat-schematics.pdf).
* [Sense HAT V2 schematics](https://datasheets.raspberrypi.com/sense-hat/sense-hat-v2-schematics.pdf).
* [Sense HAT mechanical drawings](https://datasheets.raspberrypi.com/sense-hat/sense-hat-mechanical-drawing.pdf).

### LED matrix

The LED matrix is an RGB565 [framebuffer](https://www.kernel.org/doc/Documentation/fb/framebuffer.txt) with the id "RPi-Sense FB". The appropriate device node can be written to as a standard file or mmap-ed. The included 'snake' example shows how to access the framebuffer.

### Joystick

The joystick comes up as an input event device named "Raspberry Pi Sense HAT Joystick", mapped to the arrow keys and `Enter`. It should be supported by any library which is capable of handling inputs, or directly through the [evdev interface](https://www.kernel.org/doc/Documentation/input/input.txt). Suitable libraries include SDL, [pygame](http://www.pygame.org/docs/) and [python-evdev](https://python-evdev.readthedocs.org/en/latest/). The included 'snake' example shows how to access the joystick directly.

## Calibrate

Install the necessary software and run the calibration program as follows:

```
$ sudo apt update
$ sudo apt install octave -y
$ cd
$ cp /usr/share/librtimulib-utils/RTEllipsoidFit ./ -a
$ cd RTEllipsoidFit
$ RTIMULibCal
```

The calibration program displays the following menu:

```
Options are:

  m - calibrate magnetometer with min/max
  e - calibrate magnetometer with ellipsoid (do min/max first)
  a - calibrate accelerometers
  x - exit

Enter option:
```

Press lowercase `m`. The following message will then show. Press any key to start.

```
    Magnetometer min/max calibration
    --------------------------------
    Waggle the IMU chip around, ensuring that all six axes
    (+x, -x, +y, -y and +z, -z) go through their extrema.
    When all extrema have been achieved, enter 's' to save, 'r' to reset
    or 'x' to abort and discard the data.

    Press any key to start...
```

After it starts, you should see output similar to the following scrolling up the screen:

```
 Min x:  51.60  min y:  69.39  min z:  65.91
 Max x:  53.15  max y:  70.97  max z:  67.97
```

Focus on the two lines at the very bottom of the screen, as these are the most recently posted measurements from the program.

Now, pick up the Raspberry Pi and Sense HAT and move it around in every possible way you can think of. It helps if you unplug all non-essential cables to avoid clutter.

Try and get a complete circle in each of the pitch, roll and yaw axes. Take care not to accidentally eject the SD card while doing this. Spend a few minutes moving the Sense HAT, and stop when you find that the numbers are not changing any more.

Now press lowercase `s` then lowercase `x` to exit the program. If you run the `ls` command now, you’ll see a new `RTIMULib.ini` file has been created.

In addition to those steps, you can also do the ellipsoid fit by performing the steps above, but pressing `e` instead of `m`.

When you’re done, copy the resulting `RTIMULib.ini` to `/etc/` and remove the local copy in `~/.config/sense_hat/`:

```
$ rm ~/.config/sense_hat/RTIMULib.ini
$ sudo cp RTIMULib.ini /etc
```

## Read and write EEPROM data

Enable I2C0 and I2C1 by adding the following line to the [`/boot/firmware/config.txt`](https://www.raspberrypi.com/documentation/computers/config_txt.html#what-is-config-txt) file:

```
dtparam=i2c_vc=on
dtparam=i2c_arm=on
```

Enter the following command to reboot:

```
$ sudo systemctl reboot
```

Download and build the flash tool:

```
$ git clone https://github.com/raspberrypi/hats.git
$ cd hats/eepromutils
$ make
```

| NOTE | These steps may not work on Raspberry Pi 2 Model B Rev 1.0 and Raspberry Pi 3 Model B boards. The firmware will take control of I2C0, causing the ID pins to be configured as inputs. |
| ------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

### Read

EEPROM data can be read with the following command:

```
$ sudo ./eepflash.sh -f=sense_read.eep -t=24c32 -r
```

### Write

Download EEPROM settings and build the `.eep` binary:

```
$ wget https://github.com/raspberrypi/rpi-sense/raw/master/eeprom/eeprom_settings.txt -O sense_eeprom.txt
$ ./eepmake sense_eeprom.txt sense.eep /boot/firmware/overlays/rpi-sense-overlay.dtb
```

Disable write protection:

```
$ i2cset -y -f 1 0x46 0xf3 1
```

Write the EEPROM data:

```
$ sudo ./eepflash.sh -f=sense.eep -t=24c32 -w
```

Re-enable write protection:

```
$ i2cset -y -f 1 0x46 0xf3 0
```

| WARNING | This operation will not damage your Raspberry Pi or Sense HAT, but if an error occurs, the HAT may no longer be automatically detected. The steps above are provided for debugging purposes only. |
| --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
