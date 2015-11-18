OPLM CC - CC3D - Atom Hardware Setup
------------------------------------

Summary
^^^^^^^

This page will walk you through how to set up the hardware connections that are
required for CopterControl, CC3D and Atom OPLink operation. All OpenPilot
boards support connection with the OPLink module. The OPLink connection can be
used for telemetry and/or vehicle control.

The OPLink module will get it's power from the flight controller's external
power, so unlike Revolution, the modem will not get powered on by just
plugging in the USB to the flight controller. Make sure that you have the same
OpenPilot firmware versions on both the flight controller and OPLink modem. All
the examples below are shown with a CC3D flight controller board, but they can
be applied to CopterControl and Atom, also.

Hardware connections
^^^^^^^^^^^^^^^^^^^^

Telemetry only
""""""""""""""

The OPLink will be set up to talk bidirectional telemetry with the flight
controller. You can use a regular OpenPilot 4-pin JST SH cable to connect the
two boards. It is recommended to use Main port for both boards, but you can
also use other ports to connect telemetry. Just remember the changes in the
Configuration steps below. Connect the boards like in the diagram:

.. image:: img/CC-OPLM-Telemetry.png
   :width: 600

Telemetry and vehicle control
"""""""""""""""""""""""""""""

If you also want to use OPLink modem for :doc:`vehicle control <control>`,
you'll need to add one additional wire from the TX pin of the OPLink to the PPM
input pin on the flight controller. In this diagram the wire goes to PIN 8 on
the controller, because that is the pin that allows OneShot125 and PWM Sync with
CC3D. Revolution PPM remains on PIN 3.

.. image:: img/CC-OPLM-Telemetry+PPM.png
   :width: 600

Configuration
^^^^^^^^^^^^^

Change the flight controller and OPLink Mini configuration to reflect the
wiring changes that have been made. This is where it all becomes pretty
rational. After these configuration steps, you are ready to proceed with
:doc:`binding`.

Flight-side OPLink modem configuration
""""""""""""""""""""""""""""""""""""""

* Connect to the OPLink mini modem with USB.
* From the Configuration tab, Navigate to the **OPLink page** in the GCS.
* From the **Main Port** drop down menu, select **Telemetry**.
* Click **Save**, wait a few seconds for the telemetry gadget (the meter at the
  bottom of the GCS) to calm down, and disconnect from the modem.

.. image:: img/oplm_cc_flight.png
   :width: 500

Flight controller configuration
"""""""""""""""""""""""""""""""

* Connect to the flight controller with USB.
* From the Configuration tab, navigate to the **Hardware page** in the GCS.
* From the **Main Port** drop down menu, select **Telemetry**
* From the **Telemetry Speed** drop down menu, select **38400**
* Click **Save**, wait a few seconds for the telemetry gadget (the meter at the
  bottom of the GCS) to calm down, and then disconnect from the flight
  controller.


