Overview
--------

.. image:: /img/oplink_mini.png

The OPLink is a radio transceiver backed by an ARM32 powered digital packet
processor specifically designed for the OpenPilot project, it was originally
developed under the codename: PipXtreme and there are many artifacts that still
reflect this. It is a two-way radio system allowing real time telemetry
information for the Ground Control Station, Wireless Configuration and even
:doc:`radio control <control>` from your transmitter over a single
communications link.

You will need two OPLink radios to establish a connection between the vehicle
and ground station. Note that the Revolution board has an OPLink built into
the flight controller. The same firmware version must be running in Revo and
OPLM devices *(i.e. if you upgrade one board, you will need to upgrade all*
*others that are 'bound' together)*.

The OPLM units operate at 433Mhz. This means that there will be a **frequency**
**conflict** if you operate the vehicle using a UHF 433Mhz system. In basic
terms, this conflict will lead to a loss of vehicle control and / or a crash.
Use transmitters in other parts of the spectrum *(i.e. 2.4G, 27Mhz, 36Mhz)* for
vehicle control if you intend to enable the OPLink on your Revo for transmission
of telemetry data. If you wish to use a 433Mhz transmitter for vehicle control,
then use an OPLM which will by default, enable the transmission of telemetry.

Check local laws and regulations regarding radio licensing, see our
:doc:`license` article for more information.

The device that is intended to undertake the most of the transmissions should
be allocated as the Co-ordinator. If you wish to use the OPLM for vehicle
control, then the Co-ordinator should be the OPLM device in your transmitter
module at the ground station. In this case, the Revo or another OPLink will be
acting as a slave receiver but will also transmit telemetry information to your
ground station which is comprised of another OPLM connected to a computer that
is running the OP GCS Flight Data page. Alternatively, if you wish to simply
receive telemetry data at the ground station, then the Revo should be configured
as the Co-ordinator. Configuration instructions are provided below and linked-to
pages.

First time use with OPLM
^^^^^^^^^^^^^^^^^^^^^^^^

When you first try to use your OPLM with the GCS, it will not be automatically
picked up by the GCS. You first need to go into the 'Firmware' tab and click
'Upgrade & Erase' while the OPLink is **disconnected**. Then plug in OPLink
when the upgrade process asks for it. Once this has been done, your OPLM board
will show up at the bottom of your GCS as a connected device.
**The configuration page icon at the bottom of the page icon list may be**
**hidden without scrolling down, depending on the size of your computer**
**screen.**

OPLink Mini
"""""""""""

* 100mW Standalone Radio Modem
* 3 IO Ports: Micro-B USB, Mainport & Flexiport
* MMCX Antenna Connector.
* Weight: 4g
* Dimensions: 20mm x 29mm
* Input Voltage: +5v

OPLink Revo
"""""""""""

* 100mW integrated radio modem included the OpenPilot Revolution platform.
* MMCX Antenna Connector.
* Directly integrated, no external connections or power needed.
* Dipole whip antenna

- :doc:`cc`
- :doc:`binding`
- :doc:`control`

Serial Bluetooth RF Transceiver Module RS232
--------------------------------------------

.. image:: /img/Bluetooth.jpg

This small size Bluetooth TTL transceiver module allows your target device to
both send or receive the TTL data via Bluetooth technology without connecting a
serial cable to your computer. It's easy to use and completely encapsulated.
It can be used to establish a short telemetry link directly to the vehicle,
or a telemetry link between a computer and a transmitter, that has an OPLink
module connected to it.

* Chipset CSR BC417143
* Bluetooth version V2.0+EDR (Enhanced Data Rate)
* Output power Class II (±2.5mW range ±10m)
* Flash 8Mbit
* Power Supply 3.3V (5VDC via breakout board)
* Interface UART

This configuration guide covers the displayed serial Bluetooth module. It's
available in many different internet shops (e.g. Ebay, Goodluckbuy, BlueSkyRC).
The boards generally ship for around 10$ - 20$. Although the hardware is the
same, several software or firmware revisions exist.

Different input voltage versions

.. important:: There are different versions available; 3VDC or 5VDC. You want
   the 5VDC version in order to connect directly to CopterControl. This module
   has an on-board voltage regulator.

The voltage input must be clearly mentioned. Typically, these boards can handle
a power supply between 3.6VDC ~ 6.0VDC when an on-board voltage regulator is
available.

Check for the input & output voltage which is mostly mentioned on the module
diagram.

- :doc:`bluetooth`
