# Raspberry Pi Connect (Beta)

## Introduction

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/services/connect/introduction.adoc)

Raspberry Pi Connect provides secure access to your Raspberry Pi from anywhere in the world.

![hero](https://www.raspberrypi.com/documentation/services/images/hero.png?hash=abae19beca53f018d9c434ddee214cd9)

To use Connect, [install the Connect software](https://www.raspberrypi.com/documentation/services/connect.html#install-connect) on your Raspberry Pi. Then visit [connect.raspberrypi.com](https://connect.raspberrypi.com/) to access the desktop or a shell running on your Raspberry Pi in a browser window.

Connect uses a secure, encrypted connection. By default, Connect communicates directly between your Raspberry Pi and your browser. However, when Connect can’t establish a direct connection between your Raspberry Pi and your browser, we use a relay server. In such cases, Raspberry Pi only retains the metadata required to operate Connect.

Connect is currently in the Beta phase of development.

| NOTE | To use Connect, your Raspberry Pi must run [Raspberry Pi OS Bookworm](https://www.raspberrypi.com/news/bookworm-the-new-version-of-raspberry-pi-os/) or later. |
| ------ | ------------------------------------------------------- |

## Install

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/services/connect/install.adoc)

To begin installation, open a Terminal window. Run the following command to update your system and packages:

```
$ sudo apt update
$ sudo apt upgrade
```

Run the following command on your Raspberry Pi to install Connect:

```
$ sudo apt install rpi-connect
```

After installation, reboot your Raspberry Pi or [manually start the Connect service](https://www.raspberrypi.com/documentation/services/connect.html#manually-start-connect) to use Connect:

```
$ sudo reboot
```

Connect will automatically start the next time you log in to your Raspberry Pi.

### Connect Lite

We distribute an alternate **Lite** variant of Connect that only supports remote shell access, with no ability to screen share.

Run the following command on your Raspberry Pi to install Connect Lite:

```
$ sudo apt install rpi-connect-lite
```

Reboot your Raspberry Pi or [manually start the Connect service](https://www.raspberrypi.com/documentation/services/connect.html#manually-start-connect) to use Connect.

Consider [enabling user lingering](https://www.raspberrypi.com/documentation/services/connect.html#enable-remote-shell-at-all-times) to make your device accessible even when your user account isn’t logged in.

| TIP | Lite commands use the same `rpi-connect` name as the full version of Connect. `rpi-connect-lite` is just a package name. |
| ----- | ------------------------------------------------------------------------------------------- |

### Manually start Connect

| NOTE | By default, Connect automatically starts at login. You don’t need to manually start Connect after it starts for the first time unless you remove it from your login items. |
| ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

To start the service manually from the command line, run the following command:

```
$ systemctl --user start rpi-connect
```

## Link a Raspberry Pi with a Raspberry Pi ID

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/services/connect/use.adoc)

Now that you’ve installed Connect on your Raspberry Pi, you must associate your Raspberry Pi with your Raspberry Pi ID to use Connect.

If you do not have a Raspberry Pi ID, [create one](https://www.raspberrypi.com/documentation/services/id.html#create-a-raspberry-pi-id).

To link your Raspberry Pi with your Raspberry Pi ID, use Connect to generate a verification URL. Visit the URL and sign into your Raspberry Pi ID to add your Raspberry Pi to your account.

You can generate the verification URL using the Connect icon on the Raspberry Pi Desktop or with the `rpi-connect` CLI.

### via the Raspberry Pi Desktop

Once the `rpi-connect` service starts running, the Connect icon appears in the system tray.

![just installed](https://www.raspberrypi.com/documentation/services/images/just_installed.png?hash=692f34b6fd6ffda725743c0b13fe39d4)

Click on the Connect icon and choose "Sign in" from the drop-down menu.

![sign in](https://www.raspberrypi.com/documentation/services/images/sign-in.png?hash=503e210239051b7f27465e633e19b811)

This opens a verification URL you can use to link your Raspberry Pi to your Raspberry Pi ID.

### via the command line

Use the following command to generate a link that will connect your Raspberry Pi with your Raspberry Pi ID:

```
$ rpi-connect signin
```

This command should output something like the following:

```
Complete sign in by visiting https://connect.raspberrypi.com/verify/XXXX-XXXX
```

Visit the verification URL on any device and sign in to link your Raspberry Pi with your Raspberry Pi ID.

### Finish linking your Raspberry Pi

Visit the verification URL generated in the previous step.

Sign in to Connect using your [Raspberry Pi ID](https://www.raspberrypi.com/documentation/services/id.html).

![login with id](https://www.raspberrypi.com/documentation/services/images/login-with-id.png?hash=4767d1f31e88c81aa3a89b1a5dba11b9)

After authenticating, assign a name to your Raspberry Pi. Choose a name that will help you identify your device. Click the **Create device and sign in** button to continue.

![create device](https://www.raspberrypi.com/documentation/services/images/create-device.png?hash=23e46f4bc2cfdeb6de2d3c3bc2c2e790)

You can now remotely connect to your Raspberry Pi. The Connect system tray icon will turn blue to indicate that your Raspberry Pi has been linked to the Connect service. You should receive an email notification indicating that a new device has signed into Connect.

![sign in email](https://www.raspberrypi.com/documentation/services/images/sign-in-email.png?hash=ef25669d6e5d66866d3ab09b653e7561)

| WARNING | If you receive an email that says a device that you do not recognise has signed into Connect, change your Raspberry Pi ID password immediately. [Remove the device from Connect](https://www.raspberrypi.com/documentation/services/connect.html#manage-devices) to permanently disassociate it from your account. Consider [enabling two-factor authentication](https://www.raspberrypi.com/documentation/services/id.html#enable-two-factor-authentication) to keep your account secure. |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

Click the Connect system tray icon to open the Connect menu. This menu shows your current sign in status, an option to sign out, and options to enable or disable remote access methods.

| TIP | Connect signs communication with your device serial number. Moving your SD card between devices will sign you out of Connect. |
| ----- | ------------------------------------------------------------------------------------------------------------------------------- |

## Access your Raspberry Pi

Now that your Raspberry Pi appears on your Connect dashboard, you can access your Raspberry Pi from anywhere using only a browser. Connect provides multiple ways to interact with your Raspberry Pi remotely.

### Screen sharing

Connect includes the ability to share your Raspberry Pi’s screen in a browser. Use the following instructions to share your Raspberry Pi’s screen.

| NOTE | Screen sharing requires the **Wayland** window server. By default, Raspberry Pi OS only uses Wayland for **64-bit** distributions of Raspberry Pi OS **Bookworm** on Raspberry Pi 5, 4, or 400. Screen sharing is **not** compatible with Raspberry Pi OS Lite or systems that use the X window server. |
| ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

Visit [connect.raspberrypi.com](https://connect.raspberrypi.com/) on any computer.

Connect redirects you to the Raspberry Pi ID service to sign in. After signing in, Connect displays a list of linked devices. Devices available for screen sharing show a grey **Screen sharing** badge below the name of the device.

![list of devices](https://www.raspberrypi.com/documentation/services/images/list-of-devices.png?hash=e6b8b984af50f0a6a2bf598fd93196f7)

Click the **Connect via** button to the right of the device you would like to access. Select the **Screen sharing** option from the menu. This opens a browser window that displays the desktop of your Raspberry Pi.

![screen sharing connecting](https://www.raspberrypi.com/documentation/services/images/screen-sharing-connecting.png?hash=1635bce768aa5cee5af4471cd6797c06)

You can now use your Raspberry Pi as you would locally. For more information about the connection, hover your mouse over the padlock icon immediately to the right of the **Disconnect** button.

![screen sharing start](https://www.raspberrypi.com/documentation/services/images/screen-sharing-start.png?hash=76e29e56e835ec5c22b99f7ddd725200)

| TIP | Use the **Copy from remote** and **Paste to remote** buttons above your desktop to transfer text between your local and remote clipboards. |
| ----- | ----------------------------------------------------------------------------------------------------- |

Once connected, a green dot appears next to the **Screen sharing** badge in the Connect dashboard. This indicates an active screen sharing session. Hover to see the current number of screen sharing sessions.

![screen sharing active](https://www.raspberrypi.com/documentation/services/images/screen-sharing-active.png?hash=ebd9ed1debe009f1c908ab50456033c2)

The Connect icon in the system tray turns purple and displays a closed circle when a screen sharing session is in progress.

![screen sharing connected](https://www.raspberrypi.com/documentation/services/images/screen-sharing-connected.png?hash=f0ea6b9d4d3645d4e78698272ff90ad2)

#### Stop screen sharing

To close a screen sharing session, click the **Disconnect** button above your desktop.

![screen sharing end](https://www.raspberrypi.com/documentation/services/images/screen-sharing-end.png?hash=f6e18e205b5e1a6891035d426df22431)

#### Disable screen sharing

To turn off screen sharing, click the Connect system tray icon and unselect **Allow screen sharing**. Your Raspberry Pi remains signed into Connect, but you won’t be able to create a screen sharing session from the Connect dashboard.

![screen sharing disabled desktop](https://www.raspberrypi.com/documentation/services/images/screen-sharing-disabled-desktop.png?hash=fd904d7f45f9d31d199812b7fb0ceb23)

Alternatively, you can disable screen sharing with the following command:

```
$ rpi-connect vnc off
```

In the Connect dashboard, the **Screen sharing** badge and the **Screen sharing** option in the **Connect via** menu will appear crossed-out.

![screen sharing disabled](https://www.raspberrypi.com/documentation/services/images/screen-sharing-disabled.png?hash=3883a6ecf61f7a41299c9283a362bc3c)

To re-enable screen sharing, do one of the following:

* click the Connect system tray icon and select **Allow screen sharing**
* run the following command:

  ```
  $ rpi-connect vnc on
  ```

### Remote shell

Connect includes the ability to access a shell running on your Raspberry Pi from a browser. Use the following instructions to access the remote shell.

Visit [connect.raspberrypi.com](https://connect.raspberrypi.com/) on any computer.

Connect redirects you to the Raspberry Pi ID service to sign in. After signing in, Connect displays a list of linked devices. Devices available for remote shell access show a grey **Remote shell** badge below the name of the device.

![list of devices](https://www.raspberrypi.com/documentation/services/images/list-of-devices.png?hash=e6b8b984af50f0a6a2bf598fd93196f7)

Click the **Connect via** button to the right of the device you would like to access. Select the **Remote shell** option from the menu. This opens a shell session on your Raspberry Pi.

![remote shell connecting](https://www.raspberrypi.com/documentation/services/images/remote-shell-connecting.png?hash=847ea2f508da1c9ccf7dff55858110d3)

You can now use your Raspberry Pi as you would locally.

![remote shell start](https://www.raspberrypi.com/documentation/services/images/remote-shell-start.png?hash=f30aa1e036aceddbf93db8052b90a1ba)

| TIP | On some operating systems, the browser intercepts key combinations like **Ctrl+Shift+C** and **Ctrl+C**. Instead, you can use the right click menu or **Ctrl+Insert** to copy and **Shift+Insert** to paste. |
| ----- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |

Once connected, a green dot appears next to the **Remote shell** badge in the Connect dashboard. This indicates an active remote shell session. Hover to see the current number of remote shell sessions.

![remote shell active](https://www.raspberrypi.com/documentation/services/images/remote-shell-active.png?hash=6bc5011a8cdba03770454b404688372c)

| TIP | Every remote shell connection creates a brand new connection, just like SSH. To persist background commands and configuration across multiple sessions, use `screen` or `tmux`. |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

The Connect icon in the system tray turns purple and displays a closed circle when a remote shell session is in progress.

![remote shell connected](https://www.raspberrypi.com/documentation/services/images/remote-shell-connected.png?hash=50522c3af85883c3781a9938988dac82)

| TIP | The `CONNECT_TTY` environment variable indicates that a session uses a remote shell provided by Connect. |
| ----- | --------------------------------------------------------------------------------------------- |

#### End your remote shell session

To close a remote shell session, run the `exit` command or close the window.

![remote shell end](https://www.raspberrypi.com/documentation/services/images/remote-shell-end.png?hash=d59a5b649768c4e0481519eea1cd1591)

#### Disable remote shell access

To turn off remote shell access, click the Connect system tray icon and unselect **Allow remote shell**. Your Raspberry Pi remains signed into Connect, but you won’t be able to create a remote shell session from the Connect dashboard.

![remote shell disabled desktop](https://www.raspberrypi.com/documentation/services/images/remote-shell-disabled-desktop.png?hash=ea2ce53c56113b41b4234e392bc7dac8)

Alternatively, you can disable remote shell access with the following command:

```
$ rpi-connect shell off
```

In the Connect dashboard, the **Remote shell** badge and the **Remote shell** option in the **Connect via** menu will appear crossed-out.

![remote shell disabled](https://www.raspberrypi.com/documentation/services/images/remote-shell-disabled.png?hash=8f212b4f08d929bbd325ae45089eef6a)

To re-enable screen sharing, do one of the following:

* click the Connect system tray icon and select **Allow remote shell**
* run the following command:

  ```
  $ rpi-connect shell on
  ```

## Enable remote shell at all times

Connect runs as a user-level service, not as root. As a result, Connect only works when your user account is currently logged in on your Raspberry Pi. This can make your Raspberry Pi unreachable if you reboot with automatic login disabled. To continue running Connect even when you aren’t logged into your device, enable **user-lingering**. Run the following command from your user account to enable user-lingering:

```
$ loginctl enable-linger
```

| TIP | We recommend enabling user-lingering on all headless Raspberry Pi OS Lite setups to prevent your device from becoming unreachable after a remote reboot. |
| ----- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |

## Manage devices

The Connect dashboard lists all of the Raspberry Pi devices linked with your Raspberry Pi ID and shows you the various ways you can access them.

![list of devices](https://www.raspberrypi.com/documentation/services/images/list-of-devices.png?hash=e6b8b984af50f0a6a2bf598fd93196f7)

Click on a device name to open the device details page. This screen provides low-level information about your device. You can also edit the device name or remove the device from Connect.

![device details](https://www.raspberrypi.com/documentation/services/images/device-details.png?hash=febeb62918a3230fffe99e541e136a0f)

Deleting a device from Connect automatically signs you out of Connect on the device. The Connect system tray icon turns grey and the menu only provides a **Sign in** option.

## Update

To update to the latest version of Connect, run the following command:

```
$ sudo apt update
$ sudo apt install --only-upgrade rpi-connect
```

Reboot your device to put your update into effect:

```
$ sudo reboot
```

## Disconnect a device from Connect

Run the following command on your Raspberry Pi to sign out of your Raspberry Pi ID, which will disable your device on the Connect screen:

```
$ rpi-connect signout
```

| TIP | To fully remove a Raspberry Pi from your Connect account, [remove it from the Connect dashboard](https://www.raspberrypi.com/documentation/services/connect.html#manage-devices). |
| ----- | ------------------------------------------------------------- |

## Uninstall

Run the following command to remove Connect software from a Raspberry Pi:

```
$ sudo apt remove --purge rpi-connect
```

| TIP | If you installed Connect Lite, replace `rpi-connect` with `rpi-connect-lite` in the above command. |
| ----- | --------------------------------------------------------------------- |

After uninstalling, the serial number of the Raspberry Pi remains linked with your Raspberry Pi ID. The device still appears in the Connect dashboard, but can’t be used for remote access. If you install Connect again, even with a different SD card, on the same Raspberry Pi, it will reuse the existing device name in the Connect dashboard.

To sever the link between a Raspberry Pi and a Raspberry Pi ID, remove the Raspberry Pi from the list of devices in the Connect dashboard.

## Troubleshooting

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/services/connect/troubleshooting.adoc)

### Known issues

* Screen sharing only supports sharing a single, primary display of your Raspberry Pi. When a Raspberry Pi is connected to multiple HDMI screens, Connect sometimes shares the contents of the secondary screen. You can work around this by right-clicking the desktop and changing the location of the taskbar in **Desktop Preferences…** .
* Connect does not support on-screen keyboards. For full functionality, use a physical keyboard.
* Connect requires a browser that implements [ECMAScript 2020](https://caniuse.com/?search=es2020) (ES11) as it makes use of [features](https://caniuse.com/?feats=mdn-javascript_operators_optional_chaining,mdn-javascript_operators_nullish_coalescing,mdn-javascript_builtins_globalthis,es6-module-dynamic-import,bigint,mdn-javascript_builtins_promise_allsettled,mdn-javascript_builtins_string_matchall,mdn-javascript_statements_export_namespace,mdn-javascript_operators_import_meta) unavailable in older browsers.
* Browsers intercept certain keys and key combinations. As a result, you can’t type these keys into your Connect window. Screen sharing includes a toolbar to simulate some of the most popular intercepted keys.

### View Connect status

To view the current status of the Connect service, run the following command:

```
$ rpi-connect status
```

The output of this command indicates whether or not you are currently signed in to Connect, as well as the remote services enabled on your Raspberry Pi.

### Enable enhanced logging

You can enable debug logging for both `rpi-connect` and its dedicated WayVNC server for a detailed account of local operations on your Raspberry Pi.

#### Enable enhanced logging in `rpi-connect`

Open the `rpi-connect` configuration file for editing with the following command:

```
$ systemctl --user edit rpi-connect
```

Enter the following lines of configuration between the comments:

```
ExecStart=
ExecStart=/usr/bin/rpi-connectd -socket %t/rpi-connect-wayvnc.sock -v
```

| NOTE | You need **both** lines that begin with `ExecStart=`. |
| ------ | ----------------------------------- |

Finally, restart the service with the following command:

```
$ systemctl --user restart rpi-connect
```

#### Enable enhanced logging in the dedicated `wayvnc` server

Open the configuration file for the dedicated WayVNC server associated with Connect:

```
$ systemctl --user edit rpi-connect-wayvnc
```

Enter the following lines of configuration between the comments:

```
ExecStart=
ExecStart=/usr/bin/rpi-connect-env /usr/bin/wayvnc --config /etc/rpi-connect/wayvnc.config --render-cursor --unix-socket --socket=%t/rpi-connect-wayvnc-ctl.sock -Ldebug %t/rpi-connect-wayvnc.sock
```

| NOTE | You need **both** lines that begin with `ExecStart=`. |
| ------ | ----------------------------------- |

Finally, restart the service with the following command:

```
$ systemctl --user restart rpi-connect-wayvnc
```

### View Connect logs

To view logs for the Connect service and its dedicated WayVNC server, run the following command:

```
$ journalctl --user --follow --unit rpi-connect --unit rpi-connect-wayvnc
```
