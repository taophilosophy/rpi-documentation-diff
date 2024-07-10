# Processors

## BCM2835

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/computers/processors/bcm2835.adoc)

The BCM2835 is the Broadcom chip used in the Raspberry Pi 1 Models A, A+, B, B+, the Raspberry Pi Zero, the Raspberry Pi Zero W, and the Raspberry Pi Compute Module 1. Some details of the chip can be found in the [peripheral specification](https://datasheets.raspberrypi.com/bcm2835/bcm2835-peripherals.pdf) document. It contains a single-core ARM1176JZF-S processor.

| NOTE | The peripheral specification document contains a number of errors. However there is a list of currently known [errata](https://elinux.org/BCM2835_datasheet_errata). |
| ------ | ----------------------------------------------------------------------------------------------------------------- |

Other information regarding the processor can be found in the following documents;

* [GPU documentation](https://docs.broadcom.com/docs/12358545) and [open-source driver](https://docs.broadcom.com/docs/12358546)
* [ARM1176JZF-S](https://developer.arm.com/documentation/ddi0301)

## BCM2836

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/computers/processors/bcm2836.adoc)

The Broadcom chip used in the Raspberry Pi 2 Model B. The underlying architecture in BCM2836 is identical to BCM2835. The only significant difference is the removal of the ARM1176JZF-S processor and replacement with a quad-core Cortex-A7 cluster.

You should refer to:

* [BCM2836 ARM-local peripherals](https://datasheets.raspberrypi.com/bcm2836/bcm2836-peripherals.pdf)
* [Cortex-A7 MPcore Processor Reference Manual](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.ddi0464f/index.html)

## BCM2837

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/computers/processors/bcm2837.adoc)

This is the Broadcom chip used in the Raspberry Pi 3 Model B, later models of the Raspberry Pi 2 Model B, and the Raspberry Pi Compute Module 3. The underlying architecture of the BCM2837 is identical to the BCM2836. The only significant difference is the replacement of the ARMv7 quad core cluster with a quad-core ARM Cortex A53 (ARMv8) cluster.

The ARM cores run at 1.2GHz, making the device about 50% faster than the Raspberry Pi 2. The VideoCore IV runs at 400MHz.

Please refer to the following BCM2836 document for details on the ARM peripherals specification, which also applies to the BCM2837.

* [BCM2836 ARM-local peripherals](https://datasheets.raspberrypi.com/bcm2836/bcm2836-peripherals.pdf)
* [Cortex-A53 MPCore Processor Technical Reference Manual](https://developer.arm.com/documentation/ddi0500/latest/)

## BCM2837B0

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/computers/processors/bcm2837b0.adoc)

This is the Broadcom chip used in the Raspberry Pi 3 Models A+, B+, and the Raspberry Pi Compute Module 3+. The underlying architecture of the BCM2837B0 is identical to the BCM2837 chip used in other versions of the Raspberry Pi. The ARM core hardware is the same, only the frequency is rated higher.

The ARM cores are capable of running at up to 1.4GHz, making the 3B+/3A+ about 17% faster than the original Raspberry Pi 3. The VideoCore IV runs at 400MHz. The ARM core is 64-bit, while the VideoCore IV is 32-bit.

The BCM2837B0 chip is packaged slightly differently to the BCM2837, and most notably includes a heat spreader for better thermals. This allows higher clock frequencies, and more accurate monitoring and control of the chip’s temperature.

This [post on the Raspberry Pi blog](https://www.raspberrypi.com/news/raspberry-pi-3-model-bplus-sale-now-35/) goes into further detail about the BCM2837B0 chip.

## BCM2711

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/computers/processors/bcm2711.adoc)

This is the Broadcom chip used in the Raspberry Pi 4 Model B, the Raspberry Pi 400, and the Raspberry Pi Compute Module 4. The architecture of the BCM2711 is a considerable upgrade on that used by the SoCs in earlier Raspberry Pi models. It continues the quad-core CPU design of the BCM2837, but uses the more powerful ARM A72 core. It has a greatly improved GPU feature set with much faster input/output, due to the incorporation of a PCIe link that connects the USB 2 and USB 3 ports, and a natively attached Ethernet controller. It is also capable of addressing more memory than the SoCs used before.

The ARM cores are capable of running at up to 1.5 GHz, making the Raspberry Pi 4 about 50% faster than the Raspberry Pi 3B+. The new VideoCore VI 3D unit now runs at up to 500 MHz. The ARM cores are 64-bit, and while the VideoCore is 32-bit, there is a new Memory Management Unit, which means it can access more memory than previous versions.

The BCM2711 chip continues to use the heat spreading technology started with the BCM2837B0, which provides better thermal management.

**Processor:**  Quad-core [Cortex-A72](https://en.wikipedia.org/wiki/ARM_Cortex-A72) (ARM v8) 64-bit SoC @ 1.5 GHz.

**Memory:**  Accesses up to 8GB LPDDR4-2400 SDRAM (depending on model)

**Caches:**  32kB data + 48kB instruction L1 cache per core. 1MB L2 cache.

**Multimedia:**  H.265 (4Kp60 decode); H.264 (1080p60 decode, 1080p30 encode); OpenGL ES, 3.0 graphics

**I/O:**  PCIe bus, onboard Ethernet port, 2 × DSI ports (only one exposed on Raspberry Pi 4B), 2 × CSI ports (only one exposed on Raspberry Pi 4B), up to 6 × I2C, up to 6 × UART (muxed with I2C), up to 6 × SPI (only five exposed on Raspberry Pi 4B), dual HDMI video output, composite video output.

The [datasheet for the BCM2711](https://datasheets.raspberrypi.com/bcm2711/bcm2711-peripherals.pdf) contains further details.

## BCM2712

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/computers/processors/bcm2712.adoc)

Broadcom BCM2712 is the 16nm application processor at the heart of Raspberry Pi 5. It is the successor to the BCM2711 device used in Raspberry Pi 4, and shares many common architectural features with other devices in the BCM27xx family, used on earlier Raspberry Pi products.

Built around a quad-core Arm Cortex-A76 CPU cluster, clocked at up to 2.4GHz, with 512KB per-core L2 caches and a 2MB shared L3 cache, it integrates an improved 12-core VideoCore VII GPU; a hardware video scaler and HDMI controller capable of driving dual 4Kp60 displays; and a Raspberry Pi-developed HEVC decoder and Image Signal Processor. A 32-bit LPDDR4X memory interface provides up to 17GB/s of memory bandwidth, while x1 and x4 PCI Express interfaces support high-bandwidth external peripherals; on Raspberry Pi 5 the latter is used to connect to the Raspberry Pi RP1 south bridge, which provides the bulk of the external-facing I/O functionality on the platform.

Headline features include:

* Quad-core Arm Cortex-A76 @ 2.4GHz

  * ARMv8-A ISA
  * 64KByte I and D caches
  * 512KB L2 per core, 2MB shared L3
* New Raspberry Pi-developed ISP

  * 1 gigapixel/sec
* Improved HVS and display pipeline

  * Dual 4Kp60 support
* VideoCore V3D VII

  * ~2-2.5× faster (more hardware, 1GHz versus 600MHz on Pi 4)
  * OpenGL ES 3.1, Vulkan 1.3
* 4Kp60 HEVC hardware decode

  * Other CODECs run in software
  * H264 1080p24 decode ~10–20% of CPU
  * H264 1080p60 decode ~50–60% of CPU
  * H264 1080p30 encode (from ISP) ~30–40% CPU

In aggregate, the new features present in BCM2712 deliver a performance uplift of 2-3x over Raspberry Pi 4 for common CPU or I/O-intensive use cases.

## RP3A0

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/computers/processors/rp3a0.adoc)

The Raspberry Pi RP3A0 is our first System-in-Package (SiP) consisting of a Broadcom BCM2710A1 — which is the silicon die packaged inside the Broadcom [BCM2837](https://www.raspberrypi.com/documentation/computers/processors.html#bcm2837) chip which is used on the [Raspberry Pi 3](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#raspberry-pi-3-model-b-2) — along with 512MB of DRAM.

It is used by the [Raspberry Pi Zero 2 W](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#raspberry-pi-zero-2-w).

![RP3A0 crosssection](https://www.raspberrypi.com/documentation/computers/images/RP3A0-crosssection.png)

The RP3A0 is a Quad-core 64-bit Arm Cortex A53 CPU clocked at 1 GHz, although with a heat sink or other cooling solution in place, the chip can be potentially overclocked to 1.2 GHz.

Please refer to the following BCM2836 document for details on the ARM peripherals specification, which also applies to the BCM2837 and RP3A0.

* [BCM2836 ARM-local peripherals](https://datasheets.raspberrypi.com/bcm2836/bcm2836-peripherals.pdf)
* [Cortex-A53 MPCore Processor Technical Reference Manual](https://developer.arm.com/documentation/ddi0500/latest/)

| NOTE | The original [Raspberry Pi Zero](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#raspberry-pi-zero) uses Package-on-Package (PoP) DRAM, where the DRAM is soldered directly on top of the [BCM2835](https://www.raspberrypi.com/documentation/computers/processors.html#bcm2835) chip. |
| ------ | ------------------------------------------------------------------------------------------------------------ |
