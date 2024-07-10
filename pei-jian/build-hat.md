# Build HAT

## About

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/accessories/build-hat/introduction.adoc)

The [Raspberry Pi Build HAT](https://raspberrypi.com/products/build-hat) is an add-on board that connects to the 40-pin GPIO header of your Raspberry Pi, which was designed in collaboration with LEGO® Education to make it easy to control LEGO® Technic™ motors and sensors with Raspberry Pi computers.

![build hat](https://www.raspberrypi.com/documentation/accessories/images/build-hat.jpg?hash=98708c929a91f5d5edf372371b2b7c6c)

| NOTE | A full list of supported devices can be found in the [Device Compatibility](https://www.raspberrypi.com/documentation/accessories/build-hat.html#device-compatibility) section. |
| ------ | ---------------------------------------------------------------- |

It provides four connectors for LEGO® Technic™ motors and sensors from the SPIKE™ Portfolio. The available sensors include a distance sensor, a colour sensor, and a versatile force sensor. The angular motors come in a range of sizes and include integrated encoders that can be queried to find their position.

The Build HAT fits all Raspberry Pi computers with a 40-pin GPIO header, including, with the addition of a ribbon cable or other extension device, Raspberry Pi 400. Connected LEGO® Technic™ devices can easily be controlled in Python, alongside standard Raspberry Pi accessories such as a camera module.

The Raspberry Pi Build HAT power supply (PSU), which is [available separately](https://raspberrypi.com/products/build-hat-power-supply), is designed to power both the Build HAT and Raspberry Pi computer along with all connected LEGO® Technic™ devices.

![psu](https://www.raspberrypi.com/documentation/accessories/images/psu.jpg?hash=b1bafd5ae45d03c691dda612eae68798)

The LEGO® Education SPIKE™ Prime Set 45678 and SPIKE™ Prime Expansion Set 45681, available separately from LEGO® Education resellers, include a collection of useful elements supported by the Build HAT.

| NOTE | The HAT works with all 40-pin GPIO Raspberry Pi boards, including Raspberry Pi 4 and Raspberry Pi Zero. With the addition of a ribbon cable or other extension device, it can also be used with Raspberry Pi 400. |
| ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

* Controls up to 4 LEGO® Technic™ motors and sensors included in the SPIKE™ Portfolio
* Easy-to-use [Python library](https://buildhat.readthedocs.io/) to control your LEGO® Technic™ devices
* Fits onto any Raspberry Pi computer with a 40-pin GPIO header
* Onboard [RP2040](https://www.raspberrypi.com/documentation/microcontrollers/rp2040.html) microcontroller manages low-level control of LEGO® Technic™ devices
* External 8V PSU [available separately](https://raspberrypi.com/products/build-hat-power-supply) to power both Build HAT and Raspberry Pi

| NOTE | The Build HAT cannot power the Raspberry Pi 400, since it does not support power supply over the GPIO headers. |
| ------ | ---------------------------------------------------------------------------------------------------------------- |

## Prepare your Build HAT

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/accessories/build-hat/preparing-build-hat.adoc)

| NOTE | Before starting to work with your Raspberry Pi Build HAT you should [set up](https://www.raspberrypi.com/documentation/computers/getting-started.html#setting-up-your-raspberry-pi) your Raspberry Pi, [install](https://www.raspberrypi.com/documentation/computers/getting-started.html#installing-the-operating-system) the latest version of the operating system using [Raspberry Pi Imager](https://www.raspberrypi.com/downloads/). |
| ------ | --------------------------------------------------------------------------------------------------------------------------------------------- |

Attach 9mm spacers to the bottom of the board. Seat the Raspberry Pi Build HAT onto your Raspberry Pi. Make sure you put it on the right way up. Unlike other HATs, all the components are on the bottom, leaving room for a breadboard or LEGO® elements on top.

![fitting build hat](https://www.raspberrypi.com/documentation/accessories/images/fitting-build-hat.gif?hash=929b2b4879e4a3d3a7ad5081809fa4ba)

### Access the GPIO Pins

If you want to access the GPIO pins of the Raspberry Pi, you can add an optional tall header and use 15 mm spacers.

![tall headers](https://www.raspberrypi.com/documentation/accessories/images/tall-headers.png?hash=95d6f32dec4094416cdbfaa362410725)

The following pins are used by the Build HAT itself and you should not connect anything to them.

| GPIO    | Use     | Status |
| --------- | --------- | -------- |
| GPIO0/1 | ID prom |        |
| GPIO4   | Reset   |        |
| GPIO14  | Tx      |        |
| GPIO15  | Rx      |        |
| GPIO16  | RTS     | unused |
| GPIO17  | CTS     | unused |

### Set up your Raspberry Pi

Once the Raspberry Pi has booted, open the Raspberry Pi Configuration tool by clicking on the Raspberry Menu button and then selecting "Preferences" and then "Raspberry Pi Configuration".

Click on the "interfaces" tab and adjust the Serial settings as shown below:

![setting up](https://www.raspberrypi.com/documentation/accessories/images/setting-up.png?hash=6c6c522cf51dd6d8e0bd06d39f49f500)

#### Use your Raspberry Pi headless

If you are running your Raspberry Pi headless and using `raspi-config`, select "Interface Options" from the first menu.

![raspi config 1](https://www.raspberrypi.com/documentation/accessories/images/raspi-config-1.png?hash=89492f1233dedb9cdb1589256744d875)

Then "P6 Serial Port".

![raspi config 2](https://www.raspberrypi.com/documentation/accessories/images/raspi-config-2.png?hash=08f1dc42212a007ffeeb6a9d98d6c0be)

Disable the serial console:

![raspi config 3](https://www.raspberrypi.com/documentation/accessories/images/raspi-config-3.png?hash=ec94440de42b2aa66e6b55e87cc2459d)

And enable the serial port hardware.

![raspi config 4](https://www.raspberrypi.com/documentation/accessories/images/raspi-config-4.png?hash=9f559ca55fa956d3480e115ee5679be7)

The final settings should look like this.

![raspi config 5](https://www.raspberrypi.com/documentation/accessories/images/raspi-config-5.png?hash=90b69d8b96f0a410cd6b85c7594f508d)

You will need to reboot at this point if you have made any changes.

### Power the Build HAT

Connect an external power supply — the [official Raspberry Pi Build HAT power supply](https://raspberrypi.com/products/build-hat-power-supply) is recommended — however any reliable +8V±10% power supply capable of supplying 48W via a DC 5521 centre positive barrel connector (5.5mm × 2.1mm × 11mm) will power the Build HAT. You don’t need to connect an additional USB power supply to the Raspberry Pi as well, unless you are using a Raspberry Pi 400.

| NOTE | The Build HAT can not power the Raspberry Pi 400 as it does not support being powered via the GPIO headers. |
| ------ | ------------------------------------------------------------------------------------------------------------- |

![powering build hat](https://www.raspberrypi.com/documentation/accessories/images/powering-build-hat.gif?hash=227d69a9a1e933151914a385a219f9e7)

| NOTE | The LEGO® Technic™ motors are very powerful; so to drive them you’ll need an external 8V power supply. If you want to read from motor encoders and the SPIKE™ force sensor, you can power your Raspberry Pi and Build HAT the usual way, via your Raspberry Pi’s USB power socket. The SPIKE™ colour and distance sensors, like the motors, require an [external power supply](https://raspberrypi.com/products/build-hat-power-supply). |
| ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

You have the choice to use Build HAT with Python or .NET.

## Use the Build HAT from Python

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/accessories/build-hat/py-installing-software.adoc)

### Install the Build HAT Python Library

To install the Build HAT Python library, open a terminal window and run the following command:

```
$ sudo apt install python3-build-hat
```

Raspberry Pi OS versions prior to *Bookworm* do not have access to the library with `apt`. Instead, run the following command to install the library using `pip`:

```
$ sudo pip3 install buildhat
```

For more information about the Build HAT Python Library see [ReadTheDocs](https://buildhat.readthedocs.io/).

### Use Motors from Python

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/accessories/build-hat/py-motors.adoc)

There are [a number of motors](https://www.raspberrypi.com/documentation/accessories/build-hat.html#device-compatibility) that work with the Build HAT.

#### Connect a Motor

Connect a motor to port A on the Build HAT. The LPF2 connectors need to be inserted the correct way up. If the connector doesn’t slide in easily, rotate by 180 degrees and try again.

![connect motor](https://www.raspberrypi.com/documentation/accessories/images/connect-motor.gif?hash=a8e7c413aa470e3a5d85059fa170ab70)

#### Work with Motors

Start the [Thonny IDE](https://thonny.org/). Add the program code below:

```
from buildhat import Motor

motor_a = Motor('A')

motor_a.run_for_seconds(5)
```

Run the program by clicking the play/run button. If this is the first time you’re running a Build HAT program since the Raspberry Pi has booted, there will be a few seconds pause while the firmware is copied across to the board. You should see the red LED extinguish and the green LED illuminate. Subsequent executions of a Python program will not require this pause.

![blinking light](https://www.raspberrypi.com/documentation/accessories/images/blinking-light.gif?hash=db99f6501e955b2832f80fa975ca42e3)

Your motor should turn clockwise for 5 seconds.

![turning motor](https://www.raspberrypi.com/documentation/accessories/images/turning-motor.gif?hash=1300a4c765178f6863a8b6a8e311a1e2)

Change the final line of your program and re-run.

```
motor_a.run_for_seconds(5, speed=50)
```

The motor should now turn faster. Make another change:

```
motor_a.run_for_seconds(5, speed=-50)
```

The motor should turn in the opposite (anti-clockwise) direction

Create a new program by clicking on the plus button in Thonny. Add the code below:

```
from buildhat import Motor

motor_a = Motor('A')

while True:
    print("Position: ", motor_a.get_aposition())
```

Run the program. Grab the motor and turn the shaft. You should see the numbers printed in the Thonny REPL changing.

### Use Sensors from Python

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/accessories/build-hat/py-sensors.adoc)

There is a [large range of sensors](https://www.raspberrypi.com/documentation/accessories/build-hat.html#device-compatibility) that work with the Build HAT.

#### Work with Sensors

Connect a Colour sensor to port B on the Build HAT, and a Force sensor to port C.

| NOTE | If you’re not intending to drive a motor, then you don’t need an external power supply and you can use a standard USB power supply for your Raspberry Pi. |
| ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |

Create another new program:

```
from signal import pause
from buildhat import ForceSensor, ColorSensor

button = ForceSensor('C')
cs = ColorSensor('B')

def handle_pressed(force):
    cs.on()
    print(cs.get_color())

def handle_released(force):
    cs.off()

button.when_pressed = handle_pressed
button.when_released = handle_released
pause()
```

Run it and hold a coloured object (LEGO® elements are ideal) in front of the colour sensor and press the Force sensor plunger. The sensor’s LED should switch on and the name of the closest colour should be displayed in the Thonny REPL.

## Use the Build HAT from .NET

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/accessories/build-hat/net-installing-software.adoc)

### Install the .NET Framework

The .NET framework from Microsoft is not available via `apt` on Raspberry Pi. However, you can follow the [official instructions](https://docs.microsoft.com/en-us/dotnet/iot/deployment) from Microsoft to install the .NET framework. Alternatively, there is a simplified [third party route](https://www.petecodes.co.uk/install-and-use-microsoft-dot-net-5-with-the-raspberry-pi/) to get the .NET toolchain on to your Raspberry Pi.

| WARNING | The installation script is run as `root`. You should read it first and make sure you understand what it is doing. If you are at all unsure you should follow the [official instructions](https://docs.microsoft.com/en-us/dotnet/iot/deployment) manually. |
| --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

```
$ wget -O - https://raw.githubusercontent.com/pjgpetecodes/dotnet5pi/master/install.sh | sudo bash
```

After installing the .NET framework you can create your project:

```
$ dotnet new console --name buildhat
```

This creates a default program in the `buildhat` subdirectory, and we need to be in that directory in order to continue:

```
$ cd buildhat
```

You will now need to install the following nuget packages:

```
$ dotnet add package System.Device.Gpio --version 2.1.0
$ dotnet add package Iot.Device.Bindings --version 2.1.0
```

### Run C# Code

You can run the program with the `dotnet run` command. Let’s try it now to make sure everything works. It should print "Hello World!"

```
$ dotnet run
Hello World!
```

(When instructed to "run the program" in the instructions that follow, you will simply rerun `dotnet run`)

### Edit C# Code

In the instructions below, you will be editing the file `buildhat/Program.cs`, the C# program which was generated when you ran the above commands.

Any text editor will work to edit C# code, including Geany, the IDE/Text Editor that comes pre-installed. [Visual Studio Code](https://code.visualstudio.com/docs/setup/raspberry-pi/) (often called "VS Code") is also a popular alternative.

### Use the Build HAT from .NET

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/accessories/build-hat/net-brick.adoc)

The Raspberry Pi Built HAT is referred to "Brick" in LEGO® parlance and you can talk directly to it from .NET using the [Build HAT Serial Protocol](https://datasheets.raspberrypi.com/build-hat/build-hat-serial-protocol.pdf).

You can create a `brick` object as below,

```
Brick brick = new("/dev/serial0");
```

but you need to remember to dispose of the `brick` at the end of your code.

```
brick.Dispose();
```

| WARNING | If you do not call `brick.Dispose()` your program will not terminate. |
| --------- | ------------------------------------------------------ |

If you want to avoid calling `brick.Dispose` at the end, then create your brick with the `using` statement:

```
using Brick brick = new("/dev/serial0");
```

In this case, when reaching the end of the program, your brick will be automatically disposed.

#### Display Build HAT information

You can gather the various software versions, the signature, and the input voltage:

```
var info = brick.BuildHatInformation;
Console.WriteLine($"version: {info.Version}, firmware date: {info.FirmwareDate}, signature:");
Console.WriteLine($"{BitConverter.ToString(info.Signature)}");
Console.WriteLine($"Vin = {brick.InputVoltage.Volts} V");
```

| NOTE | The input voltage is read only once at boot time and is not read again afterwards. |
| ------ | ------------------------------------------------------------------------------------ |

#### Getting sensors and motors details

The functions `GetSensorType`, `GetSensor` will allow you to retrieve any information on connected sensor.

```
SensorType sensor = brick.GetSensorType((SensorPort)i);
Console.Write($"Port: {i} {(Brick.IsMotor(sensor) ? "Sensor" : "Motor")} type: {sensor} Connected: ");
```

In this example, you can as well use the `IsMotor` static function to check if the connected element is a sensor or a motor.

```
if (Brick.IsActiveSensor(sensor))
{
    ActiveSensor activeSensor = brick.GetActiveSensor((SensorPort)i);
}
else
{
    var passive = (Sensor)brick.GetSensor((SensorPort)i);
    Console.WriteLine(passive.IsConnected);
}
```

`ActiveSensor` have a collection of advanced properties and functions allowing to understand every element of the sensor. It is also possible to call the primitive functions from the brick from them. This will allow you to select specific modes and do advance scenarios. While this is possible, motor and sensor classes have been created to make your life easier.

#### Events

Most sensors implements events on their special properties. You can simply subscribe to `PropertyChanged` and `PropertyUpdated`. The changed one will be fired when the value is changing while the updated one when there is a success update to the property. Depending on the modes used, some properties may be updated in the background all the time while some others occasionally.

You may be interested only when a colour is changing or the position of the motor is changing, using it as a tachometer. In this case, the `PropertyChanged` is what you need!

```
Console.WriteLine("Move motor on Port A to more than position 100 to stop this test.");
brick.WaitForSensorToConnect(SensorPort.PortA);
var active = (ActiveMotor)brick.GetMotor(SensorPort.PortA);
bool continueToRun = true;
active.PropertyChanged += MotorPropertyEvent;
while (continueToRun)
{
    Thread.Sleep(50);
}

active.PropertyChanged -= MotorPropertyEvent;
Console.WriteLine($"Current position: {active.Position}, eventing stopped.");

void MotorPropertyEvent(object? sender, PropertyChangedEventArgs e)
{
    Console.WriteLine($"Property changed: {e.PropertyName}");
    if (e.PropertyName == nameof(ActiveMotor.Position))
    {
        if (((ActiveMotor)brick.GetMotor(SensorPort.PortA)).Position > 100)
        {
            continueToRun = false;
        }
    }
}
```

#### Wait for initialization

The brick can take a long time before it initializes. A wait for a sensor to be connected has been implemented.

```
brick.WaitForSensorToConnect(SensorPort.PortB);
```

It does as well take a `CancellationToken` if you want to implement advance features like warning the user after some time and retrying.

### Use Motors from .NET

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/accessories/build-hat/net-motors.adoc)

There are two types of motors, the **passive** ones and the **active** ones. Active motors will provide detailed position, absolute position and speed while passive motors can only be controlled with speed.

A common set of functions to control the speed of the motors are available. There are 2 important ones: `SetPowerLimit` and `SetBias`:

```
train.SetPowerLimit(1.0);
train.SetBias(0.2);
```

The accepted values are only from 0.0 to 1.0. The power limit is a convenient ay to reduce in proportion the maximum power.

The bias value sets for the current port which is added to positive motor drive values and subtracted from negative motor drive values. This can be used to compensate for the fact that most DC motors require a certain amount of drive before they will turn at all.

The default values when a motor is created is 0.7 for the power limit and 0.3 for the bias.

#### Passive Motors

![Train motor](https://www.raspberrypi.com/documentation/accessories/images/train-motor.png?hash=45e2bbc3373b91434b8c75071c6f18cd)

Train motor, [Image from Bricklink](https://www.bricklink.com/v2/catalog/catalogitem.page?S=88011-1&name=Train%20Motor&category=%5BPower%20Functions%5D%5BPowered%20Up%5D#T=S&O={%22iconly%22:0})

The typical passive motor is a train and older Powered Up motors. The `Speed` property can be set and read. It is the target and the measured speed at the same time as those sensors do not have a way to measure them. The value is from -100 to +100.

Functions to control `Start`, `Stop` and `SetSpeed` are also available. Here is an example of how to use it:

```
Console.WriteLine("This will run the motor for 20 secondes incrementing the PWM");
train.SetPowerLimit(1.0);
train.Start();
for (int i = 0; i < 100; i++)
{
    train.SetSpeed(i);
    Thread.Sleep(250);
}

Console.WriteLine("Stop the train for 2 seconds");
train.Stop();
Thread.Sleep(2000);
Console.WriteLine("Full speed backward for 2 seconds");
train.Start(-100);
Thread.Sleep(2000);
Console.WriteLine("Full speed forward for 2 seconds");
train.Start(100);
Thread.Sleep(2000);
Console.WriteLine("Stop the train");
train.Stop();
```

| NOTE | Once the train is started, you can adjust the speed and the motor will adjust accordingly. |
| ------ | -------------------------------------------------------------------------------------------- |

#### Active Motors

![Active motor](https://www.raspberrypi.com/documentation/accessories/images/active-motor.png?hash=4f7f24df8bd5349ffa4a6055d71a4919)

Active motor, [Image from Bricklink](https://www.bricklink.com/v2/catalog/catalogitem.page?S=88014-1&name=Technic%20XL%20Motor&category=%5BPower%20Functions%5D%5BPowered%20Up%5D#T=S&O={%22iconly%22:0})

Active motors have `Speed`, `AbsolutePosition`, `Position` and `TargetSpeed` as special properties. They are read continuously even when the motor is stopped.

The code snippet shows how to get the motors, start them and read the properties:

```
brick.WaitForSensorToConnect(SensorPort.PortA);
brick.WaitForSensorToConnect(SensorPort.PortD);
var active = (ActiveMotor)brick.GetMotor(SensorPort.PortA);
var active2 = (ActiveMotor)brick.GetMotor(SensorPort.PortD);
active.Start(50);
active2.Start(50);
// Make sure you have an active motor plug in the port A and D
while (!Console.KeyAvailable)
{
    Console.CursorTop = 1;
    Console.CursorLeft = 0;
    Console.WriteLine($"Absolute: {active.AbsolutePosition}     ");
    Console.WriteLine($"Position: {active.Position}     ");
    Console.WriteLine($"Speed: {active.Speed}     ");
    Console.WriteLine();
    Console.WriteLine($"Absolute: {active2.AbsolutePosition}     ");
    Console.WriteLine($"Position: {active2.Position}     ");
    Console.WriteLine($"Speed: {active2.Speed}     ");
}

active.Stop();
active2.Stop();
```

| NOTE | Don’t forget to start and stop your motors when needed. |
| ------ | ---------------------------------------------------------- |

Advance features are available for active motors. You can request to move for seconds, to a specific position, a specific absolute position. Here are couple of examples:

```
// From the previous example, this will turn the motors back to their initial position:
active.TargetSpeed = 100;
active2.TargetSpeed = 100;
// First this motor and will block the thread
active.MoveToPosition(0, true);
// Then this one and will also block the thread
active2.MoveToPosition(0, true);
```

Each function allow you to block or not the thread for the time the operation will be performed. Note that for absolute and relative position moves, there is a tolerance of few degrees.

```
brick.WaitForSensorToConnect(SensorPort.PortA);
var active = (ActiveMotor)brick.GetMotor(SensorPort.PortA);
active.TargetSpeed = 70;
Console.WriteLine("Moving motor to position 0");
active.MoveToPosition(0, true);
Console.WriteLine("Moving motor to position 3600 (10 turns)");
active.MoveToPosition(3600, true);
Console.WriteLine("Moving motor to position -3600 (so 20 turns the other way");
active.MoveToPosition(-3600, true);
Console.WriteLine("Moving motor to absolute position 0, should rotate by 90°");
active.MoveToAbsolutePosition(0, PositionWay.Shortest, true);
Console.WriteLine("Moving motor to position 90");
active.MoveToAbsolutePosition(90, PositionWay.Shortest, true);
Console.WriteLine("Moving motor to position 179");
active.MoveToAbsolutePosition(179, PositionWay.Shortest, true);
Console.WriteLine("Moving motor to position -180");
active.MoveToAbsolutePosition(-180, PositionWay.Shortest, true);
active.Float();
```

You can place the motor in a float position, meaning, there are no more constrains on it. This is a mode that you can use when using the motor as a tachometer, moving it and reading the position. If you still have constrains on the motors, you may not be able to move it.

### Use Sensors from .NET

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/accessories/build-hat/net-sensors.adoc)

Like for motors, you have active and passive sensors. Most recent sensors are active. The passive one are lights and simple buttons. Active ones are distance or colour sensors, as well as small 3×3 pixel displays.

#### Button/Touch Passive Sensor

The button/touch passive sensor have one specific property `IsPressed`. The property is set to true when the button is pressed. Here is a complete example with events:

```
brick.WaitForSensorToConnect(SensorPort.PortA);
var button = (ButtonSensor)brick.GetSensor(SensorPort.PortA);
bool continueToRun = true;
button.PropertyChanged += ButtonPropertyEvent;
while (continueToRun)
{
    // You can do many other things here
    Thread.Sleep(50);
}

button.PropertyChanged -= ButtonPropertyEvent;
Console.WriteLine($"Button has been pressed, we're stopping the program.");
brick.Dispose();

void ButtonPropertyEvent(object? sender, PropertyChangedEventArgs e)
{
    Console.WriteLine($"Property changed: {e.PropertyName}");
    if (e.PropertyName == nameof(ButtonSensor.IsPressed))
    {
        continueToRun = false;
    }
}
```

#### Passive Light

![Passive light](https://www.raspberrypi.com/documentation/accessories/images/passive-light.png?hash=cf48cfe5f8d00496aa67d1ed716e6ddc)

Passive light, [Image from Bricklink](https://www.bricklink.com/v2/catalog/catalogitem.page?P=22168c01&name=Electric,%20Light%20Unit%20Powered%20Up%20Attachment&category=%5BElectric,%20Light%20&%20Sound%5D#T=C&C=11)

The passive light are the train lights. They can be switched on and you can controlled their brightness.

```
brick.WaitForSensorToConnect(SensorPort.PortA);
var light = (PassiveLight)brick.GetSensor(SensorPort.PortA);
// Brightness 50%
light.On(50);
Thread.Sleep(2000);
// 70% Brightness
light.Brightness = 70;
Thread.Sleep(2000);
// Switch light off
light.Off()
```

#### Active Sensor

The active sensor class is a generic one that all the active sensor inherit including active motors. They contains a set of properties regarding how they are connected to the Build HAT, the modes, the detailed Combi modes, the hardware, software versions and a specific property called `ValueAsString`. The value as string contains the last measurement as a collection of strings. A measurement arrives like `P0C0: +23 -42 0`, the enumeration will contains `P0C0:`, `+23`, `-42` and `0`. This is made so if you are using advance modes and managing yourself the Combi modes and commands, you’ll be able to get the measurements.

All active sensor can run a specific measurement mode or a Combi mode. You can setup one through the advance mode using the `SelectModeAndRead` and `SelectCombiModesAndRead` functions with the specific mode(s) you’d like to continuously have. It is important to understand that changing the mode or setting up a new mode will stop the previous mode.

The modes that can be combined in the Combi mode are listed in the `CombiModes` property. Al the properties of the sensors will be updated automatically when you’ll setup one of those modes.

#### WeDo Tilt Sensor

![WeDo Tilt sensor](https://www.raspberrypi.com/documentation/accessories/images/wedo-tilt.png?hash=83605c1b3fc4c579b417ba2f9ad74de6)

WeDo Tilt sensor, [Image from Bricklink](https://www.bricklink.com/v2/catalog/catalogitem.page?S=45305-1&name=WeDo%202.0%20Tilt%20Sensor&category=%5BEducational%20&%20Dacta%5D%5BWeDo%5D#T=S&O={%22iconly%22:0})

WeDo Tilt Sensor has a special `Tilt` property. The type is a point with X is the X tilt and Y is the Y tilt. The values goes from -45 to + 45, they are caped to those values and represent degrees.

You can set a continuous measurement for this sensor using the `ContinuousMeasurement` property.

```
brick.WaitForSensorToConnect(SensorPort.PortA);
var tilt = (WeDoTiltSensor)brick.GetSensor(SensorPort.PortA);
tilt.ContinuousMeasurement = true;
Point tiltValue;
while(!console.KeyAvailable)
{
    tiltValue = tilt.Tilt;
    console.WriteLine($"Tilt X: {tiltValue.X}, Tilt Y: {tiltValue.Y}");
    Thread.Sleep(200);
}
```

#### WeDoDistance Sensor

![WeDo Distance sensor](https://www.raspberrypi.com/documentation/accessories/images/wedo-distance.png?hash=97b4594548fae6f272fb66b815d57f0e)

WeDo Distance sensor, [Image from Bricklink](https://www.bricklink.com/v2/catalog/catalogitem.page?S=45304-1&name=WeDo%202.0%20Motion%20Sensor&category=%5BEducational%20&%20Dacta%5D%5BWeDo%5D#T=S&O={%22iconly%22:0})

WeDo Distance Sensor gives you a distance in millimetres with the Distance property.

```
brick.WaitForSensorToConnect(SensorPort.PortA);
var distance = (WeDoDistanceSensor)brick.GetSensor(SensorPort.PortA);
distance.ContinuousMeasurement = true;
while(!console.KeyAvailable)
{
    console.WriteLine($"Distance: {distance.Distance} mm");
    Thread.Sleep(200);
}
```

#### SPIKE Prime Force Sensor

![spike force sensor](https://www.raspberrypi.com/documentation/accessories/images/spike-force.png?hash=00c39c3c0c78f50f22a387914dbd14e1)

Spike Force Sensor, [Image from Bricklink](https://www.bricklink.com/v2/catalog/catalogitem.page?P=37312c01&name=Electric%20Sensor,%20Force%20-%20Spike%20Prime&category=%5BElectric%5D#T=C&C=11)

This force sensor measure the pressure applies on it and if it is pressed. The two properties can be access through `Force` and `IsPressed` properties.

```
brick.WaitForSensorToConnect(SensorPort.PortA);
var force = (ForceSensor)brick.GetSensor(SensorPort.PortA);
force.ContinuousMeasurement = true;
while(!force.IsPressed)
{
    console.WriteLine($"Force: {force.Force} N");
    Thread.Sleep(200);
}
```

#### SPIKE Essential 3×3 Colour Light Matrix

![spike 3×3 matrix](https://www.raspberrypi.com/documentation/accessories/images/3x3matrix.png?hash=e9e1cdd646b22cfd0d3bd09b97394377)

spike 3×3 matrix, [Image from Bricklink](https://www.bricklink.com/v2/catalog/catalogitem.page?P=45608c01&name=Electric,%203%20x%203%20Color%20Light%20Matrix%20-%20SPIKE%20Prime&category=%5BElectric%5D#T=C)

This is a small 3×3 display with 9 different LEDs that can be controlled individually. The class exposes functions to be able to control the screen. Here is an example using them:

```
brick.WaitForSensorToConnect(SensorPort.PortA);
var matrix = (ColorLightMatrix)brick.GetSensor(SensorPort.PortA);
for(byte i = 0; i < 10; i++)
{
    // Will light every led one after the other like a progress bar
    matrix.DisplayProgressBar(i);
    Thread.Sleep(1000);
}

for(byte i = 0; i < 11; i++)
{
    // Will display the matrix with the same color and go through all of them
    matrix.DisplayColor((LedColor)i);
    Thread.Sleep(1000);
}

Span<byte> brg = stackalloc byte[9] { 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Span<LedColor> col = stackalloc LedColor[9] { LedColor.White, LedColor.White, LedColor.White,
  LedColor.White, LedColor.White, LedColor.White, LedColor.White, LedColor.White, LedColor.White };
// Shades of grey
matrix.DisplayColorPerPixel(brg, col);
```

#### SPIKE Prime Colour Sensor and Colour and Distance Sensor

SPIKE colour sensor:

![spike color sensor](https://www.raspberrypi.com/documentation/accessories/images/spike-color.png?hash=416c9a57308a1190b3a739ef89945c0c)

spike colour sensor, [Image from Bricklink](https://www.bricklink.com/v2/catalog/catalogitem.page?P=37308c01&name=Electric%20Sensor,%20Color%20-%20Spike%20Prime&category=%5BElectric%5D#T=C&C=11)

Colour and distance sensor:

![Colour distance sensor](https://www.raspberrypi.com/documentation/accessories/images/color-distance.png?hash=cc8150aa44c484eea159b5f70d8ab256)

Color distance sensor, [Image from Bricklink](https://www.bricklink.com/v2/catalog/catalogitem.page?P=bb0891c01&name=Electric%20Sensor,%20Color%20and%20Distance%20-%20Boost&category=%5BElectric%5D#T=C&C=1)

Those colour sensor has multiple properties and functions. You can get the `Color`, the `ReflectedLight` and the `AmbiantLight`.

On top of this, the Colour and Distance sensor can measure the `Distance` and has an object `Counter`. It will count automatically the number of objects which will go in and out of the range. This does allow to count objects passing in front of the sensor. The distance is limited from 0 to 10 centimetres.

```
brick.WaitForSensorToConnect(SensorPort.PortC);

var colorSensor = (ColorAndDistanceSensor)brick.GetActiveSensor(SensorPort.PortC);
while (!Console.KeyAvailable)
{
    var colorRead = colorSensor.GetColor();
    Console.WriteLine($"Color:     {colorRead}");
    var reflected = colorSensor.GetReflectedLight();
    Console.WriteLine($"Reflected: {reflected}");
    var ambiant = colorSensor.GetAmbiantLight();
    Console.WriteLine($"Ambiant:   {ambiant}");
    var distance = colorSensor.GetDistance();
    Console.WriteLine($"Distance: {distance}");
    var counter = colorSensor.GetCounter();
    Console.WriteLine($"Counter:  {counter}");
    Thread.Sleep(200);
}
```

| NOTE | For better measurement, it is not recommended to change the measurement mode in a very fast way, the colour integration may not be done in a proper way. This example gives you the full spectrum of what you can do with the sensor. Also, this class do not implement a continuous measurement mode. You can setup one through the advance mode using the `SelectModeAndRead` function with the specific mode you’d like to continuously have. It is important to understand that changing the mode or setting up a new mode will stop the previous mode. |
| ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

#### SPIKE Prime Ultrasonic Distance Sensor

![Spike distance sensor](https://www.raspberrypi.com/documentation/accessories/images/spike-distance.png?hash=42a524aab9242bf860bf744f2dcf0e63)

Spike distance sensor, [Image from Bricklink](https://www.bricklink.com/v2/catalog/catalogitem.page?P=37316c01&name=Electric%20Sensor,%20Distance%20-%20Spike%20Prime&category=%5BElectric%5D#T=C&C=11)

This is a distance sensor and it does implement a `Distance` property that will give the distance in millimetre. A `ContinuousMeasurement` mode is also available on this one.

```
brick.WaitForSensorToConnect(SensorPort.PortA);
var distance = (UltrasonicDistanceSensor)brick.GetSensor(SensorPort.PortA);
distance.ContinuousMeasurement = true;
while(!console.KeyAvailable)
{
    console.WriteLine($"Distance: {distance.Distance} mm");
    Thread.Sleep(200);
}
```

## Further Resources

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/accessories/build-hat/links-to-other.adoc)

You can download documentation on the,

* [Raspberry Pi Build HAT Serial Protocol](https://datasheets.raspberrypi.com/build-hat/build-hat-serial-protocol.pdf)
* [Raspberry Pi Build HAT Python Library](https://datasheets.raspberrypi.com/build-hat/build-hat-python-library.pdf)

and full details of the Python Library documentation can also be found [on ReadTheDocs](https://buildhat.readthedocs.io/). You can find more information on the .NET library in the [.NET IoT](https://github.com/dotnet/iot/tree/main/src/devices/BuildHat) Github repository.

You can also follow along with projects from the Raspberry Pi Foundation,

* [LEGO® Game Controller](https://projects.raspberrypi.org/en/projects/lego-game-controller)
* [LEGO® Robot Car](https://projects.raspberrypi.org/en/projects/lego-robot-car)
* [LEGO® Plotter](https://projects.raspberrypi.org/en/projects/lego-plotter)
* [LEGO® Robot Face](https://projects.raspberrypi.org/en/projects/lego-robot-face)
* [LEGO® Data Dash](https://projects.raspberrypi.org/en/projects/lego-data-dash)

## Device Compatibility

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/accessories/build-hat/compat.adoc)

The Build HAT library supports all the LEGO® Technic™ devices included in the SPIKE™ Portfolio, along with those from the LEGO® Mindstorms Robot Inventor kit and other devices that use a PoweredUp connector.

| IMPORTANT | The product code for the SPIKE™ Prime Expansion Set that includes the Maker Plate is 45681. The original Expansion Set is 45680 and does not include the Maker Plate. |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |

| Description              | Colour      | LEGO Item Number                 | Supported in FW | Supported in Python | Alt Number     | BrickLink | Available In                                                                            | Set Numbers         | Class          | Type    | Device ID |
| -------------------------- | ------------- | ---------------------------------- | ----------------- | --------------------- | ---------------- | ----------- | ----------------------------------------------------------------------------------------- | --------------------- | ---------------- | --------- | ----------- |
| Large Angular Motor      | White/Cyan  | 45602                            | Yes             | Yes                 | 45602          | [Link](https://www.bricklink.com/v2/catalog/catalogitem.page?S=45602-1#T=S&O={%22iconly%22:0})          | SPIKE Prime Set, SPIKE Prime Expansion Set                                              | 45678, 45680        | Motor          | Active  | 31        |
| Medium Angular Motor     | White/Cyan  | 45603                            | Yes             | Yes                 | 45603          | [Link](https://www.bricklink.com/v2/catalog/catalogitem.page?S=45603-1#T=S&O={%22iconly%22:0})          | SPIKE Prime Set                                                                         | 45678               | Motor          | Active  | 30        |
| Medium Angular Motor     | White/Grey  | 6299646, 6359216, 6386708        | Yes             | Yes                 | 436655         | [Link](https://www.bricklink.com/v2/catalog/catalogitem.page?P=54696c01&idColor=86#T=C&C=86)          | Mindstorms Robot Inventor                                                               | 51515               | Motor          | Active  | 4B        |
| Small Angular Motor      | White/Cyan  | 45607, 6296520                   | Yes             | Yes                 |                | [Link](https://www.bricklink.com/v2/catalog/catalogitem.page?P=45607c01)          | SPIKE Essentials Set                                                                    |                     | Motor          | Active  | 41        |
| Light/Colour sensor      | White/Black | 6217705                          | Yes             | Yes                 |                | [Link](https://www.bricklink.com/v2/catalog/catalogitem.page?P=37308c01&idColor=11#T=C&C=11)          | SPIKE Prime Set, SPIKE Prime Expansion Set, Mindstorms Robot Inventor, SPIKE Essentials | 45678, 45680, 51515 | ColorSensor    | Active  | 3D        |
| Distance Sensor          | White/Black | 6302968                          | Yes             | Yes                 |                | [Link](https://www.bricklink.com/v2/catalog/catalogitem.page?P=37316c01&idColor=11#T=C&C=11)          | SPIKE Prime Set, Mindstorms Robot Inventor                                              | 45678, 51515        | DistanceSensor | Active  | 3E        |
| System medium motor      | White/Grey  | 45303, 6138854, 6290182, 6127110 | Yes             | Yes                 |                |           | Wedo 2.0, LEGO Ideas Piano, App controlled Batmobile                                    | 76112               |                | Passive | 1         |
| Force Sensor             | White/Black | 6254354                          | Yes             | Yes                 | 45606          | [Link](https://www.bricklink.com/v2/catalog/catalogitem.page?P=37312c01&idColor=11#T=C&C=11)          | SPIKE Prime Set                                                                         | 45678               | ForceSensor    | Active  | 3F        |
| 3×3 LED                 | White/Cyan  | 45608, 6297023                   | Yes             | Yes                 |                | [Link](https://www.bricklink.com/v2/catalog/catalogitem.page?P=45608c01)          | SPIKE Essentials                                                                        |                     | Matrix         | Active  | 40        |
| System train motor       | Black       | 88011                            | Yes             | Yes                 | 28740, 88011-1 | [Link](https://www.bricklink.com/v2/catalog/catalogitem.page?S=88011-1#T=S&O={%22iconly%22:0})          | Cargo Train, Disney Train and Station, Passenger Train                                  |                     |                | Passive | 2         |
| PoweredUp LED lights     | Black       | 88005                            | Yes             |                     |                | [Link](https://www.bricklink.com/v2/catalog/catalogitem.page?S=88005-1#T=S&O={%22iconly%22:0})          |                                                                                         |                     |                | Passive | 8         |
| Medium linear motor      | White/Grey  | 88008                            | Yes             | Yes                 | 26913, 88008-1 | [Link](https://www.bricklink.com/v2/catalog/catalogitem.page?S=88008-1#T=S&O={%22iconly%22:0})          | Boost, Droid Commander                                                                  |                     | Motor          | Active  | 26        |
| Technic large motor      | Grey/Grey   | 88013                            | Yes             | Yes                 | 22169          | [Link](https://www.bricklink.com/v2/catalog/catalogitem.page?S=88013-1#T=S&O={%22iconly%22:0})          |                                                                                         |                     |                | Active  | 2E        |
| Technic XL motor         | Grey/Grey   | 88014                            | Yes             | Yes                 | 22172, 88014   | [Link](https://www.bricklink.com/v2/catalog/catalogitem.page?S=88014-1#T=S&O={%22iconly%22:0})          |                                                                                         |                     |                | Active  | 2F        |
| Colour + distance sensor | White/Grey  | 88007                            | Partial         | ?                   | 26912          | [Link](https://www.bricklink.com/v2/catalog/catalogitem.page?S=88007-1#T=S&O={%22iconly%22:0})          |                                                                                         |                     |                | Active  | 25        |
| WeDo 2.0 Motion sensor   | White/Grey  | 45304, 6138855                   |                 |                     | 5003423-1      | [Link](https://www.bricklink.com/v2/catalog/catalogitem.page?S=9583-1#T=S&O={%22iconly%22:0}})          |                                                                                         |                     |                | Active  | 35        |
| WeDo 2.0 Tilt sensor     | White/Grey  | 45305, 6138856                   |                 |                     | 5003423-1      | [Link](https://www.bricklink.com/v2/catalog/catalogitem.page?S=9584-1#T=S&O={%22iconly%22:0})          |                                                                                         |                     |                | Active  | 34        |

## Mechanical Drawings

Edit this [on GitHub](https://github.com/raspberrypi/documentation/blob/develop/documentation/asciidoc/accessories/build-hat/mech.adoc)

Mechanical drawing of the Raspberry Pi Build HAT.

![mech build hat](https://www.raspberrypi.com/documentation/accessories/images/mech-build-hat.png?hash=40e1cb1b18511fffcfdcd32baf9db40f)
