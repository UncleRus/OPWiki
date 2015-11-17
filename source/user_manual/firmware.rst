Installing or Updating Your Firmware
====================================

You should check the bootloader version of any CC or CC3D and know the
Bootloader version. If not already on Version 4, you MUST upgrade your
Bootloader via the documentation linked below before using any firmware from
13.xx and newer.

For directions on checking bootloader version and installation instructions,
please see the :doc:`Bootloader Update </appendices/bootloader>` page.

.. note:: Please ensure you download the correct v4 Bootloader. CC, CC3D/Atom,
   OPLink and Revo all use different bootloader files!

The firmware for your OP boards is packaged within the GCS download. To update
the firmware on the various OpenPilot boards follow these steps:

#. Uninstall any previous versions of OpenPilot GCS
#. Install the latest OpenPilot GCS version (available from the previous page
   of this Wiki, the :doc:`gcs_install` page)
#. Read through the informational documentation for CC/CC3D and/or Revolution
   page by using the links at the bottom of this page.
#. Once familiar with your board's functions, find the Welcome tab of the GCS
   and with your board plugged in, proceed through the Vehicle Setup Wizard for
   Multirotor or Fixed Wing.

For vehicles other than MultiRotor or Fixed Wing, or to install firmware
manually (without the wizard) you must take the following steps to ensure that
your firmware is updated correctly:

#. Uninstall any previous versions of OpenPilot GCS
#. Install the latest OpenPilot GCS version (available from the previous page
   of this Wiki, the Downloading and Installing the Ground Control Station page)
#. Open the OpenPilot GCS and go to the Firmware Tab
#. With the board unplugged, click the Rescue button
#. Connect the board
#. (There's a chance that the new drivers might not finish installing before
   the timer runs out. If this happens, wait until the drivers finish their
   install, then unplug the board, click Rescue again, connect the board and
   continue)
#. and click the Erase Settings button.
#. Wait approximately 30 seconds
#. Click the Upgrade & Erase button and follow the on-screen instructions
#. Firmware install/update complete.

.. warning:: Never install any firmware on your board that came from untrusted
   source! Trusted sources are the OpenPilot Downloads page or firmware that you
   have built yourself from the official git repository.

Next, Select your Flight Controller:

* :doc:`CC - CC3D - Atom <cc3d>`
* :doc:`Revolution <revo/index>`
