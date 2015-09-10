OpenPilot Cables
================

The OpenPilot hardware comes with the necessary connection cables (other
than S.Bus).

.. note:: The CopterControl or CopterControl3D boards are shipped with one
   ReceiverPort cable and one Serial cable. The Revo board is shipped with
   a 10 pin ReceiverPort cable (note 2 cables empty at this stage).

The interface cables needed for OpenPilot boards are:

* **ReceiverPort cable for CC/CC3D and Atom boards**. JST-SH8.
  The ReceiverPort cable is used to hook up the receiver or servos to the
  CopterControl board depending on the configuration.

.. image:: /img/ReceiverCable.jpg
   :width: 400
   :align: center

* **The ReceiverPort cable for the Revo board**. JST-SH10.
* **Serial cable**. JST-SH4. The serial cable plugs into the FlexiPort
  or Mainport of OP boards and allows the user to connect telemetry
  modems, GPS devices, etc.
* **S.Bus cable**. For connecting a S.Bus receiver to an OpenPilot board.
  You need to make this cable yourself. Cut an OpenPilot serial cable in half.
  Remove a lead by carefully lifting plastic retaining pins in the connector.
  Solder and insulate the serial cable to a three strand servo cable.
  Ensure correct polarity - you will need to shift a lead in one end of the
  serial cable.  And once the cable is complete, you will need to change
  the configuration setting to <S.Bus> on the MainPort on the Hardware page
  of the GCS.

See the :ref:`cc_hw_ports` section in the CopterControl hardware overview
for a complete description. The cables are equipped with a JST-SH connector
which is plugged into the OpenPilot hardware.

Availability
------------

Cables and connectors are included with the OpenPilot boards. If more
connectors are needed, the JST-SH connectors together with suitable cables
will be available within the OpenPilot stores. Other sources may include
larger electronic stores.

.. note:: The JST-SR plug is compatible with the JST-SH socket - the
   difference being that the SH is a crimp type and the SR is an IDC type.
   Some commercially offered cables may use SR type plugs (which do look
   a little different) but they should fit.

Some examples below. Other cheaper or better sources may exist.

* OpenPilot Stores
* OpenPilot CopterControl cables from www.rc-connectors.com
* One tested example of these can be found on Ebay: Micro Mini JST Connector 1.0mm spacing 4-Pin
  They have the following mentioned dimensions:
  [JSTConnectorDim.png]
* Sparkfun (4-pin, and 8-pin)  -- (Note from James : I ordered some of these but
  they had a larger connector.  YMMV)
* Crimp Pliers for JST-SH crimps - CoolComponents (UK) or Sparkfun

Various sources can also be found on Ebay but the name JST-SH seldom used,
instead JST "micro" or other names can be present which makes it hard to
verify if it's the right type of JST connector.

.. todo:: Find pictures, insert links
