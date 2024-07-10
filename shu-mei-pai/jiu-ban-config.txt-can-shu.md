# Legacy `config.txt` options

## Legacy options

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/computers/legacy_config_txt/legacy.adoc)

The `config.txt` options described here are considered legacy settings, are not used by Raspberry Pi OS Bookworm, and are no longer officially supported. They either relate to older software such as the firmware graphics driver, have been deprecated, or are very unlikely to be used by most people. However they remain documented here as they may still be of benefit to users of older OSes, or people doing bare-metal development.

## Legacy boot options

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/computers/legacy_config_txt/boot.adoc)

(See also [config.txt Boot Options](https://www.raspberrypi.com/documentation/computers/config_txt.html#boot-options).)

### `start_x`, `start_debug`

These provide a shortcut to some alternative `start_file` and `fixup_file` settings, and are the recommended methods for selecting firmware configurations.

`start_x=1` implies

```
  start_file=start_x.elf
  fixup_file=fixup_x.dat
```

On Raspberry Pi 4, if the files `start4x.elf` and `fixup4x.dat` are present, these files will be used instead.

`start_debug=1` implies

```
  start_file=start_db.elf
  fixup_file=fixup_db.dat
```

### `disable_commandline_tags`

Set the `disable_commandline_tags` command to `1` to stop `start.elf` from filling in ATAGS (memory from `0x100`) before launching the kernel.

### `arm_control`

| WARNING | This setting is deprecated. Use `arm_64bit` instead to enable 64-bit kernels. |
| --------- | -------------------------------------------------------------------- |

Sets board-specific control bits.

### `armstub`

`armstub` is the filename on the boot partition from which to load the ARM stub. The default ARM stub is stored in firmware and is selected automatically based on the Raspberry Pi model and various settings.

The stub is a small piece of ARM code that is run before the kernel. Its job is to set up low-level hardware like the interrupt controller before passing control to the kernel.

### `arm_peri_high`

Set `arm_peri_high` to `1` to enable high peripheral mode on Raspberry Pi 4. It is set automatically if a suitable DTB is loaded.

| NOTE | Enabling high peripheral mode without a compatible Device Tree will make your system fail to boot. Currently ARM stub support is missing, so you will also need to load a suitable file using `armstub`. |
| ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

### `kernel_address`

`kernel_address` is the memory address to which the kernel image should be loaded. By default, 32-bit kernels are loaded to address `0x8000`, and 64-bit kernels to address `0x200000`. If `kernel_old` is set, kernels are loaded to the address `0x0`.

### `kernel_old`

Set `kernel_old` to `1` to load the kernel to the memory address `0x0`.

### `init_uart_baud`

`init_uart_baud` is the initial UART baud rate. The default value is `115200`.

### `init_uart_clock`

`init_uart_clock` is the initial UART clock frequency. The default value is `48000000` (48MHz). Note that this clock only applies to UART0 (ttyAMA0 in Linux), and that the maximum baudrate for the UART is limited to 1/16th of the clock. The default UART on the Raspberry Pi 3 and Raspberry Pi Zero is UART1 (ttyS0 in Linux), and its clock is the core VPU clock - at least 250MHz.

### `bootcode_delay`

The `bootcode_delay` command delays for a given number of seconds in `bootcode.bin` before loading `start.elf`: the default value is `0`.

This is particularly useful to insert a delay before reading the EDID of the monitor, for example if the Raspberry Pi and monitor are powered from the same source, but the monitor takes longer to start up than the Raspberry Pi. Try setting this value if the display detection is wrong on initial boot, but is correct if you soft-reboot the Raspberry Pi without removing power from the monitor.

### `boot_delay`

The `boot_delay` command forces a wait for a given number of seconds in `start.elf` before loading the kernel: the default value is `0`. The total delay in milliseconds is calculated as `(1000 x boot_delay) + boot_delay_ms`. This can be useful if your SD card needs a while to get ready before Linux is able to boot from it.

### `boot_delay_ms`

The `boot_delay_ms` command means wait for a given number of milliseconds in `start.elf`, together with `boot_delay`, before loading the kernel. The default value is `0`.

### `enable_gic` (Raspberry Pi 4 Only)

On the Raspberry Pi 4B, if this value is set to `0` then the interrupts will be routed to the Arm cores using the legacy interrupt controller, rather than via the GIC-400. The default value is `1`.

### `sha256`

If set to non-zero, enables the logging of SHA256 hashes for loaded files (the kernel, initramfs, Device Tree .dtb file, and overlays), as generated by the `sha256sum` utility. The logging output goes to the UART if enabled, and is also accessible via `sudo vclog --msg`. This option may be useful when debugging boot problems, but at the cost of potentially adding *many* seconds to the boot time. Defaults to 0 on all platforms.

### `uart_2ndstage`

Setting `uart_2ndstage=1` causes the second-stage loader (`bootcode.bin` on devices prior to the Raspberry Pi 4, or the boot code in the EEPROM for Raspberry Pi 4 devices) and the main firmware (`start*.elf`) to output diagnostic information to UART0.

Be aware that output is likely to interfere with Bluetooth operation unless it is disabled (`dtoverlay=disable-bt`) or switched to the other UART (`dtoverlay=miniuart-bt`), and if the UART is accessed simultaneously to output from Linux, then data loss can occur leading to corrupted output. This feature should only be required when trying to diagnose an early boot loading problem.

### `upstream_kernel`

If `upstream_kernel=1` is used, the firmware sets [`os\_prefix`](https://www.raspberrypi.com/documentation/computers/config_txt.html#os_prefix) to "upstream/", unless it has been explicitly set to something else, but like other `os_prefix` values it will be ignored if the required kernel and .dtb file can’t be found when using the prefix.

The firmware will also prefer upstream Linux names for DTBs (`bcm2837-rpi-3-b.dtb` instead of `bcm2710-rpi-3-b.dtb`, for example). If the upstream file isn’t found the firmware will load the downstream variant instead and automatically apply the "upstream" overlay to make some adjustments. Note that this process happens *after* the `os_prefix` has been finalised.

## Legacy GPIO control

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/computers/legacy_config_txt/gpio.adoc)

(See also [config.txt GPIO control](https://www.raspberrypi.com/documentation/computers/config_txt.html#gpio-control).)

### `enable_jtag_gpio`

Setting `enable_jtag_gpio=1` selects Alt4 mode for GPIO pins 22-27, and sets up some internal SoC connections, enabling the JTAG interface for the Arm CPU. It works on all models of Raspberry Pi.

| Pin #  | Function     |
| -------- | -------------- |
| GPIO22 | ARM\_TRST |
| GPIO23 | ARM\_RTCK |
| GPIO24 | ARM\_TDO  |
| GPIO25 | ARM\_TCK  |
| GPIO26 | ARM\_TDI  |
| GPIO27 | ARM\_TMS  |

## Legacy overclocking options

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/computers/legacy_config_txt/overclocking.adoc)

(See also [config.txt overclocking options](https://www.raspberrypi.com/documentation/computers/config_txt.html#overclocking-options).)

### Overclocking

#### `never_over_voltage`

Sets a bit in the one-time programmable (OTP) memory that prevents the device from being overvoltaged. This is intended to lock the Raspberry Pi down so the warranty bit cannot be set either inadvertently or maliciously by using an invalid overvoltage.

#### `disable_auto_turbo`

On Raspberry Pi 2 and 3, setting this flag will disable the GPU from moving into turbo mode, which it can do under particular loads.

## Legacy conditional filters

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/computers/legacy_config_txt/conditional.adoc)

(See also [config.txt conditional filters](https://www.raspberrypi.com/documentation/computers/config_txt.html#conditional-filters).)

### The `[HDMI:*]` filter

| NOTE | This filter is for Raspberry Pi 4 only. |
| ------ | ----------------------------------------- |

Raspberry Pi 4 has two HDMI ports, and for many `config.txt` commands related to HDMI, it is necessary to specify which HDMI port is being referred to. The HDMI conditional filters subsequent HDMI configurations to the specific port.

```
 [HDMI:0]
   hdmi_group=2
   hdmi_mode=45
 [HDMI:1]
   hdmi_group=2
   hdmi_mode=67
```

An alternative `variable:index` syntax is available on all port-specific HDMI commands. You could use the following, which is the same as the previous example:

```
 hdmi_group:0=2
 hdmi_mode:0=45
 hdmi_group:1=2
 hdmi_mode:1=67
```

## Legacy memory options

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/computers/legacy_config_txt/memory.adoc)

(see also [config.txt Memory Options](https://www.raspberrypi.com/documentation/computers/config_txt.html#memory-options))

| NOTE | Raspberry Pi 5 does not allocate GPU memory on behalf of the OS, so the following settings have no effect. |
| ------ | ------------------------------------------------------------------------------------------------------------ |

### `gpu_mem`

Specifies how much memory, in megabytes, to reserve for the exclusive use of the GPU: the remaining memory is allocated to the Arm CPU for use by the OS. For Raspberry Pis with less than 1GB of memory, the default is `64`; for Raspberry Pis with 1GB or more of memory the default is `76`.

| IMPORTANT | Unlike GPUs found on x86 machines, where increasing memory can improve 3D performance, the architecture of the VideoCore means **there is no performance advantage from specifying values larger than is necessary**, and doing this can in fact harm performance. |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

To ensure the best performance of Linux, you should set `gpu_mem` to the lowest possible value. If a particular graphics feature is not working correctly, try increasing the value of `gpu_mem`, being mindful of the recommended maximums shown below.

On Raspberry Pi 4 the 3D component of the GPU has its own memory management unit (MMU), and does not use memory from the `gpu_mem` allocation. Instead memory is allocated dynamically within Linux. This allows a smaller value to be specified for `gpu_mem` on the Raspberry Pi 4, compared to previous models.

On legacy kernels, the memory allocated to the GPU is used for display, 3D, codec and camera purposes as well as some basic firmware housekeeping. The maximums specified below assume you are using all these features. If you are not, then smaller values of gpu_mem should be used.

The recommended maximum values are as follows:

| total RAM      | `gpu_mem` recommended maximum     |
| ---------------- | -------------------------- |
| 256MB          | `128`                         |
| 512MB          | `384`                         |
| 1GB or greater | `512`, `76` on the Raspberry Pi 4 |

| IMPORTANT | The camera stack (libcamera) on Raspberry Pi OS uses Linux CMA memory to allocate buffers instead of GPU memory, so there is no benefit in increasing the GPU memory size. |
| ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

It is possible to set `gpu_mem` to larger values, however this should be avoided since it can cause problems, such as preventing Linux from booting. The minimum value is `16`, however this disables certain GPU features.

You can also use `gpu_mem_256`, `gpu_mem_512`, and `gpu_mem_1024` to allow swapping the same SD card between Raspberry Pis with different amounts of RAM without having to edit `config.txt` each time:

### `gpu_mem_256`

The `gpu_mem_256` command sets the GPU memory in megabytes for Raspberry Pis with 256MB of memory. It is ignored if memory size is not 256MB. This overrides `gpu_mem`.

### `gpu_mem_512`

The `gpu_mem_512` command sets the GPU memory in megabytes for Raspberry Pis with 512MB of memory. It is ignored if memory size is not 512MB. This overrides `gpu_mem`.

### `gpu_mem_1024`

The `gpu_mem_1024` command sets the GPU memory in megabytes for Raspberry Pis with 1GB or more of memory. It is ignored if memory size is smaller than 1GB. This overrides `gpu_mem`.

### `disable_l2cache`

Setting this to `1` disables the CPU’s access to the GPU’s L2 cache and requires a corresponding L2 disabled kernel. Default value on BCM2835 is `0`. On BCM2836, BCM2837, BCM2711, and BCM2712, the ARMs have their own L2 cache and therefore the default is `1`. The standard Raspberry Pi `kernel.img` and `kernel7.img` builds reflect this difference in cache setting.

## Legacy video options

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/computers/legacy_config_txt/video.adoc)

(see also [config.txt Video Options](https://www.raspberrypi.com/documentation/computers/config_txt.html#video-options))

### HDMI mode

| NOTE | Because Raspberry Pi 4 and Raspberry Pi 400 have two HDMI ports, some HDMI commands can be applied to either port. You can use the syntax `<command>:<port>`, where port is 0 or 1, to specify which port the setting should apply to. If no port is specified, the default is 0. If you specify a port number on a command that does not require a port number, the port is ignored. Further details on the syntax and alternative mechanisms can be found in the HDMI sub-section of the [conditionals section](https://www.raspberrypi.com/documentation/computers/legacy_config_txt.html#legacy-conditional-filters) of the documentation. |
| ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

#### `hdmi_safe`

Setting `hdmi_safe` to `1` will lead to "safe mode" settings being used to try to boot with maximum HDMI compatibility. This is the same as setting the following parameters:

```
hdmi_force_hotplug=1
hdmi_ignore_edid=0xa5000080
config_hdmi_boost=4
hdmi_group=2
hdmi_mode=4
disable_overscan=0
overscan_left=24
overscan_right=24
overscan_top=24
overscan_bottom=24
```

#### `hdmi_ignore_edid`

Setting `hdmi_ignore_edid` to `0xa5000080` enables the ignoring of EDID/display data if your display does not have an accurate [EDID](https://en.wikipedia.org/wiki/Extended_display_identification_data). It requires this unusual value to ensure that it is not triggered accidentally.

#### `hdmi_edid_file`

Setting `hdmi_edid_file` to `1` will cause the GPU to read EDID data from the `edid.dat` file, located in the boot partition, instead of reading it from the monitor.

#### `hdmi_edid_filename`

On the Raspberry Pi 4B, you can use the `hdmi_edid_filename` command to specify the filename of the EDID file to use, and also to specify which port the file is to be applied to. This also requires `hdmi_edid_file=1` to enable EDID files.

For example:

```
hdmi_edid_file=1
hdmi_edid_filename:0=FileForPortZero.edid
hdmi_edid_filename:1=FileForPortOne.edid
```

#### `hdmi_force_edid_audio`

Setting `hdmi_force_edid_audio` to `1` pretends that all audio formats are supported by the display, allowing passthrough of DTS/AC3 even when this is not reported as supported.

#### `hdmi_ignore_edid_audio`

Setting `hdmi_ignore_edid_audio` to `1` pretends that all audio formats are unsupported by the display. This means ALSA will default to the analogue audio (headphone) jack.

#### `hdmi_force_edid_3d`

Setting `hdmi_force_edid_3d` to `1` pretends that all CEA modes support 3D, even when the EDID does not indicate support for this.

#### `hdmi_ignore_cec_init`

Setting `hdmi_ignore_cec_init` to `1` will stop the initial active source message being sent during bootup. This prevents a CEC-enabled TV from coming out of standby and channel-switching when you are rebooting your Raspberry Pi.

#### `hdmi_ignore_cec`

Setting `hdmi_ignore_cec` to `1` pretends that [CEC](https://en.wikipedia.org/wiki/Consumer_Electronics_Control#CEC) is not supported at all by the display. No CEC functions will be supported.

#### `cec_osd_name`

The `cec_osd_name` command sets the initial CEC name of the device. The default is Raspberry Pi.

#### `hdmi_pixel_encoding`

The `hdmi_pixel_encoding` command forces the pixel encoding mode. By default, it will use the mode requested from the EDID, so you shouldn’t need to change it.

| hdmi\_pixel\_encoding | result                                          |
| ----------------------------- | ------------------------------------------------- |
| 0                           | default (RGB limited for CEA, RGB full for DMT) |
| 1                           | RGB limited (16-235)                            |
| 2                           | RGB full (0-255)                                |
| 3                           | YCbCr limited (16-235)                          |
| 4                           | YCbCr full (0-255)                              |

#### `hdmi_max_pixel_freq`

The pixel frequency is used by the firmware and KMS to filter HDMI modes. Note, this is not the same as the frame rate. It specifies the maximum frequency that a valid mode can have, thereby culling out higher frequency modes. So for example, if you wish to disable all 4K modes, you could specify a maximum frequency of 200000000, since all 4K modes have frequencies greater than this.

#### `hdmi_blanking`

The `hdmi_blanking` command controls what happens when the operating system asks for the display to be put into standby mode, using DPMS, to save power. If this option is not set or set to 0, the HDMI output is blanked but not switched off. In order to mimic the behaviour of other computers, you can set the HDMI output to switch off as well by setting this option to 1: the attached display will go into a low-power standby mode.

| NOTE | On Raspberry Pi 4, setting `hdmi_blanking=1` will not cause the HDMI output to be switched off, since this feature has not yet been implemented. This feature may cause issues when using applications which don’t use the framebuffer, such as `omxplayer`. |
| ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

| hdmi\_blanking | result                                       |
| ------------------- | ---------------------------------------------- |
| 0                 | HDMI output will be blanked                  |
| 1                 | HDMI output will be switched off and blanked |

#### `hdmi_drive`

The `hdmi_drive` command allows you to choose between HDMI and DVI output modes.

| hdmi\_drive | result                                                         |
| ---------------- | ---------------------------------------------------------------- |
| 1              | Normal DVI mode (no sound)                                     |
| 2              | Normal HDMI mode (sound will be sent if supported and enabled) |

#### `config_hdmi_boost`

Configures the signal strength of the HDMI interface. The minimum value is `0` and the maximum is `11`.

The default value for the original Model B and A is `2`. The default value for the Model B+ and all later models is `5`.

If you are seeing HDMI issues (speckling, interference) then try `7`. Very long HDMI cables may need up to `11`, but values this high should not be used unless absolutely necessary.

This option is ignored on Raspberry Pi 4.

#### `hdmi_group`

The `hdmi_group` command defines the HDMI output group to be either CEA (Consumer Electronics Association, the standard typically used by TVs) or DMT (Display Monitor Timings, the standard typically used by monitors). This setting should be used in conjunction with `hdmi_mode`.

| hdmi\_group | result                |
| ---------------- | ----------------------- |
| 0              | Auto-detect from EDID |
| 1              | CEA                   |
| 2              | DMT                   |

#### `hdmi_mode`

Together with `hdmi_group`, `hdmi_mode` defines the HDMI output format. Format mode numbers are derived from the [CTA specification](https://web.archive.org/web/20171201033424/https://standards.cta.tech/kwspub/published_docs/CTA-861-G_FINAL_revised_2017.pdf).

| NOTE | Not all modes are available on all models. |
| ------ | -------------------------------------------- |

These values are valid if `hdmi_group=1` (CEA):

| hdmi\_mode | Resolution    | Frequency | Screen aspect | Notes             |
| --------------- | --------------- | ----------- | --------------- | ------------------- |
| 1             | VGA (640x480) | 60Hz      | 4:3           |                   |
| 2             | 480p          | 60Hz      | 4:3           |                   |
| 3             | 480p          | 60Hz      | 16:9          |                   |
| 4             | 720p          | 60Hz      | 16:9          |                   |
| 5             | 1080i         | 60Hz      | 16:9          |                   |
| 6             | 480i          | 60Hz      | 4:3           |                   |
| 7             | 480i          | 60Hz      | 16:9          |                   |
| 8             | 240p          | 60Hz      | 4:3           |                   |
| 9             | 240p          | 60Hz      | 16:9          |                   |
| 10            | 480i          | 60Hz      | 4:3           | pixel quadrupling |
| 11            | 480i          | 60Hz      | 16:9          | pixel quadrupling |
| 12            | 240p          | 60Hz      | 4:3           | pixel quadrupling |
| 13            | 240p          | 60Hz      | 16:9          | pixel quadrupling |
| 14            | 480p          | 60Hz      | 4:3           | pixel doubling    |
| 15            | 480p          | 60Hz      | 16:9          | pixel doubling    |
| 16            | 1080p         | 60Hz      | 16:9          |                   |
| 17            | 576p          | 50Hz      | 4:3           |                   |
| 18            | 576p          | 50Hz      | 16:9          |                   |
| 19            | 720p          | 50Hz      | 16:9          |                   |
| 20            | 1080i         | 50Hz      | 16:9          |                   |
| 21            | 576i          | 50Hz      | 4:3           |                   |
| 22            | 576i          | 50Hz      | 16:9          |                   |
| 23            | 288p          | 50Hz      | 4:3           |                   |
| 24            | 288p          | 50Hz      | 16:9          |                   |
| 25            | 576i          | 50Hz      | 4:3           | pixel quadrupling |
| 26            | 576i          | 50Hz      | 16:9          | pixel quadrupling |
| 27            | 288p          | 50Hz      | 4:3           | pixel quadrupling |
| 28            | 288p          | 50Hz      | 16:9          | pixel quadrupling |
| 29            | 576p          | 50Hz      | 4:3           | pixel doubling    |
| 30            | 576p          | 50Hz      | 16:9          | pixel doubling    |
| 31            | 1080p         | 50Hz      | 16:9          |                   |
| 32            | 1080p         | 24Hz      | 16:9          |                   |
| 33            | 1080p         | 25Hz      | 16:9          |                   |
| 34            | 1080p         | 30Hz      | 16:9          |                   |
| 35            | 480p          | 60Hz      | 4:3           | pixel quadrupling |
| 36            | 480p          | 60Hz      | 16:9          | pixel quadrupling |
| 37            | 576p          | 50Hz      | 4:3           | pixel quadrupling |
| 38            | 576p          | 50Hz      | 16:9          | pixel quadrupling |
| 39            | 1080i         | 50Hz      | 16:9          | reduced blanking  |
| 40            | 1080i         | 100Hz     | 16:9          |                   |
| 41            | 720p          | 100Hz     | 16:9          |                   |
| 42            | 576p          | 100Hz     | 4:3           |                   |
| 43            | 576p          | 100Hz     | 16:9          |                   |
| 44            | 576i          | 100Hz     | 4:3           |                   |
| 45            | 576i          | 100Hz     | 16:9          |                   |
| 46            | 1080i         | 120Hz     | 16:9          |                   |
| 47            | 720p          | 120Hz     | 16:9          |                   |
| 48            | 480p          | 120Hz     | 4:3           |                   |
| 49            | 480p          | 120Hz     | 16:9          |                   |
| 50            | 480i          | 120Hz     | 4:3           |                   |
| 51            | 480i          | 120Hz     | 16:9          |                   |
| 52            | 576p          | 200Hz     | 4:3           |                   |
| 53            | 576p          | 200Hz     | 16:9          |                   |
| 54            | 576i          | 200Hz     | 4:3           |                   |
| 55            | 576i          | 200Hz     | 16:9          |                   |
| 56            | 480p          | 240Hz     | 4:3           |                   |
| 57            | 480p          | 240Hz     | 16:9          |                   |
| 58            | 480i          | 240Hz     | 4:3           |                   |
| 59            | 480i          | 240Hz     | 16:9          |                   |
| 60            | 720p          | 24Hz      | 16:9          |                   |
| 61            | 720p          | 25Hz      | 16:9          |                   |
| 62            | 720p          | 30Hz      | 16:9          |                   |
| 63            | 1080p         | 120Hz     | 16:9          |                   |
| 64            | 1080p         | 100Hz     | 16:9          |                   |
| 65            | Custom        |           |               |                   |
| 66            | 720p          | 25Hz      | 64:27         | Pi 4              |
| 67            | 720p          | 30Hz      | 64:27         | Pi 4              |
| 68            | 720p          | 50Hz      | 64:27         | Pi 4              |
| 69            | 720p          | 60Hz      | 64:27         | Pi 4              |
| 70            | 720p          | 100Hz     | 64:27         | Pi 4              |
| 71            | 720p          | 120Hz     | 64:27         | Pi 4              |
| 72            | 1080p         | 24Hz      | 64:27         | Pi 4              |
| 73            | 1080p         | 25Hz      | 64:27         | Pi 4              |
| 74            | 1080p         | 30Hz      | 64:27         | Pi 4              |
| 75            | 1080p         | 50Hz      | 64:27         | Pi 4              |
| 76            | 1080p         | 60Hz      | 64:27         | Pi 4              |
| 77            | 1080p         | 100Hz     | 64:27         | Pi 4              |
| 78            | 1080p         | 120Hz     | 64:27         | Pi 4              |
| 79            | 1680x720      | 24Hz      | 64:27         | Pi 4              |
| 80            | 1680x720      | 25z       | 64:27         | Pi 4              |
| 81            | 1680x720      | 30Hz      | 64:27         | Pi 4              |
| 82            | 1680x720      | 50Hz      | 64:27         | Pi 4              |
| 83            | 1680x720      | 60Hz      | 64:27         | Pi 4              |
| 84            | 1680x720      | 100Hz     | 64:27         | Pi 4              |
| 85            | 1680x720      | 120Hz     | 64:27         | Pi 4              |
| 86            | 2560x720      | 24Hz      | 64:27         | Pi 4              |
| 87            | 2560x720      | 25Hz      | 64:27         | Pi 4              |
| 88            | 2560x720      | 30Hz      | 64:27         | Pi 4              |
| 89            | 2560x720      | 50Hz      | 64:27         | Pi 4              |
| 90            | 2560x720      | 60Hz      | 64:27         | Pi 4              |
| 91            | 2560x720      | 100Hz     | 64:27         | Pi 4              |
| 92            | 2560x720      | 120Hz     | 64:27         | Pi 4              |
| 93            | 2160p         | 24Hz      | 16:9          | Pi 4              |
| 94            | 2160p         | 25Hz      | 16:9          | Pi 4              |
| 95            | 2160p         | 30Hz      | 16:9          | Pi 4              |
| 96            | 2160p         | 50Hz      | 16:9          | Pi 4              |
| 97            | 2160p         | 60Hz      | 16:9          | Pi 4              |
| 98            | 4096x2160     | 24Hz      | 256:135       | Pi 4              |
| 99            | 4096x2160     | 25Hz      | 256:135       | Pi 4              |
| 100           | 4096x2160     | 30Hz      | 256:135       | Pi 4              |
| 101           | 4096x2160     | 50Hz      | 256:135       | Pi 4[^](https://www.raspberrypi.com/documentation/computers/legacy_config_txt.html#needsoverclock)​**[1](https://www.raspberrypi.com/documentation/computers/legacy_config_txt.html#needsoverclock)**​[^](https://www.raspberrypi.com/documentation/computers/legacy_config_txt.html#needsoverclock)              |
| 102           | 4096x2160     | 60Hz      | 256:135       | Pi 4[^](https://www.raspberrypi.com/documentation/computers/legacy_config_txt.html#needsoverclock)​**[1](https://www.raspberrypi.com/documentation/computers/legacy_config_txt.html#needsoverclock)**​[^](https://www.raspberrypi.com/documentation/computers/legacy_config_txt.html#needsoverclock)              |
| 103           | 2160p         | 24Hz      | 64:27         | Pi 4              |
| 104           | 2160p         | 25Hz      | 64:27         | Pi 4              |
| 105           | 2160p         | 30Hz      | 64:27         | Pi 4              |
| 106           | 2160p         | 50Hz      | 64:27         | Pi 4              |
| 107           | 2160p         | 60Hz      | 64:27         | Pi 4              |

**1.**  Only available with an overclocked core frequency: set `core_freq_min=600` and `core_freq=600`. See [overclocking](https://www.raspberrypi.com/documentation/computers/config_txt.html#overclocking).

Pixel doubling and quadrupling indicates a higher clock rate, with each pixel repeated two or four times respectively.

These values are valid if `hdmi_group=2` (DMT):

| hdmi\_mode | Resolution | Frequency | Screen Aspect | Notes                          |
| --------------- | ------------ | ----------- | --------------- | -------------------------------- |
| 1             | 640x350    | 85Hz      |               |                                |
| 2             | 640x400    | 85Hz      | 16:10         |                                |
| 3             | 720x400    | 85Hz      |               |                                |
| 4             | 640x480    | 60Hz      | 4:3           |                                |
| 5             | 640x480    | 72Hz      | 4:3           |                                |
| 6             | 640x480    | 75Hz      | 4:3           |                                |
| 7             | 640x480    | 85Hz      | 4:3           |                                |
| 8             | 800x600    | 56Hz      | 4:3           |                                |
| 9             | 800x600    | 60Hz      | 4:3           |                                |
| 10            | 800x600    | 72Hz      | 4:3           |                                |
| 11            | 800x600    | 75Hz      | 4:3           |                                |
| 12            | 800x600    | 85Hz      | 4:3           |                                |
| 13            | 800x600    | 120Hz     | 4:3           |                                |
| 14            | 848x480    | 60Hz      | 16:9          |                                |
| 15            | 1024x768   | 43Hz      | 4:3           | incompatible with Raspberry Pi |
| 16            | 1024x768   | 60Hz      | 4:3           |                                |
| 17            | 1024x768   | 70Hz      | 4:3           |                                |
| 18            | 1024x768   | 75Hz      | 4:3           |                                |
| 19            | 1024x768   | 85Hz      | 4:3           |                                |
| 20            | 1024x768   | 120Hz     | 4:3           |                                |
| 21            | 1152x864   | 75Hz      | 4:3           |                                |
| 22            | 1280x768   | 60Hz      | 15:9          | reduced blanking               |
| 23            | 1280x768   | 60Hz      | 15:9          |                                |
| 24            | 1280x768   | 75Hz      | 15:9          |                                |
| 25            | 1280x768   | 85Hz      | 15:9          |                                |
| 26            | 1280x768   | 120Hz     | 15:9          | reduced blanking               |
| 27            | 1280x800   | 60        | 16:10         | reduced blanking               |
| 28            | 1280x800   | 60Hz      | 16:10         |                                |
| 29            | 1280x800   | 75Hz      | 16:10         |                                |
| 30            | 1280x800   | 85Hz      | 16:10         |                                |
| 31            | 1280x800   | 120Hz     | 16:10         | reduced blanking               |
| 32            | 1280x960   | 60Hz      | 4:3           |                                |
| 33            | 1280x960   | 85Hz      | 4:3           |                                |
| 34            | 1280x960   | 120Hz     | 4:3           | reduced blanking               |
| 35            | 1280x1024  | 60Hz      | 5:4           |                                |
| 36            | 1280x1024  | 75Hz      | 5:4           |                                |
| 37            | 1280x1024  | 85Hz      | 5:4           |                                |
| 38            | 1280x1024  | 120Hz     | 5:4           | reduced blanking               |
| 39            | 1360x768   | 60Hz      | 16:9          |                                |
| 40            | 1360x768   | 120Hz     | 16:9          | reduced blanking               |
| 41            | 1400x1050  | 60Hz      | 4:3           | reduced blanking               |
| 42            | 1400x1050  | 60Hz      | 4:3           |                                |
| 43            | 1400x1050  | 75Hz      | 4:3           |                                |
| 44            | 1400x1050  | 85Hz      | 4:3           |                                |
| 45            | 1400x1050  | 120Hz     | 4:3           | reduced blanking               |
| 46            | 1440x900   | 60Hz      | 16:10         | reduced blanking               |
| 47            | 1440x900   | 60Hz      | 16:10         |                                |
| 48            | 1440x900   | 75Hz      | 16:10         |                                |
| 49            | 1440x900   | 85Hz      | 16:10         |                                |
| 50            | 1440x900   | 120Hz     | 16:10         | reduced blanking               |
| 51            | 1600x1200  | 60Hz      | 4:3           |                                |
| 52            | 1600x1200  | 65Hz      | 4:3           |                                |
| 53            | 1600x1200  | 70Hz      | 4:3           |                                |
| 54            | 1600x1200  | 75Hz      | 4:3           |                                |
| 55            | 1600x1200  | 85Hz      | 4:3           |                                |
| 56            | 1600x1200  | 120Hz     | 4:3           | reduced blanking               |
| 57            | 1680x1050  | 60Hz      | 16:10         | reduced blanking               |
| 58            | 1680x1050  | 60Hz      | 16:10         |                                |
| 59            | 1680x1050  | 75Hz      | 16:10         |                                |
| 60            | 1680x1050  | 85Hz      | 16:10         |                                |
| 61            | 1680x1050  | 120Hz     | 16:10         | reduced blanking               |
| 62            | 1792x1344  | 60Hz      | 4:3           |                                |
| 63            | 1792x1344  | 75Hz      | 4:3           |                                |
| 64            | 1792x1344  | 120Hz     | 4:3           | reduced blanking               |
| 65            | 1856x1392  | 60Hz      | 4:3           |                                |
| 66            | 1856x1392  | 75Hz      | 4:3           |                                |
| 67            | 1856x1392  | 120Hz     | 4:3           | reduced blanking               |
| 68            | 1920x1200  | 60Hz      | 16:10         | reduced blanking               |
| 69            | 1920x1200  | 60Hz      | 16:10         |                                |
| 70            | 1920x1200  | 75Hz      | 16:10         |                                |
| 71            | 1920x1200  | 85Hz      | 16:10         |                                |
| 72            | 1920x1200  | 120Hz     | 16:10         | reduced blanking               |
| 73            | 1920x1440  | 60Hz      | 4:3           |                                |
| 74            | 1920x1440  | 75Hz      | 4:3           |                                |
| 75            | 1920x1440  | 120Hz     | 4:3           | reduced blanking               |
| 76            | 2560x1600  | 60Hz      | 16:10         | reduced blanking               |
| 77            | 2560x1600  | 60Hz      | 16:10         |                                |
| 78            | 2560x1600  | 75Hz      | 16:10         |                                |
| 79            | 2560x1600  | 85Hz      | 16:10         |                                |
| 80            | 2560x1600  | 120Hz     | 16:10         | reduced blanking               |
| 81            | 1366x768   | 60Hz      | 16:9          | [NOT on Raspberry Pi 4](https://www.raspberrypi.com/documentation/computers/config_txt.html#hdmi-pipeline-for-raspberry-pi-4)                               |
| 82            | 1920x1080  | 60Hz      | 16:9          | 1080p                          |
| 83            | 1600x900   | 60Hz      | 16:9          | reduced blanking               |
| 84            | 2048x1152  | 60Hz      | 16:9          | reduced blanking               |
| 85            | 1280x720   | 60Hz      | 16:9          | 720p                           |
| 86            | 1366x768   | 60Hz      | 16:9          | reduced blanking               |

| NOTE | There is a pixel clock limit. The highest supported mode on models prior to the Raspberry Pi 4 is 1920×1200 at 60Hz with reduced blanking, whilst the Raspberry Pi 4 can support up to 4096×2160 (colloquially 4k) at 60Hz. Also note that if you are using both HDMI ports of the Raspberry Pi 4 for 4k output, then you are limited to 30Hz on both. |
| ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

#### `hdmi_timings`

This allows setting of raw HDMI timing values for a custom mode, selected using `hdmi_group=2` and `hdmi_mode=87`.

```
hdmi_timings=<h_active_pixels> <h_sync_polarity> <h_front_porch> <h_sync_pulse> <h_back_porch> <v_active_lines> <v_sync_polarity> <v_front_porch> <v_sync_pulse> <v_back_porch> <v_sync_offset_a> <v_sync_offset_b> <pixel_rep> <frame_rate> <interlaced> <pixel_freq> <aspect_ratio>
```

```
<h_active_pixels> = horizontal pixels (width)
<h_sync_polarity> = invert hsync polarity
<h_front_porch>   = horizontal forward padding from DE active edge
<h_sync_pulse>    = hsync pulse width in pixel clocks
<h_back_porch>    = vertical back padding from DE active edge
<v_active_lines>  = vertical pixels height (lines)
<v_sync_polarity> = invert vsync polarity
<v_front_porch>   = vertical forward padding from DE active edge
<v_sync_pulse>    = vsync pulse width in pixel clocks
<v_back_porch>    = vertical back padding from DE active edge
<v_sync_offset_a> = leave at zero
<v_sync_offset_b> = leave at zero
<pixel_rep>       = leave at zero
<frame_rate>      = screen refresh rate in Hz
<interlaced>      = leave at zero
<pixel_freq>      = clock frequency (h_active_pixels + h_front_porch + h_sync_pulse + h_back_porch)
                                    * (v_active_lines + v_front_porch + v_sync_pulse + v_back_porch)
                                    * framerate
<aspect_ratio>    = [see footnote]
```

The aspect ratio can be set to one of eight values. Choose a value representing the aspect ratio most similar to your screen from the following:

| Aspect Ratio | Name                          | Value |
| -------------- | ------------------------------- | ------- |
| 4:3          | HDMI\_ASPECT\_4\_3   | 1     |
| 14:9         | HDMI\_ASPECT\_14\_9  | 2     |
| 16:9         | HDMI\_ASPECT\_16\_9  | 3     |
| 5:4          | HDMI\_ASPECT\_5\_4   | 4     |
| 16:10        | HDMI\_ASPECT\_16\_10 | 5     |
| 15:9         | HDMI\_ASPECT\_15\_9  | 6     |
| 21:9         | HDMI\_ASPECT\_21\_9  | 7     |
| 64:27        | HDMI\_ASPECT\_64\_27 | 8     |

#### `hdmi_force_mode`

Setting to `1` will remove all other modes except the ones specified by `hdmi_mode` and `hdmi_group` from the internal list, meaning they will not appear in any enumerated lists of modes. This option may help if a display seems to be ignoring the `hdmi_mode` and `hdmi_group` settings.

#### `edid_content_type`

Forces the EDID content type to a specific value.

The options are:

* `0` = `EDID_ContentType_NODATA`, content type none
* `1` = `EDID_ContentType_Graphics`, content type graphics, ITC must be set to 1
* `2` = `EDID_ContentType_Photo`, content type photo
* `3` = `EDID_ContentType_Cinema`, content type cinema
* `4` = `EDID_ContentType_Game`, content type game

### Which values are valid for my monitor?

Your HDMI monitor may only support a limited set of formats. To find out which formats are supported, use the following method:

* Set the output format to VGA 60Hz (`hdmi_group=1` and `hdmi_mode=1`) and boot up your Raspberry Pi
* Enter the following command to give a list of CEA-supported modes: `/opt/vc/bin/tvservice -m CEA`
* Enter the following command to give a list of DMT-supported modes: `/opt/vc/bin/tvservice -m DMT`
* Enter the following command to show your current state: `/opt/vc/bin/tvservice -s`
* Enter the following commands to dump more detailed information from your monitor: `/opt/vc/bin/tvservice -d edid.dat; /opt/vc/bin/edidparser edid.dat`

The `edid.dat` should also be provided when troubleshooting problems with the default HDMI mode.

### Custom mode

If your monitor requires a mode that is not in one of the tables above, then it’s possible to define a custom CVT mode for it instead:

```
hdmi_cvt=<width> <height> <framerate> <aspect> <margins> <interlace> <rb>
```

| Value     | Default    | Description                                                                        |
| ----------- | ------------ | ------------------------------------------------------------------------------------ |
| width     | (required) | width in pixels                                                                    |
| height    | (required) | height in pixels                                                                   |
| framerate | (required) | framerate in Hz                                                                    |
| aspect    | 3          | aspect ratio 1\=4:3, 2\=14:9, 3\=16:9, 4\=5:4, 5\=16:10, 6\=15:9 |
| margins   | 0          | 0\=margins disabled, 1\=margins enabled                                      |
| interlace | 0          | 0\=progressive, 1\=interlaced                                                |
| rb        | 0          | 0\=normal, 1\=reduced blanking                                               |

Fields at the end can be omitted to use the default values.

Note that this simply **creates** the mode (group 2 mode 87). In order to make the Raspberry Pi use this by default, you must add some additional settings. For example, to select an 800×480 resolution and enable audio drive:

```
hdmi_cvt=800 480 60 6
hdmi_group=2
hdmi_mode=87
hdmi_drive=2
```

This may not work if your monitor does not support standard CVT timings.

### Composite video mode

#### `sdtv_mode`

The `sdtv_mode` command defines the TV standard used for composite video output:

| sdtv\_mode | result                                                                        |
| --------------- | ------------------------------------------------------------------------------- |
| 0 (default)   | Normal NTSC                                                                   |
| 1             | Japanese version of NTSC — no pedestal                                     |
| 2             | Normal PAL                                                                    |
| 3             | Brazilian version of PAL — 525/60 rather than 625/50, different subcarrier |
| 16            | Progressive scan NTSC                                                         |
| 18            | Progressive scan PAL                                                          |

#### `sdtv_aspect`

The `sdtv_aspect` command defines the aspect ratio for composite video output. The default value is `1`.

| sdtv\_aspect | result |
| ----------------- | -------- |
| 1               | 4:3    |
| 2               | 14:9   |
| 3               | 16:9   |

#### `sdtv_disable_colourburst`

Setting `sdtv_disable_colourburst` to `1` disables colourburst on composite video output. The picture will be displayed in monochrome, but it may appear sharper.

### LCD displays and touchscreens

#### `display_default_lcd`

If a Raspberry Pi Touch Display is detected it will be used as the default display and will show the framebuffer. Setting `display_default_lcd=0` will ensure the LCD is not the default display, which usually implies the HDMI output will be the default. The LCD can still be used by choosing its display number from supported applications, for example, omxplayer.

#### `lcd_framerate`

Specify the framerate of the Raspberry Pi Touch Display, in Hz/fps. Defaults to 60Hz.

#### `lcd_rotate`

This flips the display using the LCD’s inbuilt flip functionality, which is a computationally cheaper operation than using the GPU-based rotate operation.

For example, `lcd_rotate=2` will compensate for an upside-down display.

#### `enable_dpi_lcd`

Enable LCD displays attached to the DPI GPIOs. This is to allow the use of third-party LCD displays using the parallel display interface.

#### `dpi_group`, `dpi_mode`, `dpi_output_format`

The `dpi_group` and `dpi_mode` `config.txt` parameters are used to set either predetermined modes (DMT or CEA modes as used by HDMI above). A user can generate custom modes in much the same way as for HDMI (see `dpi_timings` section).

`dpi_output_format` is a bitmask specifying various parameters used to set up the display format.

#### `dpi_timings`

This allows setting of raw DPI timing values for a custom mode, selected using `dpi_group=2` and `dpi_mode=87`.

```
dpi_timings=<h_active_pixels> <h_sync_polarity> <h_front_porch> <h_sync_pulse> <h_back_porch> <v_active_lines> <v_sync_polarity> <v_front_porch> <v_sync_pulse> <v_back_porch> <v_sync_offset_a> <v_sync_offset_b> <pixel_rep> <frame_rate> <interlaced> <pixel_freq> <aspect_ratio>
```

```
<h_active_pixels> = horizontal pixels (width)
<h_sync_polarity> = invert hsync polarity
<h_front_porch>   = horizontal forward padding from DE active edge
<h_sync_pulse>    = hsync pulse width in pixel clocks
<h_back_porch>    = vertical back padding from DE active edge
<v_active_lines>  = vertical pixels height (lines)
<v_sync_polarity> = invert vsync polarity
<v_front_porch>   = vertical forward padding from DE active edge
<v_sync_pulse>    = vsync pulse width in pixel clocks
<v_back_porch>    = vertical back padding from DE active edge
<v_sync_offset_a> = leave at zero
<v_sync_offset_b> = leave at zero
<pixel_rep>       = leave at zero
<frame_rate>      = screen refresh rate in Hz
<interlaced>      = leave at zero
<pixel_freq>      = clock frequency (h_active_pixels + h_front_porch + h_sync_pulse + h_back_porch)
                                    * (v_active_lines + v_front_porch + v_sync_pulse + v_back_porch)
                                    * framerate
<aspect_ratio>    = [see footnote]
```

The aspect ratio can be set to one of eight values. Choose a value representing the aspect ratio most similar to your screen from the following:

| Aspect ratio | Name                          | Value |
| -------------- | ------------------------------- | ------- |
| 4:3          | HDMI\_ASPECT\_4\_3   | 1     |
| 14:9         | HDMI\_ASPECT\_14\_9  | 2     |
| 16:9         | HDMI\_ASPECT\_16\_9  | 3     |
| 5:4          | HDMI\_ASPECT\_5\_4   | 4     |
| 16:10        | HDMI\_ASPECT\_16\_10 | 5     |
| 15:9         | HDMI\_ASPECT\_15\_9  | 6     |
| 21:9         | HDMI\_ASPECT\_21\_9  | 7     |
| 64:27        | HDMI\_ASPECT\_64\_27 | 8     |

### Generic display options

#### `hdmi_force_hotplug`

Setting `hdmi_force_hotplug` to `1` pretends that the HDMI hotplug signal is asserted, so it appears that a HDMI display is attached. In other words, HDMI output mode will be used, even if no HDMI monitor is detected.

#### `hdmi_ignore_hotplug`

Setting `hdmi_ignore_hotplug` to `1` pretends that the HDMI hotplug signal is not asserted, so it appears that a HDMI display is not attached. HDMI output will therefore be disabled, even if a monitor is connected.

#### `disable_overscan`

The default value for `disable_overscan` is `0` which gives default values of overscan for the left, right, top, and bottom edges of `48` for HD CEA modes, `32` for SD CEA modes, and `0` for DMT modes.

Set `disable_overscan` to `1` to disable the default values of [overscan](https://www.raspberrypi.com/documentation/computers/configuration.html#underscan) that are set by the firmware.

#### `overscan_left`

The `overscan_left` command specifies the number of pixels to add to the firmware default value of overscan on the left edge of the screen. The default value is `0`.

Increase this value if the text flows off the left edge of the screen; decrease it if there is a black border between the left edge of the screen and the text.

#### `overscan_right`

The `overscan_right` command specifies the number of pixels to add to the firmware default value of overscan on the right edge of the screen. The default value is `0`.

Increase this value if the text flows off the right edge of the screen; decrease it if there is a black border between the right edge of the screen and the text.

#### `overscan_top`

The `overscan_top` command specifies the number of pixels to add to the firmware default value of overscan on the top edge of the screen. The default value is `0`.

Increase this value if the text flows off the top edge of the screen; decrease it if there is a black border between the top edge of the screen and the text.

#### `overscan_bottom`

The `overscan_bottom` command specifies the number of pixels to add to the firmware default value of overscan on the bottom edge of the screen. The default value is `0`.

Increase this value if the text flows off the bottom edge of the screen; decrease it if there is a black border between the bottom edge of the screen and the text.

#### `overscan_scale`

Set `overscan_scale` to `1` to force any non-framebuffer layers to conform to the overscan settings. The default value is `0`.

**NOTE:**  this feature is generally not recommended: it can reduce image quality because all layers on the display will be scaled by the GPU. Disabling overscan on the display itself is the recommended option to avoid images being scaled twice (by the GPU and the display).

#### `framebuffer_width`

The `framebuffer_width` command specifies the console framebuffer width in pixels. The default is the display width minus the total horizontal overscan.

#### `framebuffer_height`

The `framebuffer_height` command specifies the console framebuffer height in pixels. The default is the display height minus the total vertical overscan.

#### `max_framebuffer_height`, `max_framebuffer_width`

Specifies the maximum dimensions of the internal frame buffer.

#### `framebuffer_depth`

Use `framebuffer_depth` to specify the console framebuffer depth in bits per pixel. The default value is `16`.

| framebuffer\_depth | result             | notes                                       |
| ----------------------- | -------------------- | --------------------------------------------- |
| 8                     | 8-bit framebuffer  | Default RGB palette makes screen unreadable |
| 16                    | 16-bit framebuffer |                                             |
| 24                    | 24-bit framebuffer | May result in a corrupted display           |
| 32                    | 32-bit framebuffer | May need to be used in conjunction with `framebuffer_ignore_alpha=1`    |

#### `framebuffer_ignore_alpha`

Set `framebuffer_ignore_alpha` to `1` to disable the alpha channel. Can help with the display of a 32-bit `framebuffer_depth`.

#### `framebuffer_priority`

In a system with multiple displays, using the legacy (pre-KMS) graphics driver, this forces a specific internal display device to be the first Linux framebuffer (i.e. `/dev/fb0`).

The options that can be set are:

| Display       | ID |
| --------------- | ---- |
| Main LCD      | 0  |
| Secondary LCD | 1  |
| HDMI 0        | 2  |
| Composite     | 3  |
| HDMI 1        | 7  |

#### `max_framebuffers`

This configuration entry sets the maximum number of firmware framebuffers that can be created. Valid options are 0, 1, and 2. By default on devices before the Raspberry Pi 4 this is set to 1, so will need to be increased to 2 when using more than one display, for example HDMI and a DSI or DPI display. The Raspberry Pi 4 configuration sets this to 2 by default as it has two HDMI ports.

It is safe to set this to 2 in most instances, as framebuffers will only be created when an attached device is actually detected.

Setting this value to 0 can be used to reduce memory requirements when used in headless mode, as it will prevent any framebuffers from being allocated.

#### `test_mode`

The `test_mode` command displays a test image and sound during boot (over the composite video and analogue audio outputs only) for the given number of seconds, before continuing to boot the OS as normal. This is used as a manufacturing test; the default value is `0`.

#### `display_hdmi_rotate`

Use `display_hdmi_rotate` to rotate or flip the HDMI display orientation. The default value is `0`.

| display\_hdmi\_rotate | result                       |
| ----------------------------- | ------------------------------ |
| 0                           | no rotation                  |
| 1                           | rotate 90 degrees clockwise  |
| 2                           | rotate 180 degrees clockwise |
| 3                           | rotate 270 degrees clockwise |
| 0x10000                     | horizontal flip              |
| 0x20000                     | vertical flip                |

Note that the 90 and 270 degree rotation options require additional memory on the GPU, so these will not work with the 16MB GPU split.

You can combine the rotation settings with the flips by adding them together. You can also have both horizontal and vertical flips in the same way. E.g. A 180 degree rotation with a vertical and horizontal flip will be 0x20000 + 0x10000 + 2 = 0x30002.

#### `display_lcd_rotate`

For the legacy graphics driver (default on models prior to the Raspberry Pi 4), use `display_lcd_rotate` to rotate or flip the LCD orientation. Parameters are the same as `display_hdmi_rotate`. See also `lcd_rotate`.

#### `display_rotate`

In the latest firmware, `display_rotate` is deprecated. It has only been retained for backwards compatibility. Please use `display_lcd_rotate` and `display_hdmi_rotate` instead.

Use `display_rotate` to rotate or flip the screen orientation. Parameters are the same as `display_hdmi_rotate`.

### Other options

#### `dispmanx_offline`

Forces `dispmanx` composition to be done offline in two offscreen framebuffers. This can allow more `dispmanx` elements to be composited, but is slower and may limit screen framerate to around 30fps.

## Legacy Raspberry Pi 4 HDMI pipeline

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/computers/legacy_config_txt/pi4-hdmi.adoc)

| IMPORTANT | When using the VC4 KMS graphics driver, the complete display pipeline is managed by Linux - this includes the HDMI outputs. These settings only apply to the legacy FKMS and firmware-based graphics driver. |
| ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

Raspberry Pi 4 is unable to output over HDMI at 1366×768 @ 60Hz. On some monitors it is possible to configure them to use 1360×768 @ 60Hz. They do not typically advertise this mode via their EDID, so the selection can’t be made automatically, but it can be selected manually by adding:

```
hdmi_group=2
hdmi_mode=87
hdmi_cvt=1360 768 60
```

…to [config.txt](https://www.raspberrypi.com/documentation/computers/legacy_config_txt.html#legacy-video-options).

Timings specified manually via a `hdmi_timings=` line in `config.txt` will also need to comply with the restriction of all horizontal timing parameters being divisible by two.

`dpi_timings=` are not restricted in the same way, as that pipeline still only runs at a single pixel per clock cycle.

## Legacy Miscellaneous Options

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/computers/legacy_config_txt/misc.adoc)

### `avoid_warnings`

`avoid_warnings=2` allows turbo mode even when low-voltage is present.

### `logging_level`

Sets the VideoCore logging level. The value is a VideoCore-specific bitmask.
