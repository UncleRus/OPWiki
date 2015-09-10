OPLM Vehicle Control Link
-------------------------

Summary
^^^^^^^

These instructions will walk you through on how to use your existing OPLink
telemetry connection for vehicle control. The instructions consist of hardware
and software side. Set up the hardware side first and then do the necessary
hardware configuration changes. If you have not done binding yet for the
OPLink modules, do that first using :doc:`binding` page instructions, and
return to this tutorial after that.

For Revolution, no hardware configuration is required at the flight controller
side. For CC, CC3D and Atom, a PPM wire has to be connected from the OPLink
module to the flight controller. The instructions for how to prepare those
flight controllers for control link can be found on :doc:`cc` page. If you do
not have the PPM wire connected, do it now, and then return to this page.

OPLink wiring
^^^^^^^^^^^^^

You will need to supply power and control data from the transmitter to the
OPLink module. The OPLink Mini module requires three wires for normal operation
with a transmitter.

.. image:: /img/oplm_control.jpg
   :width: 500

* Ground
* Voltage (recommended 5V - 8.4V)
* PPM Out from the transmitter

The voltage wire, Vcc in the picture, is a bit tricky. A regular transmitter
usually uses 3S LiPo for power and it outputs that 3S voltage to the trainer
port and radio module connections. That voltage is too high to be directly
used. You should use a linear regulator or UBEC to bring the voltage down to
5 volts.

The PPM wire can be directly connected and does not need anything in between
the OPLink module and transmitter. You can cut a regular OpenPilot 4-pin serial
cable in half and use that to connect the wires to your OPLink module. The blue
wire in the 4-pin cable is not used for this application, so you can remove it.

.. rubric:: OPLink PPM input

OPLink module is programmed to accept PPM sum between 4 and 8 channels.
Recommended PPM frame length is 22,5 milliseconds.

.. rubric:: OPLink input voltage

Do not input higher than 8.4 volts (2S) to the OPLink module! Higher voltage
will cause permanent damage to the electronics.

Pinouts for connecting OPLink to the transmitter
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Here are two pinout diagrams that might help to connect the OPLink module
to your transmitter. The JR type module bay outputs PPM, which can be
connected directly to your OPLink module. A 5V UBEC is needed between +BAT and
GND. You can connect the UBEC output to OPLink Vcc and GND. The +6V wire can be
used to power the OPLink directly if your radio has it, but most radios don't.

The Futaba and Hitec trainer ports have similar pins that you can use, called
GROUND, PPMout and Vbattery in the diagram. A nice trick is to cut a trainer
cable in half and use that to make a neat connection to the transmitter. If you
cut a trainer cable, you'll have to identify the correct wires with a
multimeter.

.. image:: /img/oplm_tx_pinout.jpg
   :width: 500

Mounting the OPLink module to the transmitter
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. image:: /img/oplm_tx.jpg
   :width: 500

There are many ways to attach the OPLink mini module to your transmitter. The
options listed here are just ideas and possible inspiration for the job.

- You can install the OPLink module inside an existing JR or Futaba transmitter
  case
- 3D print a JR module: `<http://www.thingiverse.com/thing:585245>`_
- Heat shrink the module and attach it to the transmitter with velcro
- Install the OPLink and UBEC inside the module bay without a case
- Invent a new method and contact a forum moderator to add your idea here!


