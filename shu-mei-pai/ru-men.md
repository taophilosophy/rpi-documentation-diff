# Getting started

## Getting started with your Raspberry Pi

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/computers/getting-started/setting-up.adoc)

To get started with your Raspberry Pi, you’ll need the following:

* a [power supply](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#power-supply)
* boot media (e.g. a [microSD card with ample storage and speed](https://www.raspberrypi.com/documentation/computers/getting-started.html#recommended-sd-cards))

You can set up your Raspberry Pi as an interactive computer with a desktop, or as a *headless* computer accessible only over the network. To set your Raspberry Pi up headless, you don’t need any additional peripherals: you can preconfigure a hostname, user account, network connection, and SSH when you [install an operating system](https://www.raspberrypi.com/documentation/computers/getting-started.html#installing-the-operating-system). If you want to use your Raspberry Pi directly, you’ll need the following additional accessories:

* a display
* a cable to connect your Raspberry Pi to your display
* a keyboard
* a mouse

### Power supply

The following table shows the USB-PD power mode required to power various Raspberry Pi models. You can use any high-quality power supply that provides the correct power mode.

| Model                          | Recommended power supply (voltage/current) | Raspberry Pi power supply |
| -------------------------------- | -------------------------------------------- | --------------------------- |
| Raspberry Pi 5                 | 5V/5A, 5V/3A limits peripherals to 600mA   | [27W USB-C power supply](https://www.raspberrypi.com/products/27w-power-supply/)                          |
| Raspberry Pi 4 Model B         | 5V/3A                                      | [15W USB-C power supply](https://www.raspberrypi.com/products/type-c-power-supply/)                          |
| Raspberry Pi 3 (all models)    | 5V/2.5A                                    | [12.5W Micro USB power supply](https://www.raspberrypi.com/products/micro-usb-power-supply/)                          |
| Raspberry Pi 2 (all models)    | 5V/2.5A                                    | [12.5W Micro USB power supply](https://www.raspberrypi.com/products/micro-usb-power-supply/)                          |
| Raspberry Pi 1 (all models)    | 5V/2.5A                                    | [12.5W Micro USB power supply](https://www.raspberrypi.com/products/micro-usb-power-supply/)                          |
| Raspberry Pi Zero (all models) | 5V/2.5A                                    | [12.5W Micro USB power supply](https://www.raspberrypi.com/products/micro-usb-power-supply/)                          |

![Plugging a power supply into a Raspberry Pi.](https://www.raspberrypi.com/documentation/computers/images/peripherals/cable-power.png?hash=b5cb190b02c5c2555af60a48dba0a1f9)

Plug your power supply into the port marked "POWER IN", "PWR IN", or "PWR". Some Raspberry Pi models, such as the Zero series, have output USB ports with the same form factor as the power port. Be sure to use the correct port on your Raspberry Pi!

### Boot Media

Raspberry Pi models lack onboard storage, so you have to supply it. You can boot your Raspberry Pi from an operating system image installed on any supported media: microSD cards are used commonly, but USB storage, network storage, and storage connected via a PCIe HAT are also available. However, only recent Raspberry Pi models support all of these media types.

All Raspberry Pi consumer models since the Raspberry Pi 1 Model A+ feature a microSD slot. Your Raspberry Pi automatically boots from the microSD slot when the slot contains a card.

![Inserting a microSD card into a Raspberry Pi.](https://www.raspberrypi.com/documentation/computers/images/peripherals/sd-card.png?hash=d0b4ea20b41681cee6ce87eb5df2b279)

#### Recommended SD cards

We recommend using an SD card with at least 32GB of storage for Raspberry Pi OS installations. For Raspberry Pi OS Lite, we recommend at least 16GB. You can use any SD card with a capacity of less than 2TB. Capacities above 2TB are currently not supported due to limitations in the [MBR](https://en.wikipedia.org/wiki/Master_boot_record). As with any other boot media, you’ll see improved performance on SD cards with faster read and write speeds.

Because of a hardware limitation, the following devices will only boot from a boot partition of 256GB or less:

* Raspberry Pi Zero
* Raspberry Pi 1
* early Raspberry Pi 2 models with the BCM2836 SoC

Other operating systems have different requirements. Check the documentation for your operating system for capacity requirements.

### Keyboard

You can use any of the USB ports on your Raspberry Pi to connect a [wired keyboard](https://www.raspberrypi.com/products/raspberry-pi-keyboard-and-hub/) or USB Bluetooth receiver.

![Plugging a keyboard into a Raspberry Pi.](https://www.raspberrypi.com/documentation/computers/images/peripherals/cable-key.png)

### Mouse

You can use any of the USB ports on your Raspberry Pi to connect a [wired mouse](https://www.raspberrypi.com/products/raspberry-pi-mouse/) or USB Bluetooth receiver.

![Plugging a mouse into a Raspberry Pi.](https://www.raspberrypi.com/documentation/computers/images/peripherals/cable-mouse.png)

### Display

Raspberry Pi models have the following display connectivity:

| Model                          | Display outputs                                         |
| -------------------------------- | --------------------------------------------------------- |
| Raspberry Pi 5                 | 2× micro HDMI                                          |
| Raspberry Pi 4 (all models)    | 2× micro HDMI, audio and composite out via 3.5mm [TRRS](http://en.wikipedia.org/wiki/Phone_connector_(audio)#TRRS_standards) jack |
| Raspberry Pi 3 (all models)    | HDMI, audio and composite out via 3.5mm [TRRS](http://en.wikipedia.org/wiki/Phone_connector_(audio)#TRRS_standards) jack           |
| Raspberry Pi 2 (all models)    | HDMI, audio and composite out via 3.5mm [TRRS](http://en.wikipedia.org/wiki/Phone_connector_(audio)#TRRS_standards) jack           |
| Raspberry Pi 1 Model B+        | HDMI, audio and composite out via 3.5mm [TRRS](http://en.wikipedia.org/wiki/Phone_connector_(audio)#TRRS_standards) jack           |
| Raspberry Pi 1 Model A+        | HDMI, audio and composite out via 3.5mm [TRRS](http://en.wikipedia.org/wiki/Phone_connector_(audio)#TRRS_standards) jack           |
| Raspberry Pi Zero (all models) | mini HDMI                                               |

| NOTE | No Raspberry Pi models support video over USB-C (DisplayPort alt mode). |
| ------ | ------------------------------------------------------------------------- |

If your Raspberry Pi has more than one HDMI port, plug your primary monitor into the port marked `HDMI0`.

Most displays don’t have micro or mini HDMI ports. However, you can use a [micro-HDMI-to-HDMI cable](https://www.raspberrypi.com/products/micro-hdmi-to-standard-hdmi-a-cable/) or [mini-HDMI-to-HDMI cable](https://www.raspberrypi.com/products/standard-hdmi-a-male-to-mini-hdmi-c-male-cable/) to connect those ports on your Raspberry Pi to any HDMI display. For displays that don’t support HDMI, consider an adapter that translates display output from HDMI to a port supported by your display.

![Plugging a micro HDMI cable into a Raspberry Pi.](https://www.raspberrypi.com/documentation/computers/images/peripherals/cable-hdmi.png?hash=f483bed69e8caae75cc6f79552e41e64)

### Audio

All Raspberry Pi models with HDMI, micro HDMI, or mini HDMI support audio output over HDMI. All Raspberry Pi models support audio over USB. All Raspberry Pi models equipped with Bluetooth support Bluetooth audio. All variants of the Raspberry Pi 1, 2, 3, and 4 include a 3.5mm auxiliary [TRRS](http://en.wikipedia.org/wiki/Phone_connector_(audio)#TRRS_standards) jack, which may require amplification for sufficient output volume.

### Networking

The following Raspberry Pi models come with Wi-Fi and Bluetooth connectivity:

* Raspberry Pi 5
* Raspberry Pi 4
* Raspberry Pi 3B+
* Raspberry Pi 3
* Raspberry Pi Zero W
* Rsapberry Pi Zero 2 W

The "Model B" suffix indicates variants with an Ethernet port; "Model A" indicates no Ethernet port. If your Raspberry Pi doesn’t have an Ethernet port, you can still connect to a wired internet connection using a USB-to-Ethernet adapter.

![Plugging an Ethernet cable into a Raspberry Pi.](https://www.raspberrypi.com/documentation/computers/images/peripherals/cable-net.png?hash=f9cb414421165e03c1c1f6acd524630f)

## Install an operating system

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/computers/getting-started/install.adoc)

To use your Raspberry Pi, you’ll need an operating system. By default, Raspberry Pis check for an operating system on any SD card inserted in the SD card slot.

Depending on your Raspberry Pi model, you can also boot an operating system from other storage devices, including USB drives, storage connected via a HAT, and network storage.

To install an operating system on a storage device for your Raspberry Pi, you’ll need:

* a computer you can use to image the storage device into a boot device
* a way to plug your storage device into that computer

Most Raspberry Pi users choose microSD cards as their boot device.

We recommend installing an operating system using [Raspberry Pi Imager](https://www.raspberrypi.com/documentation/computers/getting-started.html#raspberry-pi-imager).

Raspberry Pi Imager is a tool that helps you download and write images on macOS, Windows, and Linux. Imager includes many popular operating system images for Raspberry Pi. Imager also supports loading images downloaded directly from [Raspberry Pi](https://www.raspberrypi.com/software/operating-systems/) or third-party vendors such as [Ubuntu](https://ubuntu.com/download/raspberry-pi). You can use Imager to preconfigure credentials and remote access settings for your Raspberry Pi.

Imager supports images packaged in the `.img` format as well as container formats like `.zip`.

If you have no other computer to write an image to a boot device, you may be able to install an operating system [directly on your Raspberry Pi from the internet](https://www.raspberrypi.com/documentation/computers/getting-started.html#install-over-the-network).

### Install using Imager

You can install Imager in the following ways:

* Download the latest version from [raspberrypi.com/software](https://www.raspberrypi.com/software/) and run the installer.
* Install it from a terminal using your package manager, e.g. `sudo apt install rpi-imager`.

Once you’ve installed Imager, launch the application by clicking the Raspberry Pi Imager icon or running `rpi-imager`.

![Raspberry Pi Imager main window.](https://www.raspberrypi.com/documentation/computers/images/imager/welcome.png?hash=a351c2ba01f30809c2921de09be67683)

Click **Choose device** and select your Raspberry Pi model from the list.

![Raspberry Pi model selections in Imager.](https://www.raspberrypi.com/documentation/computers/images/imager/choose-model.png?hash=0543c40612882f917cfc565caa6dc92f)

Next, click **Choose OS** and select an operating system to install. Imager always shows the recommended version of Raspberry Pi OS for your model at the top of the list.

![Operating system selections in Imager.](https://www.raspberrypi.com/documentation/computers/images/imager/choose-os.png?hash=9d49bdaf867704b30f177d47e72dc9b8)

Connect your preferred storage device to your computer. For example, plug a microSD card in using an external or built-in SD card reader. Then, click **Choose storage** and select your storage device.

| WARNING | If you have more than one storage device connected to your computer, *be sure to choose the correct device!*  You can often identify storage devices by size. If you’re unsure, disconnect other devices until you’ve identified the device you want to image. |
| --------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

![Storage selection options in Imager.](https://www.raspberrypi.com/documentation/computers/images/imager/choose-storage.png?hash=05e6671a4cac0b1f3781448688f5d692)

Next, click **Next**.

![Imager prompt to open OS customisation menu.](https://www.raspberrypi.com/documentation/computers/images/imager/os-customisation-prompt.png?hash=4df5658cd09684490db4c1f2352255a3)

In a popup, Imager will ask you to apply OS customisation. We strongly recommend configuring your Raspberry Pi via the OS customisation settings. Click the **Edit Settings** button to open [OS customisation](https://www.raspberrypi.com/documentation/computers/getting-started.html#advanced-options).

If you don’t configure your Raspberry Pi via OS customisation settings, Raspberry Pi OS will ask you for the same information at first boot during the [configuration wizard](https://www.raspberrypi.com/documentation/computers/getting-started.html#configuration-on-first-boot). You can click the **No** button to skip OS customisation.

#### OS customisation

The OS customisation menu lets you set up your Raspberry Pi before first boot. You can preconfigure:

* a username and password
* Wi-Fi credentials
* the device hostname
* the time zone
* your keyboard layout
* remote connectivity

When you first open the OS customisation menu, you might see a prompt asking for permission to load Wi-Fi credentials from your host computer. If you respond "yes", Imager will prefill Wi-Fi credentials from the network you’re currently connected to. If you respond "no", you can enter Wi-Fi credentials manually.

The **hostname** option defines the hostname your Raspberry Pi broadcasts to the network using [mDNS](https://en.wikipedia.org/wiki/Multicast_DNS). When you connect your Raspberry Pi to your network, other devices on the network can communicate with your computer using `<hostname>.local` or `<hostname>.lan`.

The **username and password** option defines the username and password of the admin user account on your Raspberry Pi.

The **wireless LAN** option allows you to enter an SSID (name) and password for your wireless network. If your network does not broadcast an SSID publicly, you should enable the "Hidden SSID" setting. By default, Imager uses the country you’re currently in as the "Wireless LAN country". This setting controls the Wi-Fi broadcast frequencies used by your Raspberry Pi. Enter credentials for the wireless LAN option if you plan to run a headless Raspberry Pi.

The **locale settings** option allows you to define the time zone and default keyboard layout for your Pi.

![General settings in the OS customisation menu.](https://www.raspberrypi.com/documentation/computers/images/imager/os-customisation-general.png?hash=6509321c9eebb02e53dd711c12395571)

The **Services** tab includes settings to help you connect to your Raspberry Pi remotely.

If you plan to use your Raspberry Pi remotely over your network, check the box next to **Enable SSH**. You should enable this option if you plan to run a headless Raspberry Pi.

* Choose the **password authentication** option to SSH into your Raspberry Pi over the network using the username and password you provided in the general tab of OS customisation.
* Choose **Allow public-key authentication only** to preconfigure your Raspberry Pi for passwordless public-key SSH authentication using a private key from the computer you’re currently using. If already have an RSA key in your SSH configuration, Imager uses that public key. If you don’t, you can click **Run SSH-keygen** to generate a public/private key pair. Imager will use the newly-generated public key.

![Services settings in the OS customisation menu.](https://www.raspberrypi.com/documentation/computers/images/imager/os-customisation-services.png?hash=bbc8c0ff2f1eb7207d43180d7694c399)

OS customisation also includes an **Options** menu that allows you to configure the behaviour of Imager during a write. These options allow you to play a noise when Imager finishes verifying an image, to automatically unmount storage media after verification, and to disable telemetry.

![Options in the OS customisation menu.](https://www.raspberrypi.com/documentation/computers/images/imager/os-customisation-options.png?hash=eda44365c03e4184f09832f46516a41b)

#### Write

When you’ve finished entering OS customisation settings, click **Save** to save your customisation.

Then, click **Yes** to apply OS customisation settings when you write the image to the storage device.

Finally, respond **Yes** to the "Are you sure you want to continue?" popup to begin writing data to the storage device.

![Confirming a reimage of a storage device in Imager.](https://www.raspberrypi.com/documentation/computers/images/imager/are-you-sure.png?hash=5dce4cfcd6622b97ce741b2c168f0a3d)

If you see an admin prompt asking for permissions to read and write to your storage medium, grant Imager the permissions to proceed.

![Writing an image to a device in Imager.](https://www.raspberrypi.com/documentation/computers/images/imager/writing.png?hash=15fc8293a1c6b12fad0436e4d4aaf506)

Grab a cup of coffee or go for a walk. This could take a few minutes.

![Verifying an image on a device in Imager.](https://www.raspberrypi.com/documentation/computers/images/imager/stop-ask-verify.png?hash=78a0e9f7a1df18d5df3ebe92b073ed97)

If you want to live especially dangerously, you can click **cancel verify** to skip the verification process.

When you see the "Write Successful" popup, your image has been completely written and verified. You’re now ready to boot a Raspberry Pi from the storage device!

![The screen Imager shows when it finishes writing an image to a storage device.](https://www.raspberrypi.com/documentation/computers/images/imager/finished.png?hash=ba5031e958427e07a6c3a727d3b30021)

Next, proceed to the [first boot configuration instructions](https://www.raspberrypi.com/documentation/computers/getting-started.html#configuration-on-first-boot) to get your Raspberry Pi up and running.

### Install over the network

Network Install enables a Raspberry Pi to install an operating system on a storage device using a version of Raspberry Pi Imager downloaded over the network. With Network Install, you can get an operating system installed on your Raspberry Pi with no separate SD card reader and no computer other than your Raspberry Pi. You can run Network Install on any compatible storage device, including SD cards and USB storage.

Network Install only runs on Raspberry Pi 4, 400, and 5. If your Raspberry Pi runs an older bootloader, you may need to [update the bootloader](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#bootloader_update_stable) to use Network Install.

Network Install requires the following:

* a compatible Raspberry Pi model running firmware that supports Network Install
* a monitor
* a keyboard
* a wired internet connection

To launch Network Install, power on your Raspberry Pi *while pressing and holding the* ***SHIFT*** *key* in the following configuration:

* no bootable storage device
* attached keyboard
* attached compatible storage device, such as an SD card or USB storage

![The Network Install screen.](https://www.raspberrypi.com/documentation/computers/images/network-install-1.png?hash=860b27343ffe3b99bbdf90242787bf93)

If you haven’t already connected your Raspberry Pi to the internet, connect it with an Ethernet cable.

![Starting Network Install.](https://www.raspberrypi.com/documentation/computers/images/network-install-2.png?hash=7a66f6f7b4f2421c488c3f3a25742fad)

Once you’re connected to the internet, your Raspberry Pi will download Raspberry Pi installer. If the download fails, you can repeat the process to try again.

![Downloading Imager using Network Install.](https://www.raspberrypi.com/documentation/computers/images/network-install-3.png?hash=3af0667640d3789e700378b9c33dfa8d)

Once you finish downloading Raspberry Pi Installer, your Raspberry Pi will automatically start Raspberry Pi Imager. For more information about running Raspberry Pi Imager, see [install an operating system](https://www.raspberrypi.com/documentation/computers/getting-started.html#installing-the-operating-system).

![Choose a storage device.](https://www.raspberrypi.com/documentation/computers/images/network-install-4.png?hash=c5270de569440bc4c0f0cc11c0fdb3e7)

For more information about Network Install configuration, see [HTTP boot](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#http-boot).

## Set up your Raspberry Pi

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/computers/getting-started/configuring.adoc)

After installing an operating system image, connect your storage device to your Raspberry Pi.

First, unplug your Raspberry Pi’s power supply to ensure that the Raspberry Pi is powered down while you connect peripherals. If you installed the operating system on a microSD card, you can plug it into your Raspberry Pi’s card slot now. If you installed the operating system on any other storage device, you can connect it to your Raspberry Pi now.

![Inserting a microSD card into a Raspberry Pi.](https://www.raspberrypi.com/documentation/computers/images/peripherals/sd-card.png?hash=d0b4ea20b41681cee6ce87eb5df2b279)

Then, plug in any other peripherals, such as your mouse, keyboard, and monitor.

![Attaching the power supply to a Raspberry Pi.](https://www.raspberrypi.com/documentation/computers/images/peripherals/cable-all.png?hash=99131f604cad98dc8eddc7daa0b7d20e)

Finally, connect the power supply to your Raspberry Pi. You should see the status LED light up when your Pi powers on. If your Pi is connected to a display, you should see the boot screen within minutes.

## Configuration on first boot

If you used OS customisation in Imager to preconfigure your Raspberry Pi, **congratulations!**  Your device is ready to use. Proceed to [next steps](https://www.raspberrypi.com/documentation/computers/getting-started.html#next-steps) to learn how you can put your Raspberry Pi to good use.

If your Raspberry Pi does not boot within 5 minutes, check the status LED. If it’s flashing, see the [LED warning flash codes for more information](https://www.raspberrypi.com/documentation/computers/configuration.html#led-warning-flash-codes). If your Pi refuses to boot, try the following mitigation steps:

* if you used a boot device other than an SD card, try booting from an SD card
* [re-image your SD card](https://www.raspberrypi.com/documentation/computers/getting-started.html#installing-the-operating-system); be sure to complete the entire verify step in Imager
* [update the bootloader](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#bootloader_update_stable) on your Raspberry Pi, then [re-image your SD card](https://www.raspberrypi.com/documentation/computers/getting-started.html#installing-the-operating-system)

If you chose to skip OS customisation in Imager, your Raspberry Pi will run a configuration wizard on first boot. You need a monitor and keyboard to navigate through the wizard; a mouse is optional.

![Click Next to get started with configuration.](https://www.raspberrypi.com/documentation/computers/images/initial-setup/start.png?hash=b09c881a5736586851e18c5f05848de9)

### Bluetooth

If you’re using a Bluetooth keyboard or mouse, this step will walk you through device pairing. Your Raspberry Pi will scan for pairable devices and connect to the first device it finds for each item.

This process works with built-in or external USB Bluetooth adapters. If you use a USB adapter, plug it in before booting your Raspberry Pi.

### Locale

This page helps you configure your country, language, and time zone, and keyboard layout.

![Adjust country, language, time zone, and keyboard layout.](https://www.raspberrypi.com/documentation/computers/images/initial-setup/locale.png?hash=fbd68b45d7d7dbdb8d4b8a007b884dcd)

### User

This page helps you configure the username and password for the default user account.

By default, older versions of Raspberry Pi OS set the username to "pi". If you use the username "pi", avoid the old default password of "raspberry" to keep your Raspberry Pi secure.

![Create your username and password.](https://www.raspberrypi.com/documentation/computers/images/initial-setup/user.png?hash=a599f2e570ef4504b7686165b75ff87d)

### Wi-Fi

This page helps you connect to a Wi-Fi network. Choose your preferred network from the list.

![Selecting a wireless network.](https://www.raspberrypi.com/documentation/computers/images/initial-setup/network.png?hash=0689b7309b820bbe9d6481ede702ae90)

If your network requires a password, you can enter it here.

![Entering a password for a wireless network.](https://www.raspberrypi.com/documentation/computers/images/initial-setup/network_password.png?hash=0e8c3340265258d58892ada216415fbb)

### Browser

This page lets you select Firefox or Chromium as your default internet browser. You can optionally uninstall the browser you don’t set as default.

![The Choose Browser page.](https://www.raspberrypi.com/documentation/computers/images/initial-setup/browser.png?hash=81ebfe9b12c6bf8977067fd8570b5c3d)

### Software updates

Once your Raspberry Pi has internet access, this page helps you update your operating system and software to the latest versions. During the software update process, the wizard will remove the non-default browser if you opted to uninstall it in the browser selection step. Downloading updates may take several minutes.

![You can download the latest software updates during the wizard before you boot for the first time.](https://www.raspberrypi.com/documentation/computers/images/initial-setup/update.png?hash=246c11bd48b5c6f0e3332b39fc58e6a5)

![You can download the latest software updates during the wizard before you boot for the first time.](https://www.raspberrypi.com/documentation/computers/images/initial-setup/download.png?hash=1b90dc708944ceeeabe6ac5fb3c65df4)

When you see a popup indicating that your system is up to date, click **OK** to proceed to the next step.

### Finish

At the end of the configuration wizard, click **Restart** to reboot your Raspberry Pi. Your Raspberry Pi will apply your configuration and boot to the desktop.

![The Setup Complete dialogue prompts to restart your Raspberry Pi.](https://www.raspberrypi.com/documentation/computers/images/initial-setup/restart.png?hash=a4722ccce3851961d3c05d4ac8245452)

## Next steps

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/computers/getting-started/wrapping-up.adoc)

Now that your Raspberry Pi is set up and ready to go, what’s next?

### Recommended software

Raspberry Pi OS comes with many essential applications pre-installed so you can start using them straight away. If you’d like to take advantage of other applications we find useful, click the raspberry icon in the top left corner of the screen. Select **Preferences &gt;**  **Recommended Software** from the drop-down menu, and you’ll find the package manager. You can install a wide variety of recommended software here for free.

![Opening the package manager GUI in Raspberry Pi OS](https://www.raspberrypi.com/documentation/computers/images/recommended-software.png?hash=941c1b34b17afdc98bba97c62dc2da0a)

For example, if you plan to use your Raspberry Pi as a home computer, you might find LibreOffice useful for writing and editing documents and spreadsheets. You can also make your Raspberry Pi more accessible with apps like a screen magnifier and Orca screen reader, found under Universal Access.

### Tutorials

Our tutorials demonstrate various ways you can use your new computer. You can learn to code, control external devices, and build exciting new projects by following [tutorials](https://www.raspberrypi.com/tutorials/) that pique your interest.

### Support

For support with official Raspberry Pi products, or to connect with other Raspberry Pi users, visit the [Raspberry Pi forums](https://forums.raspberrypi.com/).

### Further reading

![](https://www.raspberrypi.com/documentation/computers/images/fifth-editon-cover.png)[https://store.rpipress.cc/products/the-official-raspberry-pi-beginners-guide-5th-edition](https://store.rpipress.cc/products/the-official-raspberry-pi-beginners-guide-5th-edition)

You can find more information on how get started with your Raspberry Pi in the latest edition of [Official Raspberry Pi Beginners Guide](https://store.rpipress.cc/collections/latest-releases/products/the-official-raspberry-pi-beginners-guide-5th-edition) by Gareth Halfacree.

Learn how to:

* Set up your Raspberry Pi, install its operating system, and start using this fully functional computer.
* Start coding projects, with step-by-step guides using the Scratch 3, Python, and MicroPython programming languages.
* Experiment with connecting electronic components, and have fun creating amazing projects.

New in the 5th edition:

* Updated for the latest Raspberry Pi computers: Raspberry Pi 5 and Raspberry Pi Zero 2 W.
* Covers the latest Raspberry Pi OS.
* Includes a new chapter on the Raspberry Pi Pico!

You can [buy this book](https://store.rpipress.cc/products/the-official-raspberry-pi-beginners-guide-5th-edition) on the Raspberry Pi Press site.
