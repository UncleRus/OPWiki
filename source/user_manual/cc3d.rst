CopterControl / CC3D / Atom Hardware Setup
==========================================

CopterControl3D (CC3D and Atom) and CopterControl Introduction
--------------------------------------------------------------

The CopterControl, CC3D and Atom flight controllers are all types of
stabilisation hardware which run the OpenPilot firmware. They can be configured
to fly any airframe from fixed wing to an octocopter using the OpenPilot Ground
Control Station (GCS) software. If you haven't already installed the Ground
Control software, see :doc:`gcs_install`.

The CopterControl was the first generation board, which ceased manufacture in
2012 due to lack of availability of the gyro sensors used for stabilisation.
The board design was then revised and released with an improved gyro sensor
which is less affected by temperature changes. This revision is called the CC3D,
and apart from the gyro sensor change is identical to the original
CopterControl. The Atom is the latest edition to this family - it has the full
functionality of the CC3D, but in a smaller form factor and was made available
in August 2014 by getfvp.com and readymaderc.com.

All three of these boards are 100% compatible with the latest firmware release
when updated to the latest boot-loader. All documentation referring to the
original CopterControl board is applicable to both the CC3D and Atom boards.

Getting to know your board
--------------------------

CopterControl
^^^^^^^^^^^^^

.. image:: /img/CC-top-300.png
   :alt: CopterControl top side

.. image:: /img/CC-bottom-300.png
   :alt: CopterControl bottom side

Weight: 8g

CopterControl3D/CC3D
^^^^^^^^^^^^^^^^^^^^

.. image:: /img/CC3D-top-300.png
   :alt: CC3D Top

.. image:: /img/CC3D-bottom-300.png
   :alt: CC3D Bottom

Weight: 8g

The CC3D and the Atom are both available with right angle or straight output
connectors.

ATOM
^^^^

.. image:: /img/Atom-top-300.png
   :alt: ATOM Top

.. image:: /img/Atom-bottom-300.png
   :alt: ATOM Bottom

Weight: 4g

The Atom doesn't have mounting holes. Cases designed to mount and protect all
of the flight controllers are available from a number of sources. For example,
for the Atom, www.readymaderc.com have lightweight cases with and without feet.


Connection diagram
------------------

The diagram below summarizes how the overall CopterControl system is connected.

.. image:: /img/CopterControl-connections.png
   :alt: CopterControl connection diagram


Connection Details
------------------

Ports
^^^^^

CopterControl / CC3D / Atom have 4 ports.

.. image:: /img/CopterControlPorts.png

.. image:: /img/Atom-ports.png

* **Servo Output 1-6**: These are the PWM outputs that go to servos or ESCs.
  Power is typically applied through these headers from only one of the ESCs.
  The positive (Vcc) and negative (Gnd) pins are indicated on this diagram and
  the board.

  Servo output pin layout is
     * Outside --> ground
     * Middle --> 5V - 15V
     * Inside --> signal

* **MainPort (also previously known as Telemetry)**:
  :doc:`JST-SH </appendices/jst-sh>` 4-pin. This is a serial USART whose baud
  rate can be adjusted through the GCS. Optionally Futaba S.Bus receiver,
  Spektrum/JR satellite receiver or GPS can be mapped to the MainPort. Default
  configuration is Telemetry for connecting an RF modem.

* **FlexiPort**: JST-SH 4-pin. The function of this port also depends on the
  configuration and can be configured for I2C or Serial. The default
  configuration doesn't use this port but it can be used for Telemetry, GPS,
  Spektrum satellite receivers (all working), and other I2C peripherals
  (under development).

* **ReceiverPort** : JST-SH 8-pin. The receiver port can act as an input or
  output port depending on the configuration which is set in the Hardware
  Settings. Configuring the receiver port as an output port allows the user
  to assign more output channels then the 6 standard servo outputs.

  ReceiverPort use depends on the type of RC receiver in use, and whether
  OneShot125 or PWM Sync output is desired:

  - **PWM**

    - **PWM+NoOneShot** should be used with a normal PWM type receiver.
      The 6 rightmost wires of the receiver port carry the signal for each
      channel individually.

  - **PPM - Pin 3**

    - **PPM+NoOneShot** is used with modern PPM type receivers, that combine the
      control signal to one wire. The PPM stream should be sent to the first
      input through the white wire connected to CC ReceiverPort wire/pin 3. For
      a PPM receiver, only one pin is used for signal - the remaining wires
      connected to CC ReceiverPort wires 4-8 are left unused.
    - **PPM+PWM+NoOneShot** combines the two modes above, wire/pin 3 is used for
      PPM and the rest, wires/pins 4-8 are used as PWM inputs.
    - **PPM+Outputs+NoOneShot** enables PPM input in ReceiverPort wire/pin 3,
      and PWM output in wires/pins 5-8. These work as output channels 7-10.

  - **PPM - Pin 8**

    - **PPM_PIN8+OneShot** is a new mode, where PPM input wire
      is moved from previous ReceiverPort pin 3 to pin 8 to allow PWM Sync and
      OneShot125 to be used as ESC output modes.

  - **RECEIVER PORT AS OUTPUTS**

    - **Outputs+OneShot** makes ReceiverPort pins 5-8 work as output channels
      7-10. ReceiverPort pins 3 and 4 are unused. This and the Disabled option
      can be used if the control communication is via a spektrum satellite
      receiver or directly through telemetry.

  - **DISABLING**

    - **Disabled+OneShot** basically disables the ReceiverPort.

  **Default settings**

  By default, the Vehicle Setup Wizard will set receiver port as
  PPM_PIN8+OneShot when PPM type receiver is selected.

.. note:: Please note that the output rate on the output channels from the
   ReceiverPort cannot be set individually. If servos are connected to this
   outputs, you must ensure that they can work with the defined output rate
   for the bound channel. E.g. if you choose a high output rate to support an
   octocopter configuration, the update rate from the output channels from the
   ReceiverPort are bound to the update rate from channels 5 & 6. In this case,
   you cannot connect analogue servo's to these outputs since an analogue servo
   only supports an output rate of 50Hz. The output rates are set in GCS
   Outputs page.
  
Power
-----

.. warning:: **MAKE SURE YOU ARE CONNECTING POSITIVE AND NEGATIVE CORRECTLY.**

* CopterControl can be powered in several ways. Via the USB port, through the
  power pins on the servo headers or through the ReceiverPort connector (see
  the ports section for the port location). When powered by USB, peripherals
  connected (receiver, serial ports, servos, ESCs) will not be powered to
  protect your computer from too much current draw through the USB.
* The minimum allowed input voltage for CopterControl is 4.8V, the maximum
  allowed input voltage is +15V.
* Power consumption = ±70mA.
* You can connect the USB and the receiver (with the power) at the same time.

.. caution:: The PWR Out pins provide unregulated voltage to the ports. If the
   CC is powered from a +15V (max. allowed) source then +15V will be on the
   PWR Out pins and can damage connected receivers, GPS, telemetry modems or
   other add-on boards.

If you power the flight controller through the servo connectors (utilising the
BEC function of the speed controller), the positive power lead from only one
ESC is truly necessary. In most cases, all the wires can be left intact and
plugged into the board without any problem. If you experience problems with
setup or know for a fact that your particular ESC model requires it, you may
remove the positive and negative pins from all but one of the ESC servo
connectors. In some ESCs (very few, actually), connecting multiple voltage
regulators (built in to the ESC's) in parallel could cause problems. Also,
in rare cases, connecting multiple ground wires could cause ground loops
so remove the extra ground pins only if experiencing weird problems.

These photos show how to remove and insulate the positive wire from the ESC.
Remove the positive & negative wire leaving only the signal cable connected for
all but one of your ESC's. A small flat blade screwdriver (or X-Acto knife could
be used) and 2mm heat shrink tube was used in this example. This modification
can easily be reversed by removing the heat shrink and inserting the positive
wire back in to the ESC plug. Also, remove the ground wire when removing the
hot and insulate separately from the hot wire.


.. image:: /img/Remove-pos1.png
   :height: 224

.. image:: /img/Remove-pos2.png
   :height: 224

.. image:: /img/Remove-pos3.png
   :height: 224


Cables, colors & pin-outs
-------------------------

CopterControl uses the :doc:`JST-SH </appendices/jst-sh>` series headers. A
CopterControl board comes standard with one 8-pin connection cable as shown
below to connect your receiver. Additionally, one 4-pin JST-SH cable is supplied
to connect to the MainPort or FlexiPort. You can easily cut the 4-pins cable and
connect your telemetry or Spektrum satellite.

.. image:: /img/ReceiverCable.jpg
   :width: 400

ReceiverPort
^^^^^^^^^^^^

+--------+--------------------------+------------+-----------------------+
| Color  | Function                 | JST-SH Pin | Servo connector plug, |
|        |                          |            | ReceiverPort pin      |
+========+==========================+============+=======================+
| Black  | Ground                   | 1          | 1                     |
+--------+--------------------------+------------+-----------------------+
| Red    | Power to RC RX (VCC      | 2          | 1                     |
|        | Unregulated) 4.8V - 15V  |            |                       |
+--------+--------------------------+------------+-----------------------+
| White  | PWM Signal 1 or combined | 3          | 1                     |
|        | PPM                      |            |                       |
+--------+--------------------------+------------+-----------------------+
| Blue   | PWM Signal 2             | 4          | 2                     |
+--------+--------------------------+------------+-----------------------+
| Yellow | PWM Signal 3 or PWM      | 5          | 3                     |
|        | Output channel 7         |            |                       |
+--------+--------------------------+------------+-----------------------+
| Green  | PWM Signal 4 or PWM      | 6          | 4                     |
|        | Output channel 8         |            |                       |
+--------+--------------------------+------------+-----------------------+
| Orange | PWM Signal 5 or PWM      | 7          | 5                     |
|        | Output channel 9         |            |                       |
+--------+--------------------------+------------+-----------------------+
| Purple | PWM Signal 6 or PWM      | 8          | 6                     |
|        | Output channel 10        |            |                       |
+--------+--------------------------+------------+-----------------------+

.. image:: /img/JSH-SH-8pin.png

MainPort and FlexiPort serial cable pinout
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

+--------+--------+---------------+--------------+--------------+--------------+--------------+
| Color  | JST-SH | Voltage       | Serial       | I2C          | Spektrum     | S.Bus        |
|        | Pin    |               | Function     | Function     |              |              |
+========+========+===============+==============+==============+==============+==============+
| Black  | 1      | GND           | GND          | GND          | GND          | GND          |
+--------+--------+---------------+--------------+--------------+--------------+--------------+
| Red    | 2      | 4.8V -        | PWR          | PWR          | PWR          | PWR          |
|        |        | 15V           | Out (VCC     | Out (VCC     | Out (VCC     | Out (VCC     |
|        |        |               | Unregulated) | Unregulated) | Unregulated) | Unregulated) |
+--------+--------+---------------+--------------+--------------+--------------+--------------+
| Blue   | 3      | 3.3V          | TX           | SCL          |              |              |
+--------+--------+---------------+--------------+--------------+--------------+--------------+
| Orange | 4      | 3.3V          | RX           | SDA          | TX           | TX           |
|        |        | (5V Tolerant) |              |              | (Signal)     | (Signal)     |
+--------+--------+---------------+--------------+--------------+--------------+--------------+

.. image:: /img/JSH-SH-4pin.png

.. caution:: The Spektrum adapter should only be powered by 3.3V, a step down
   adapter must be used.

.. caution:: The PWR Out voltage is dependent on the CC supplied voltage.
   Verify that you use the correct voltage for your S.BUS receiver.

Receiver PWM connection
^^^^^^^^^^^^^^^^^^^^^^^

There are several ways to connect your receiver to CopterControl. You can
connect any plug from the CopterControl receiver cable to any channel of your
receiver. The correct channel mapping is done in the GCS `<https://librepilot.atlassian.net/wiki/display/LPDOC/Input+Configuration>`_.
However as a guideline for a standard PWM receiver, you may want to connect
it as follows:

.. rubric:: For Futaba and Hitec

+-----------+--------------------+--------+----------+
| Channel 1 | AILERON or ROLL    | White  | Signal 1 |
+-----------+--------------------+--------+----------+
| Channel 2 | ELEV or PITCH      | Blue   | Signal 2 |
+-----------+--------------------+--------+----------+
| Channel 3 | THROTTLE           | Yellow | Signal 3 |
+-----------+--------------------+--------+----------+
| Channel 4 | RUDDER             | Green  | Signal 4 |
+-----------+--------------------+--------+----------+
| Channel 5 | GEAR - Flight mode | Orange | Signal 5 |
+-----------+--------------------+--------+----------+
| Channel 6 | AUX1               | Purple | Signal 6 |
+-----------+--------------------+--------+----------+

.. rubric:: For JR and Spektrum

+-----------+--------------------+--------+----------+
| Channel 1 | THROTTLE           | White  | Signal 1 |
+-----------+--------------------+--------+----------+
| Channel 2 | AILERON or ROLL    | Blue   | Signal 2 |
+-----------+--------------------+--------+----------+
| Channel 3 | ELEV or PITCH      | Yellow | Signal 3 |
+-----------+--------------------+--------+----------+
| Channel 4 | RUDDER             | Green  | Signal 4 |
+-----------+--------------------+--------+----------+
| Channel 5 | GEAR - Flight mode | Orange | Signal 5 |
+-----------+--------------------+--------+----------+
| Channel 6 | AUX1               | Purple | Signal 6 |
+-----------+--------------------+--------+----------+

.. note:: If you are unsure about the type of your receiver (PPM, PWM, 
   Spektrum Satellite...) or where to connect it, please refer to this
   page where the different options are explained.

Sensors and Components
----------------------

* 3-axis Gyroscope array: IDG-500 and ISZ-500 [#f1]_
* 3-axis Accelerometer: ADXL345 [#f1]_
* Supports several common RC inputs: 6 PWM channels, combined PPM,
  Spektrum/JR DSM2, DSMJ, DSMX satellites, and Futaba S.Bus receivers
* Simultaneous support for multiple receivers
* ReceiverPort functions (configurable): 6 PWM input channels or combined PPM
  stream, 4 PWM output channels
* MainPort functions (configurable): serial telemetry (default), GPS, S.Bus,
  Spektrum/JR satellites
* FlexiPort (configurable): serial telemetry, GPS, Spektrum/JR satellites, or
  I2C peripherals (under development)
* 10 PWM outputs to servos or ESC's, or for camera stabilization
* Camera stabilization: supports up to 3-axis camera mounts with stabilization
  and manual control from any of configured receivers
* Onboard USB connectivity for easy configuration
* USB and serial telemetry and configuration (including wireless with optional
  radio modules)
* Supported by powerful OpenPilot GCS
* 4 Mbit onboard memory
* 3C Quaternion based complementary filter running at 500Hz


.. [#f1] On CC3D the IDG-500, ISZ-500 and ADXL345 is replaced by the MPU6000.


DIY Boards
----------

Schematics, PCB Layout, Gerbers, BOM for **CopterControl**:
:download:`CopterControl.zip </files/hw/CopterControl.zip>`

Schematics, PCB Layout, Gerbers, BOM for **CopterControl 3D**:
:download:`CopterControl 3D.zip </files/hw/CopterControl 3D.zip>`

Schematics, PCB Layout, Gerbers, BOM for **Atom**:
:download:`Atom.zip </files/hw/Atom.zip>`


Other Information
-----------------

Dimensions
^^^^^^^^^^

CopterControl & CC3D used the standard OpenPilot footprint, and hence has the
same dimensions and mounting holes as the OpenPilot Revo, GPS, OSD and PipX
boards.

.. image:: /img/ccmeasurements.png

