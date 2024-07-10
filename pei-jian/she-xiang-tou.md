# Camera

## About the Camera Modules

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/accessories/camera/camera_hardware.adoc)

There are now several official Raspberry Pi camera modules. The original 5-megapixel model was [released](https://www.raspberrypi.com/news/camera-board-available-for-sale/) in 2013, it was followed by an 8-megapixel [Camera Module 2](https://www.raspberrypi.com/products/camera-module-v2/) which was [released](https://www.raspberrypi.com/news/new-8-megapixel-camera-board-sale-25/) in 2016. The latest camera model is the 12-megapixel [Camera Module 3](https://raspberrypi.com/products/camera-module-3/) which was [released](https://www.raspberrypi.com/news/new-autofocus-camera-modules/) in 2023. The original 5MP device is no longer available from Raspberry Pi.

All of these cameras come in visible light and infrared versions, while the Camera Module 3 also comes as a standard or wide FoV model for a total of four different variants.

![Camera Module 3 normal and wide angle](https://www.raspberrypi.com/documentation/accessories/images/cm3.jpg?hash=87abd731a81318a03d494783da281fc9)

Camera Module 3 (left) and Camera Module 3 Wide (right)

![Camera Module 3 NoIR normal and wide angle](https://www.raspberrypi.com/documentation/accessories/images/cm3_noir.jpg?hash=432695c74fd478fd59e68e91c6b8ac75)

Camera Module 3 NoIR (left) and Camera Module 3 NoIR Wide (right)

Additionally a 12-megapixel [High Quality Camera](https://www.raspberrypi.com/products/raspberry-pi-high-quality-camera/) with CS- or M12-mount variants for use with external lenses was [released in 2020](https://www.raspberrypi.com/news/new-product-raspberry-pi-high-quality-camera-on-sale-now-at-50/) and [2023](https://www.raspberrypi.com/news/new-autofocus-camera-modules/) respectively. There is no infrared version of the HQ Camera, however the [IR Filter can be removed](https://www.raspberrypi.com/documentation/accessories/camera.html#filter-removal) if required.

![M12- and C/CS-mount versions of the HQ Camera](https://www.raspberrypi.com/documentation/accessories/images/hq.jpg?hash=bac44ac498765e28c7160ac0e3907e32)

HQ Camera, M12-mount (left) and C/CS-mount (right)

Finally, there is the Global Shutter camera, which was [released in 2023](http://raspberrypi.com/news/new-raspberry-pi-global-shutter-camera). There is no infrared version of the GS Camera, however the IR Filter can be removed if required.

![GS Camera](https://www.raspberrypi.com/documentation/accessories/images/gs-camera.jpg?hash=cd9e8c1e1dabd47d79800c72870af6f6)

Global Shutter Camera

| NOTE | Raspberry Pi Camera Modules are compatible with all Raspberry Pi computers with CSI connectors - that is, all models except Raspberry Pi 400 and the 2016 launch version of Zero. |
| ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

### Rolling or Global shutter?

Most digital cameras, including our Camera Modules, use a **rolling shutter**: they scan the image they’re capturing line-by-line, then output the results. You may have noticed that this can cause distortion effects in some settings; if you’ve ever photographed rotating propeller blades, you’ve probably spotted the image shimmering rather than looking like an object that is rotating. The propeller blades have had enough time to change position in the tiny moment that the camera has taken to swipe across and observe the scene.

A **global shutter**, like the one on our Global Shutter Camera Module, doesn’t do this. It captures the light from every pixel in the scene at once, so your photograph of propeller blades will not suffer from the same distortion.

Why is this useful? Fast-moving objects, like those propeller blades, are now easy to capture; we can also synchronise several cameras to take a photo at precisely the same moment in time. There are plenty of benefits here, like minimising distortion when capturing stereo images. (The human brain is confused if any movement that appears in the left eye has not appeared in the right eye yet.) The Raspberry Pi Global Shutter Camera can also operate with shorter exposure times - down to 30µs, given enough light - than a rolling shutter camera, which makes it useful for high-speed photography.

| NOTE | The Global Shutter Camera’s image sensor has a 6.3mm diagonal active sensing area, which is similar in size to Raspberry Pi’s HQ Camera. However, the pixels are larger and can collect more light. Large pixel size and low pixel count are valuable in machine-vision applications; the more pixels a sensor produces, the harder it is to process the image in real time. To get around this, many applications downsize and crop images. This is unnecessary with the Global Shutter Camera and the appropriate lens magnification, where the lower resolution and large pixel size mean an image can be captured natively. |
| ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

## Install a Raspberry Pi camera

| WARNING | Cameras are sensitive to static. Earth yourself prior to handling the PCB. A sink tap or similar should suffice if you don’t have an earthing strap. |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |

### Connect the Camera

The flex cable inserts into the connector labelled CAMERA on the Raspberry Pi, which is located between the Ethernet and HDMI ports. The cable must be inserted with the silver contacts facing the HDMI port. To open the connector, pull the tabs on the top of the connector upwards, then towards the Ethernet port. The flex cable should be inserted firmly into the connector, with care taken not to bend the flex at too acute an angle. To close the connector, push the top part of the connector towards the HDMI port and down, while holding the flex cable in place.

We have created a video to illustrate the process of connecting the camera. The following video shows how to connect the original camera on the original Raspberry Pi 1. The principle is the same for all Raspberry Pi boards with a camera connector, though the Raspberry Pi 5 and all Raspberry Pi Zero models require a [different camera cable](https://www.raspberrypi.com/products/camera-cable/).

Depending on the model, the camera may come with a small piece of translucent blue plastic film covering the lens. This is only present to protect the lens while it is being mailed to you, and needs to be removed by gently peeling it off.

| NOTE | There is additional documentation available around fitting the recommended [6mm](https://datasheets.raspberrypi.com/hq-camera/cs-mount-lens-guide.pdf) and [16mm](https://datasheets.raspberrypi.com/hq-camera/c-mount-lens-guide.pdf) lens to the HQ Camera. |
| ------ | --------------------------------------------------------------------------------------------------------- |

### Prepare the Software

Before proceeding, we recommend ensuring that your kernel, GPU firmware and applications are all up to date. Please follow the instructions on [keeping your operating system up to date](https://www.raspberrypi.com/documentation/computers/os.html#update-software).

Then, please follow the relevant setup instructions for [`rpicam-apps`](https://www.raspberrypi.com/documentation/computers/camera_software.html#rpicam-apps), and the [Picamera2 Python library](https://datasheets.raspberrypi.com/camera/picamera2-manual.pdf).

## Hardware Specification

|                                  | Camera Module v1                     | Camera Module v2                            | Camera Module 3                                       | Camera Module 3 Wide                                  | HQ Camera                                            | GS Camera                                           |
| ---------------------------------- | -------------------------------------- | --------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------ | ----------------------------------------------------- |
| Net price                        | \$25                              | \$25                                     | \$25                                               | \$35                                               | \$50                                              | \$50                                             |
| Size                             | Around 25 × 24 × 9 mm              | Around 25 × 24 × 9 mm                     | Around 25 × 24 × 11.5 mm                            | Around 25 × 24 × 12.4 mm                            | 38 x 38 x 18.4mm (excluding lens)                    | 38 x 38 x 19.8mm (29.5mm with adaptor and dust cap) |
| Weight                           | 3g                                   | 3g                                          | 4g                                                    | 4g                                                    | 30.4g                                                | 34g (41g with adaptor and dust cap)                 |
| Still resolution                 | 5 Megapixels                         | 8 Megapixels                                | 11.9 Megapixels                                       | 11.9 Megapixels                                       | 12.3 Megapixels                                      | 1.58 Megapixels                                     |
| Video modes                      | 1080p30, 720p60 and 640 × 480p60/90 | 1080p47, 1640 × 1232p41 and 640 × 480p206 | 2304 × 1296p56, 2304 × 1296p30 HDR, 1536 × 864p120 | 2304 × 1296p56, 2304 × 1296p30 HDR, 1536 × 864p120 | 2028 × 1080p50, 2028 × 1520p40 and 1332 × 990p120 | 1456 x 1088p60                                      |
| Sensor                           | OmniVision OV5647                    | Sony IMX219                                 | Sony IMX708                                           | Sony IMX708                                           | Sony IMX477                                          | Sony IMX296                                         |
| Sensor resolution                | 2592 × 1944 pixels                  | 3280 × 2464 pixels                         | 4608 x 2592 pixels                                    | 4608 x 2592 pixels                                    | 4056 x 3040 pixels                                   | 1456 x 1088 pixels                                  |
| Sensor image area                | 3.76 × 2.74 mm                      | 3.68 x 2.76 mm (4.6 mm diagonal)            | 6.45 x 3.63mm (7.4mm diagonal)                        | 6.45 x 3.63mm (7.4mm diagonal)                        | 6.287mm x 4.712 mm (7.9mm diagonal)                  | 6.3mm diagonal                                      |
| Pixel size                       | 1.4 µm × 1.4 µm                   | 1.12 µm x 1.12 µm                         | 1.4 µm x 1.4 µm                                     | 1.4 µm x 1.4 µm                                     | 1.55 µm x 1.55 µm                                  | 3.45 µm x 3.45 µm                                 |
| Optical size                     | 1/4"                                 | 1/4"                                        | 1/2.43"                                               | 1/2.43"                                               | 1/2.3"                                               | 1/2.9"                                              |
| Focus                            | Fixed                                | Adjustable                                  | Motorized                                             | Motorized                                             | Adjustable                                           | Adjustable                                          |
| Depth of field                   | Approx 1 m to ∞                     | Approx 10 cm to ∞                          | Approx 10 cm to ∞                                    | Approx 5 cm to ∞                                     | N/A                                                  | N/A                                                 |
| Focal length                     | 3.60 mm +/- 0.01                     | 3.04 mm                                     | 4.74 mm                                               | 2.75 mmm                                              | Depends on lens                                      | Depends on lens                                     |
| Horizontal Field of View (FoV)   | 53.50 +/- 0.13 degrees               | 62.2 degrees                                | 66 degrees                                            | 102 degrees                                           | Depends on lens                                      | Depends on lens                                     |
| Vertical Field of View (FoV)     | 41.41 +/- 0.11 degrees               | 48.8 degrees                                | 41 degrees                                            | 67 degrees                                            | Depends on lens                                      | Depends on lens                                     |
| Focal ratio (F-Stop)             | F2.9                                 | F2.0                                        | F1.8                                                  | F2.2                                                  | Depends on lens                                      | Depends on lens                                     |
| Maximum exposure times (seconds) | 0.97                                 | 11.76                                       | 112                                                   | 112                                                   | 670.74                                               | 15.5                                                |
| Lens Mount                       | N/A                                  | N/A                                         | N/A                                                   | N/A                                                   | C/CS- or M12-mount                                   | C/CS                                                |
| NoIR version available?          | Yes                                  | Yes                                         | Yes                                                   | Yes                                                   | No                                                   | No                                                  |

| NOTE | There is [some evidence](https://github.com/raspberrypi/libcamera/issues/43) to suggest that the Camera Module 3 may emit RFI at a harmonic of the CSI clock rate. This RFI is in a range to interfere with GPS L1 frequencies (1575 MHz). Please see the [thread on Github](https://github.com/raspberrypi/libcamera/issues/43) for details and proposed workarounds. |
| ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

### Mechanical Drawings

Available mechanical drawings;

* Camera Module 2 [PDF](https://datasheets.raspberrypi.com/camera/camera-module-2-mechanical-drawing.pdf)
* Camera Module 3 [PDF](https://datasheets.raspberrypi.com/camera/camera-module-3-standard-mechanical-drawing.pdf)
* Camera Module 3 Wide [PDF](https://datasheets.raspberrypi.com/camera/camera-module-3-wide-mechanical-drawing.pdf)
* Camera Module 3 [STEP files](https://datasheets.raspberrypi.com/camera/camera-module-3-step.zip)
* HQ Camera Module (CS-mount version) [PDF](https://datasheets.raspberrypi.com/hq-camera/hq-camera-cs-mechanical-drawing.pdf)

  * The CS-mount [PDF](https://datasheets.raspberrypi.com/hq-camera/hq-camera-cs-lensmount-drawing.pdf)
* HQ Camera Module (M12-mount version) [PDF](https://datasheets.raspberrypi.com/hq-camera/hq-camera-m12-mechanical-drawing.pdf)
* GS Camera Module [PDF](https://datasheets.raspberrypi.com/gs-camera/gs-camera-mechanical-drawing.pdf)

| NOTE | Board dimensions and mounting-hole positions for Camera Module 3 are identical to Camera Module 2. However, due to changes in the size and position of the sensor module, it is not mechanically compatible with the camera lid for the Raspberry Pi Zero Case. |
| ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

### Schematics

Schematic of the Raspberry Pi CSI camera connector.

![camera connector](https://www.raspberrypi.com/documentation/accessories/images/RPi-S5-conn.png)

Other available schematics;

* Camera Module v2 [PDF](https://datasheets.raspberrypi.com/camera/camera-module-2-schematics.pdf)
* Camera Module v3 [PDF](https://datasheets.raspberrypi.com/camera/camera-module-3-schematics.pdf)
* HQ Camera Module [PDF](https://datasheets.raspberrypi.com/hq-camera/hq-camera-schematics.pdf)

## Camera Filters

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/accessories/camera/filters.adoc)

Some transmission characteristics are available for the Camera Module 3 and the HQ and GS cameras.

| NOTE | These graphs are available as [a PDF](https://datasheets.raspberrypi.com/camera/camera-extended-spectral-sensitivity.pdf). |
| ------ | --------------------------------- |

### Camera Module 3

The Camera Module 3 is built around the IMX708, which has the following spectral sensitivity characteristics.

![Camera Module 3 Transmission Graph](https://www.raspberrypi.com/documentation/accessories/images/cm3-filter.png?hash=b9fd642050f8dfeb52df80c2d23a528e)

### HQ Camera

Raspberry Pi HQ Camera without IR-Cut filter.

![HQ Camera Transmission Graph without IR-Cut filter](https://www.raspberrypi.com/documentation/accessories/images/hq.png?hash=25eaca9e283810d0d6951e6ecd69c409)

### GS Camera

Raspberry Pi GS Camera without IR-Cut filter.

![GS Camera Transmission Graph without IR-Cut filter](https://www.raspberrypi.com/documentation/accessories/images/gs.png?hash=199052f768e0b1fdcd3154510ccde6f1)

### HQ and GS Cameras

The HQ and GS Cameras use a Hoya CM500 infrared filter. Its transmission characteristics are as represented in the following graph.

![CM500 Transmission Graph](https://www.raspberrypi.com/documentation/accessories/images/hoyacm500.png?hash=f5a0512fff9a3def9c2152f1a7c276eb)

## Filter Removal

| NOTE | This procedure applies to both the HQ and GS cameras. |
| ------ | ------------------------------------------------------- |

| WARNING | **This procedure cannot be reversed:**  the adhesive that attaches the filter will not survive being lifted and replaced, and while the IR filter is about 1.1mm thick, it may crack when it is removed. **Removing it will void the warranty on the product**. Nevertheless, removing the filter will be desirable to some users. |
| --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

![FILTER ON small](https://www.raspberrypi.com/documentation/accessories/images/FILTER_ON_small.jpg)

Both the High Quality Camera and Global Shutter Camera contain an IR filter, which is used to reduce the camera’s sensitivity to infrared light. This ensures that outdoor photos look more natural. However, some nature photography can be enhanced with the removal of this filter; the colours of sky, plants, and water can be affected by its removal. The camera can also be used without the filter for night vision in a location that is illuminated with infrared light.

| WARNING | Before proceeding read through all of the steps and decide whether you are willing to void your warranty. **Do not proceed** unless you are sure that you are willing to void your warranty. |
| --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

To remove the filter:

* Work in a clean and dust-free environment, as the sensor will be exposed to the air.
* Unscrew the two 1.5 mm hex lock keys on the underside of the main circuit board. Be careful not to let the washers roll away. There is a gasket of slightly sticky material between the housing and PCB which will require some force to separate.

![SCREW REMOVED small](https://www.raspberrypi.com/documentation/accessories/images/SCREW_REMOVED_small.jpg)

* Lift up the board and place it down on a very clean surface. Make sure the sensor does not touch the surface.

![FLATLAY small](https://www.raspberrypi.com/documentation/accessories/images/FLATLAY_small.jpg)

* You may try some ways to weaken the adhesive, such as a little isopropyl alcohol and/or heat (~20-30 C).

![SOLVENT small](https://www.raspberrypi.com/documentation/accessories/images/SOLVENT_small.jpg)

* Turn the lens mount around so that it is "looking" upwards and place it on a table.
* Using a pen top or similar soft plastic item, push down on the filter only at the very edges where the glass attaches to the aluminium - to minimise the risk of breaking the filter. The glue will break and the filter will detach from the lens mount.

![REMOVE FILTER small](https://www.raspberrypi.com/documentation/accessories/images/REMOVE_FILTER_small.jpg)

* Given that changing lenses will expose the sensor, at this point you could affix a clear filter (for example, OHP plastic) to minimize the chance of dust entering the sensor cavity.
* Replace the main housing over the circuit board. Be sure to realign the housing with the gasket, which remains on the circuit board.
* The nylon washer prevents damage to the circuit board; apply this washer first. Next, fit the steel washer, which prevents damage to the nylon washer.
* Screw down the two hex lock keys. As long as the washers have been fitted in the correct order, they do not need to be screwed very tightly.

![FILTER OFF small](https://www.raspberrypi.com/documentation/accessories/images/FILTER_OFF_small.jpg)

| NOTE | It is likely to be difficult or impossible to glue the filter back in place and return the device to functioning as a normal optical camera. |
| ------ | ---------------------------------------------------------------------------------------------------------------------------------------------- |

## Recommended Lenses

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/accessories/camera/lens.adoc)

The following lenses are recommended for use with our HQ and GS cameras.

| NOTE | While the HQ Camera is available in both C/CS- and M12-mount versions, the GS Camera is available only with a C/CS-mount. |
| ------ | --------------------------------------------------------------------------------------------------------------------------- |

### C/CS Lenses

We recommend two lenses, a 6mm wide angle lens and a 16mm telephoto lens. These lenses should be available from your nearest [Authorised Reseller](https://www.raspberrypi.com/products/raspberry-pi-high-quality-camera/).

|                              | 16mm telephoto        | 6mm wide angle          |
| ------------------------------ | ----------------------- | ------------------------- |
| Resolution                   | 10MP                  | 3MP                     |
| Image format                 | 1"                    | 1/2"                    |
| Aperture                     | F1.4 to F16           | F1.2                    |
| Mount                        | C                     | CS                      |
| Field of View H°×V° (D°) | HQ                    | 22.2°×16.7° (27.8°) |
| GS                           | 17.8°×13.4° (22.3) | 45°×34° (56°)       |
| Back focal length            | 17.53mm               | 7.53mm                  |
| M.O.D.                       | 0.2m                  | 0.2m                    |
| Dimensions                   | φ39.00×50.00mm      | φ30×34mm              |

### M12 Lenses

![m12 lens](https://www.raspberrypi.com/documentation/accessories/images/m12-lens.jpg)

We recommend three lenses manufactured by [Gaojia Optotech](https://www.gaojiaoptotech.com/). These lenses should be available from your nearest [Authorised Reseller](https://www.raspberrypi.com/products/raspberry-pi-high-quality-camera/).

|                                 | 8mm               | 25mm                    | Fish Eye                 |
| --------------------------------- | ------------------- | ------------------------- | -------------------------- |
| Resolution                      | 12MP              | 5MP                     | 15MP                     |
| Image format                    | 1/1.7"            | 1/2"                    | 1/2.3"                   |
| Aperture                        | F1.8              | F2.4                    | F2.5                     |
| Mount                           | M12               |                         |                          |
| HQ Field of View H°×V° (D°) | 49°×36° (62°) | 14.4°×10.9° (17.9)° | 140°×102.6° (184.6°) |

## Synchronous Captures

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/accessories/camera/synchronous_cameras.adoc)

Both the HQ Camera and the Global Shutter Camera, have support for synchronous captures. Making use of the XVS pin (Vertical Sync) allows one camera to pulse when a frame capture is initiated. The other camera can then listen for this sync pulse, and capture a frame at the same time as the other camera.

### Using the HQ Camera

For correct operation, both cameras require a 1.65V pull up voltage on the XVS line, which is created by a potential divider through the 3.3V and GND pins on the Raspberry Pi.

![Image showing potential divider setup](https://www.raspberrypi.com/documentation/accessories/images/synchronous_camera_wiring.jpg?hash=d48b1400c9d450ab9166cb5ec571ab63)

Create a potential divider from two 10kΩ resistors to 3.3V and ground (to make 1.65V with an effective source impedance of 5kΩ). This can be connected to either Raspberry Pi.

Solder the GND and XVS test points of each HQ Camera board to each other.

Connect the XVS wires to the 1.65V potential divider pull-up.

#### Boot up both Raspberry Pis

The file `/sys/module/imx477/parameters/trigger_mode` determines which board outputs pulses, or waits to receive pulses (source and sink). This parameter can only be altered in superuser mode.

Run the following commands to configure the sink:

[[source,console]h]

```
$ sudo su
$ echo 2 > /sys/module/imx477/parameters/trigger_mode
$ exit
```

Run the following commands to configure the source:

```
$ sudo su
$ echo 1 > /sys/module/imx477/parameters/trigger_mode
$ exit
```

Run the following command to start the sink:

```
$ rpicam-vid --frames 300 --qt-preview -o sink.h264
```

Run the following command to start the source:

```
$ rpicam-vid --frames 300 --qt-preview -o source.h264
```

Frames should be synchronous. Use `--frames` to ensure the same number of frames are captured, and that the recordings are exactly the same length. Running the sink first ensures that no frames are missed.

| NOTE | The potential divider is needed to pull up the XVS pin to high whilst the source is in an idle state. This ensures that no frames are created or lost upon startup. The source whilst initialising goes from LOW to HIGH which can trigger a false frame. |
| ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

### Use the GS Camera

| NOTE | The Global Shutter (GS) camera can also be operated in a synchronous mode. However, the source camera will record one extra frame. A much better alternative method to ensure that both cameras capture the same amount of frames is to use the [external trigger method](https://www.raspberrypi.com/documentation/accessories/camera.html#external-trigger-on-the-gs-camera). |
| ------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

To operate as source and sink together, the Global Shutter Cameras also require connection of the XHS (horizontal sync) pins together. However, these do not need connection to a pullup resistor.

The wiring setup is identical to the [HQ Camera method](https://www.raspberrypi.com/documentation/accessories/camera.html#using-the-hq-camera), except that you will also need to connect the XHS pins together.

Create a potential divider from two 10kΩ resistors to 3.3V and ground (to make 1.65V with an effective source impedance of 5kΩ). This can be connected to either Raspberry Pi.

Solder 2 wires to the XVS test points on each board and connect both of these wires together to the 1.65V potential divider.

Solder the GND of each Camera board to each other. Also solder 2 wires to the XHS test points on each board and connect these. No pullup is needed for XHS pin.

On the boards that you wish to act as sinks, solder the two halves of the MAS pad together. This tells the sensor to act as a sink, and will wait for a signal to capture a frame.

#### Boot up source and sink

Run the following command to start the sink:

```
$ rpicam-vid --frames 300 -o sync.h264
```

Due to the limitations of the IMX296 sensor, the sink cannot record exactly the same number of frames as the source. **The source records one extra frame before the sink starts recording**. Because of this, you need to specify that the sink records one less frame with the `--frames` option.

Wait at least two seconds before you start the source.

After waiting two seconds, run the following command to start the source:

```
$ rpicam-vid --frames 299 -o sync.h264
```

Because the sink and source record a different number of frames, use `ffmpeg` to resync the videos. By dropping the first frame from the source, we then get two recordings with the same starting point and frame length:

```
$ ffmpeg -i source.h264 -vf select="gte(n\, 1)" source.h264
```

## External Trigger on the GS Camera

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/accessories/camera/external_trigger.adoc)

The Global Shutter (GS) camera can be triggered externally by pulsing the external trigger (denoted on the board as XTR) connection on the board. Multiple cameras can be connected to the same pulse, allowing for an alternative way to synchronise two cameras.

The exposure time is equal to the low pulse-width time plus an additional 14.26us. i.e. a low pulse of 10000us leads to an exposure time of 10014.26us. Framerate is directly controlled by how often you pulse the pin. A PWM frequency of 30Hz will lead to a framerate of 30 frames per second.

![Image showing pulse format](https://www.raspberrypi.com/documentation/accessories/images/external_trigger.jpg?hash=f5c22e2145d64a40b0e40fd76f643e3f)

### Preparation

| WARNING | This modification includes removing an SMD soldered part. You should not attempt this modification unless you feel you are competent to complete it. When soldering to the Camera board, please remove the plastic back cover to avoid damaging it. |
| --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

If your board has transistor Q2 fitted (shown in blue on the image below), then you will need to remove R11 from the board (shown in red). This connects GP1 to XTR and without removing R11, the camera will not operate in external trigger mode. The location of the components is displayed below.

![Image showing resistor to be removed](https://www.raspberrypi.com/documentation/accessories/images/resistor.jpg?hash=821e0afb44752644b8e2da513104f330)

Next, solder a wire to the touchpoints of XTR and GND on the GS Camera board. Note that XTR is a 1.8V input, so you may need a level shifter or potential divider.

We can use a Raspberry Pi Pico to provide the trigger. Connect any Pico GPIO pin (GP28 is used in this example) to XTR via a 1.5kΩ resistor. Also connect a 1.8kΩ resistor between XTR and GND to reduce the high logic level to 1.8V. A wiring diagram is shown below.

![Image showing Raspberry Pi Pico wiring](https://www.raspberrypi.com/documentation/accessories/images/pico_wiring.jpg?hash=bc27ec294a4d88083795db258f58aab9)

#### Boot up the Raspberry Pi with the camera connected.

Enable external triggering through superuser mode:

```
$ sudo su
$ echo 1 > /sys/module/imx296/parameters/trigger_mode
$ exit
```

#### Raspberry Pi Pico MicroPython Code

```
from machine import Pin, PWM

from time import sleep

pwm = PWM(Pin(28))

framerate = 30
shutter = 6000  # In microseconds

frame_length = 1000000 / framerate
pwm.freq(framerate)

pwm.duty_u16(int((1 - (shutter - 14) / frame_length) * 65535))
```

The low pulse width is equal to the shutter time, and the frequency of the PWM equals the framerate.

| NOTE | In this example, Pin 28 connects to the XTR touchpoint on the GS camera board. |
| ------ | -------------------------------------------------------------------------------- |

### Operation

Run the code on the Pico, and set the camera running:

```
$ rpicam-hello -t 0 --qt-preview --shutter 3000
```

Every time that the Pico pulses the pin, it should generate a frame. To control the framerate, vary the duration between pulses.

| NOTE | When running `rpicam-apps`, always specify a fixed shutter duration to ensure the AGC does not adjust the camera’s shutter speed. The duration does not matter, since it is actually controlled by the external trigger pulse. |
| ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
