CopterControl - CC3D - Atom Hardware Setup
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
which is less affected by temperature changes. This revision is called the
CC3D, and apart from the gyro sensor change is identical to the original
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

The Atom doesn't have mounting holes. Cases designed to mount and protect all of
the flight controllers are available from a number of sources. For example, for
the Atom, `http:://www.readymaderc.com`_ have lightweight cases with and
without feet.


Connection diagram
------------------

The diagram below summarizes how the overall CopterControl system is connected.

.. image:: /img/CopterControl-connections.png
   :alt: CopterControl connection diagram


Connection Details
------------------

Ports
^^^^^

CopterControl has 4 ports.

.. image:: /img/CopterControlPorts.png

* **Servo 1-6**: These are the PWM outputs that go to servos or ESCs. Power is
  typically applied through these headers from only one of the ESCs. The
  positive (Vcc) and negative (Gnd) pins are indicated on this diagram and the
  board.

  Servo output pin layout is

     * Outside --> ground
     * Middle --> 5V - 15V
     * Inside --> signal

* **MainPort (also previously known as Telemetry)**:
  :doc:`/appendices/JST-SH <jst-sh>` 4-pin. This is a serial USART whose baud
  rate can be adjusted through the GCS. Optionally Futaba S.Bus receiver,
  Spektrum/JR satellite receiver or GPS can be mapped to the MainPort. Default
  configuration is Telemetry for connecting an RF modem.

* **FlexiPort**: JST-SH 4-pin. The function of this port also depends on the
  configuration and can be configured for I2C or Serial. The default
  configuration doesn't use this port but it can be used for Telemetry, GPS,
  Spektrum satellite receivers (all working), and other I2C peripherals (under
  development).

* **Receiver Port** : JST-SH 8-pin. The receiver port can act as an input or
  output port depending on the configuration which is set in the Hardware
  Settings. Configuring the receiver port as an output port allows the user to
  assign more output channels then the 6 standard servo outputs.

ReceiverPort Options:
"""""""""""""""""""""

#. For a standard **PWM receiver**, this is where standard PWM pulses from a
   receiver are brought in. Power is supplied from the board to the receiver
   through the first 2 wires on the receiver port connection cable
   (Black-ground & Red-positive). The remaining 6 wires carry the signal for
   each channel individually & are connected to the CC ReceiverPort pins 1 - 6.
   (The channels from the receiver are thus connected to the blue, yellow,
   green, orange & purple wires.)

#. In the case of a combined **PPM receiver** signal, the same port is used.
   The PPM stream should be sent to the first input through the white wire
   connected to CC ReceiverPort pin 1. For a PPM receiver, only the CC
   ReceiverPort pin 1 is used, and the remaining wires connected to CC
   ReceiverPort pins 2-6 are unused by the receiver.

#. The port can be configured as a **PPM receiver + Outputs**: The
   ReceiverPort is used as a PPM input port like in above point 2. However, the
   4 remaining CC ReceiverPort pins 3-6 can be used as output ports. In this
   mode, the wires connected to pins 3-6 are yellow, green, orange & pink ) &
   work as output channels. If you use this mode, please be careful to unplug
   any PWM receiver first.

#. The port can be configured as an output port only: defined as **Outputs**.
   The ReceiverPort is used as an **output** port, CC ReceiverPort pins 3-6
   (yellow, green, orange & pink wires) work as **output** channels.
   ReceiverPort pins 1-2 are unused.

   - In case the CC ReceiverPort pins 3-6 are defined as output ports, they
     are available in the GCS as channels 7, 8, 9 & 10.
   - The output rate of channels 7 & 8 are bound to the same output rate of
     channel 5.
   - The output rate of channels 9 & 10 are bound to the same output rate
     of channel 6.
   - These output rates are set in the :doc:`/gcs/output`.

.. note:: Please note that the output rate on the output channels from the
   ReceiverPort cannot be set individually. If servos are connected to this
   outputs, you must ensure that they can work with the defined output rate for
   the bound channel. E.g. if you choose a high output rate to support an
   octocopter configuration, the update rate from the output channels from the
   ReceiverPort are bound to the update rate from channels 5 & 6. In this case,
   you cannot connect analog servo's to these outputs since an analog servo
   only supports an output rate of 50Hz.


Power
-----

.. warning:: **MAKE SURE YOU ARE CONNECTING POSITIVE AND NEGATIVE CORRECTLY.**

CopterControl can be powered in several ways. Via the USB port, through the
power pins on the servo headers or through the ReceiverPort connector (see the
ports section for the port location). When powered by USB, peripherals
connected (receiver, serial ports, servos) will not be powered to protect your
computer.

The minimum allowed input voltage for CopterControl is 4.8V, the maximum allowed
input voltage is +15V. CopterControl power consumption = ±70mA.

You can connect the USB and the receiver (with the power) at the same time.

.. warning:: The PWR Out pins provide unregulated voltage to the ports. If the
   CC is powered from a +15V (max. allowed) source then +15V will be on the
   PWR Out pins and can damage connected receivers, GPS, telemetry modems or
   other add-on boards.

.. note:: In case CopterControl is powered through the servo connectors, then
   only connect the power from one ESC and remove the positive and negative wire
   from the other ESC's. Connecting multiple voltage regulators (built in to
   the ESC's) in parallel could cause problems. Connecting multiple black ground
   wires could cause ground loops which we want to avoid.

These photos show how to remove and insulate the positive wire from the ESC.
Remove the positive & negative wire leaving only the signal cable connected for
all but one of your ESC's. A small flat blade screwdriver (or X-Acto knife
could be used) and 2mm heat shrink tube was used in this example. This
modification can easily be reversed by removing the heat shrink and inserting
the positive wire back in to the ESC plug. Also, remove the ground wire when
removing the hot and insulate separately from the hot wire.


.. image:: /img/Remove-pos1.png
   :height: 224

.. image:: /img/Remove-pos2.png
   :height: 224

.. image:: /img/Remove-pos3.png
   :height: 224

.. note:: In some rare cases or on high-end ESCs the ESC doesn't perform
   correctly without connecting the additional ground signal. In those cases it
   may be necessary to connect the ground wire to the ESC.


Cables, colors & pin-outs
-------------------------

CopterControl uses the :doc:`JST-SH <jst-sh>` series headers. A CopterControl
board comes standard with one 8-pin connection cable as shown below to connect
your receiver. Additionally, one 4-pin JST-SH cable is supplied to connect to
the MainPort or FlexiPort. You can easily cut the 4-pins cable and use it to
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

MainPort and FlexiPort
^^^^^^^^^^^^^^^^^^^^^^

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

.. warning:: The Spektrum adapter should only be powered by 3.3V, a step down
   adapter must be used.

.. warning:: The PWR Out voltage is dependent on the CC supplied voltage.
   Verify that you use the correct voltage for your S.BUS receiver.

Receiver PWM connection
^^^^^^^^^^^^^^^^^^^^^^^

There are several ways to connect your receiver to CopterControl. You can
connect any plug from the CopterControl receiver cable to any channel of your
receiver. The correct channel mapping is done in the GCS :doc:`/sw/user/input`.
However as a guideline for a standard PWM receiver, you may want to connect it
as follows:

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
* Supports several common RC inputs: 6 PWM channels, combined PPM, Spektrum/JR
  DSM2, DSMJ, DSMX satellites, and Futaba S.Bus receivers
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



Technical description
---------------------

Dimensions
^^^^^^^^^^

CopterControl & CC3D used the standard OpenPilot footprint, and hence has the
same dimensions and mounting holes as the OpenPilot Revo, GPS, OSD and PipX
boards.

.. image:: /img/ccmeasurements.png


.. _cc_hw_ports:


.. rubric:: Footnotes

.. [#f1] On CC3D the IDG-500, ISZ-500 and ADXL345 is replaced by the MPU6000.
  
