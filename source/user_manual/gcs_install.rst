
Downloading and Installing the Ground Control Station
=====================================================

You can use the OpenPilot Ground Control Station (GCS) both to configure your
controller board and to control and monitor your aircraft during flight. More
commonly, you would use a conventional radio control transmitter to control
your vehicle, but the GCS is also capable of doing so.

All OpenPilot products use the same Ground Control Station. OpenPilot GCS is
currently available for the Windows, Mac, and Linux operating systems.

Downloading the GCS installer
-----------------------------

The first step is to download the appropriate GCS installer. Using the release
table below, select the Download Link that corresponds to your computer's
operating system.

If updating from a previous release, you may wish note the current settings for
your vehicle first by creating a .UAV file or taking screenshots of vehicle
settings.

.. important:: The software on this page comes with no warranty. Use it at your
   own risk and please be careful!

Visit the `OpenPilot forums <http://forums.openpilot.org/>`_  if you have
questions and/or suggestions. Extensive documentation about how the system
works and how to install and configure it is available in this wiki.

.. todo:: LINKS

Installation of the GCS
-----------------------

Open the GCS installer file that you downloaded and follow these steps:

1. Choose a language from the drop-down list on the first page, then click OK.
   (You can cancel installation at any point by clicking Cancel.)
2. The OpenPilot Welcome screen appears. Click Next.
3. Review the conditions of the license agreement and then click I Agree to
   accept the terms.
4. You can select which components to install in the Choose Components dialog
   box. Click Next to accept the default selections.

.. note:: Note that the Mesa OpenGL driver may be required by older operating
   systems and is a required component for the GCS interface. If major elements
   of the GCS user interface fail to display, re-installation with selection of
   the Mesa OpenGL driver may help.

5. You can specify where to install OpenPilot GCS in the Choose Install Location
   dialog box. Click Browse to choose a location or Install to install the
   software in the default location shown in the text box.

   Previous installations of the OpenPilot GCS were installed in the Documents
   and Settings directory on Windows machines. The latest default GCS location
   is the standard Program Files location on Windows machines.
6. OpenPilot GCS installs on your computer. Click Next when installation is
   complete.
7. If you have have chosen the default setup, Windows will now install the CDC
   driver for the Virtual Comm Port of your OpenPilot board.

.. note:: Note that the CDC driver is not required to connect and configure
   your OpenPilot board with the GCS. You need the CDC driver for Virtual
   Comm Port support.

8. Click Finish to complete installation. (Clear the check box if you don't want
   OpenPilot GCS to run immediately.)
9. If you choose to run OpenPilot GCS immediately, click OK to load the default
   configuration file.
10. The OpenPilot GCS start page appears. Congratulations! You can explore
    OpenPilot GCS or proceed to the next step, Installing or Updating Your
    Firmware.
