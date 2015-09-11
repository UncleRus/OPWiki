Bootloader Update
=================

Introduction
------------

The bootloader is a small piece of software resident on the flight controller
which is started as soon as the board is powered. It performs hardware checks
and loads and executes the firmware. It also handles the USB port to
communicate with GCS to support bootloader and firmware updates.

You can check the version of the bootloader installed on any OP board to make
sure it is the most up-to-date version and upgrade the bootloader software if
required.

.. warning:: Upgrading the bootloader can be tricky. If something goes wrong, 
   you may render the flight controller inoperable. Happily, almost all bad 
   mistakes can be rectified via the methods described on the "How to"
   sub-pages to this one.
   

How to Check the Bootloader Version
-----------------------------------

The bootloader version is shown when the flight controller is in boot mode. You
can enter boot mode by:

* using either the **Halt** option or,
* by using **Rescue**.

Either method will reveal the bootloader version on your board and both methods
are explained below.

Halt Option
^^^^^^^^^^^

Connect the flight controller to GCS via USB and open the Firmware page.
On the Firmware page, click **Halt**.

.. image:: /img/bootloader_halt.png

Once the board is halted, the bootloader (BL) version of the board is shown.

.. image:: /img/bootloader_halted.png

Click **Boot** to restart the flight controller once you have noted the
bootloader version.

Rescue Method
^^^^^^^^^^^^^

Ensure that the flight controller is **not** connected to GCS via USB.
Click **Rescue** and connect the flight controller via USB when prompted.

.. image:: /img/bootloader_rescue.png

When the board is connected, its bootloader (BL) version is shown.
Click **Boot** to restart the flight controller once you have noted the
bootloader version.

OpenPilot Downloads
-------------------

Bootloader Versions
^^^^^^^^^^^^^^^^^^^

* **Version 1** - First bootloader version which was loaded onto all
  CopterControl boards.
* **Version 2** - Safe boot capabilities were added to prevent the user from
  being locked out of the board due to a bad hardware configuration.
* **Version 3** - Added different USB serial numbers for bootloader and
  firmware. This helps Windows separate the two functions of the board by
  making it think there are two different boards connected. Twitching servo
  movement during the board start has been eliminated.
* **Version 4** - Added support for internal settings erasure so that no more
  special firmware is required; simply enter boot mode and click Erase Settings
  (CC/CC3D/Atom and OPLM)
* **Version 5** - Added better F4 processor support (Revo and OSD)

The bootloaders for CopterControl (CC), CopterControl3D (CC3D), Atom, Revolution
(Revo), OPLink mini (OPLM) and On Screen Display (OSD) are available for
download below.

.. caution:: All OP boards are different and require the appropriate bootloader
   to be installed, please ensure you download and use the correct version
   listed below.

Also note that you should have the appropriate GCS installed (in most cases,
the latest version) on your PC when you flash the new bootloader so that the
followup Auto Update you perform will automatically install the correct version
of firmware that is embedded in the version of the GCS on your PC.

The PCB for CC or CC3D boards should have "CopterControl" or "CC3D" printed
clearly on the board. This indicates which bootloader needs to be flashed to
the board.

Version 3 bootloaders can only be used with GCS versions 12.10.2 or older.
Version 4 bootloaders can only be used with GCS versions 13.06.01 and newer.

.. rubric:: Bootloader Updater Files

+-----------+---------+------------------------------------------------------------------------------------------------------------------+---------------------+
| Board     | BL      | Updater                                                                                                          | Note                |
|           | Version | Bootloader                                                                                                       |                     |
+===========+=========+==================================================================================================================+=====================+
| CC        | 3       | :download:`bu_coptercontrol-20120630_5a1efef3.opfw </files/bootloaders/bu_coptercontrol-20120630_5a1efef3.opfw>` | For use with GCS    |
|           |         |                                                                                                                  | 12.10.2 and lower   |
+-----------+---------+------------------------------------------------------------------------------------------------------------------+---------------------+
| CC3D      | 3       | :download:`bu_CC3D-20120620_f44b9d3.opfw </files/bootloaders/bu_CC3D-20120620_f44b9d3.opfw>`                     | For use with GCS    |
|           |         |                                                                                                                  | 12.10.2 and lower   |
+-----------+---------+------------------------------------------------------------------------------------------------------------------+---------------------+
| CC        | 4       | CC V4                                                                                                            | For use with GCS    |
|           |         | :download:`bu_cc.opfw </files/bootloaders/bu_cc.opfw>`                                                           | 13.06.01 and higher |
+-----------+---------+------------------------------------------------------------------------------------------------------------------+---------------------+
| CC3D/Atom | 4       | CC3D V4                                                                                                          | For use with GCS    |
|           |         | :download:`bu_cc3d.opfw </files/bootloaders/bu_cc3d.opfw>`                                                       | 13.06.01 and higher |
+-----------+---------+------------------------------------------------------------------------------------------------------------------+---------------------+
| Revo      | 5       | Revo V5                                                                                                          | For use with GCS    |
|           |         | :download:`bu_revolution.opfw </files/bootloaders/bu_revolution.opfw>`                                           | 13.06.01 and higher |
+-----------+---------+------------------------------------------------------------------------------------------------------------------+---------------------+
| OPLMini   | 4       | OPLM                                                                                                             | For use with GCS    |
|           |         | :download:`bu_oplinkmini.opfw </files/bootloaders/bu_oplinkmini.opfw>`                                           | 13.06.01 and higher |
+-----------+---------+------------------------------------------------------------------------------------------------------------------+---------------------+
| OSD       | 5       | OSD bu_osd.opfw                                                                                                  | For use with GCS    |
|           |         | :download:`bu_osd.opfw </files/bootloaders/bu_osd.opfw>`                                                         | 13.06.01 and higher |
+-----------+---------+------------------------------------------------------------------------------------------------------------------+---------------------+


How to Upgrade the Bootloader and Erase Settings
------------------------------------------------

If it is necessary to upload the bootloader, **strictly** follow these
instructions:

* Download the appropriate bootloader (ie CC3D - BL4 or Revo - BL5) and save it
  to your hard drive where you can find it again
* Using the **Firmware** workspace in GCS, and with the board disconnected from
  USB, click **Rescue** and follow the onscreen instruction to connect the board
* After the board is detected, click **Open** and select the BootloaderUpdater
  (BU) file from where you saved it on your hard drive
* Click **Flash** to flash it to your board
* After the flashing is complete, press **Boot** and wait until the blue LED is
  on, then flashes, and finally goes off (normally ±15 seconds).
* Wait 10 seconds more.
* Disconnect the board from USB.
* Click **Rescue**, connect the board, click **Erase Settings** and wait for the
  erasure to complete.
* Disconnect the board from USB.
* Click **Upgrade** and follow the onscreen instruction to connect the board to
  automatically install firmware.


LED Behavior
------------

* A slowly blinking blue LED indicates that the board is booted and running the
  firmware; this is the normal operating mode.
* Bootloader mode. A slow fading in and out of the blue LED with the green LED
  on indicates that the board is in bootloader mode.
* A rapidly blinking blue LED during a bootloader update indicates an error
  state. An invalid bootloader image was likely detected and the update
  hasn't been performed.

FAQs
----

.. rubric:: What's the difference between firmware, bootloader (BL) and
   bootloader updater (BU)?

The **firmware (FW)** is the application to be loaded by the bootloader after
the board has been powered up and initialized. The firmware is regularly updated
and newer firmwares typically include new features and bug fixes. The firmware
and GCS version must match in order to be able to configure the board.

The **bootloader (BL)** is a small piece of software which is started as soon
as the board is powered up. Every board ships with a bootloader preloaded and
is not normally required to be upgraded by the user.

The **bootloader updater (BU)** is a special firmware which is loaded by the
current bootloader and replaces the old bootloader with the new bootloader
which it contains. This approach is required because the bootloader can't
erase and overwrite itself.

.. rubric:: The bootloader version isn't updated after the update.

There is a built in check that prevents the user from updating the bootloader
with an incompatible version. If the blue LED blinks rapidly and continuously
during the upgrade process, the updater is in an error state. Reboot the board
and repeat the process using the correct bootloader updater.

