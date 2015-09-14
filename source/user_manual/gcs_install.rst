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

Latest version can be found here: `<http://www.openpilot.org/download/>`_.

RELEASE – 15.05.02 – Revolution Nano, Revo, OPLM and Platinum GPS
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. note:: Please note that **CC3D is NOT supported by this release**. To find
   the latest release for the CC3D, please see Release – 15.02.02 below. 

.. rubric:: Windows NSIS Installer

`OpenPilot-RELEASE-15.05.2-win32.exe <http://www.openpilot.org/wp-content/uploads/OP-Downloads/OpenPilot-RELEASE-15.05.2-win32.exe>`_

Uninstall previous version first.

.. rubric:: Mac OS X distribution image

`OpenPilot-RELEASE-15.05.2-osx.dmg <http://www.openpilot.org/wp-content/uploads/OP-Downloads/OpenPilot-RELEASE-15.05.2-osx.dmg>`_

Open as a standard distribution image.

.. rubric:: Linux 64 bit Debian package

`openpilot_15.05.2-1_amd64.deb <http://www.openpilot.org/wp-content/uploads/OP-Downloads/openpilot_15.05.2-1_amd64.deb>`_

Uninstall previous version first, then use your system package installer to
install.

.. note:: Please note that Linux .debs will only work with Linux versions Ubuntu
   14.04 or later, due to lack of popularity we are no longer building 32 Bit
   .debs but if needed you can build them easily using the source below and the
   ‘make package’ command.

.. rubric:: Source code

`SRC-OpenPilot-RELEASE-15.05.2.tar.gz <http://www.openpilot.org/wp-content/uploads/OP-Downloads/SRC-OpenPilot-RELEASE-15.05.2.tar.gz>`_


::

   Note that the CC3D is not supported by this release.
   
   This release fixes an important bug of Nano attitude drift with Basic
   attitude estimation. 
   
   All Revolution hardware running 15.05.01 should upgrade to 15.05.02.
   
   Note that this is a hotfix; to get the new defaults a full erase settings
   is required.
   
   Stabilization settings and banks can be imported back after upgrade
   
   Furthermore, please review your vtolpathfollowersettings:HorizontalVelMax;
   a value of around 4m/s would be more appropriate for preliminary trialing of
   a new release and will be changed in future.
   
   This version supports Revolution Nano, Revolution, OPLink Modems, and
   Platinum GPS.


(Previous) RELEASE – 15.02.02 – Revo, CC3D, Atom, CC and v9 GPS
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This version supports the CopterControl, CC3D, Atom, and Revo as well as the
OPLink Modems.

.. rubric:: Windows NSIS Installer

`OpenPilot-RELEASE-15.02.02-win32.exe <http://www.openpilot.org/wp-content/uploads/OP-Downloads/OpenPilot-RELEASE-15.02.02-win32.exe>`_

Uninstall previous version first.

.. rubric:: Mac OS X distribution image

`OpenPilot-RELEASE-15.02.02-osx.dmg <http://www.openpilot.org/wp-content/uploads/OP-Downloads/OpenPilot-RELEASE-15.02.02-osx.dmg>`_

Open as a standard distribution image.

.. rubric:: Linux Debian packages

:32 bit: `openpilot_15.02.02-1_i386.deb <http://www.openpilot.org/wp-content/uploads/OP-Downloads/openpilot_15.02.02-1_i386.deb>`_
:64 bit: `openpilot_15.02.02-1_amd64.deb <http://www.openpilot.org/wp-content/uploads/OP-Downloads/openpilot_15.02.02-1_amd64.deb>`_

Uninstall previous version first, then use your system package installer to
install.

.. note:: Please note that Linux .debs will only work with Linux versions Ubuntu
   14.04 or later.

::

   This release fixes a bug that prevents revo onboard mag to work correctly.
   
   Release Notes - OpenPilot - Version RELEASE-15.02.02
   
   The full list of bugfixes in this release is accessible here:
   https://progress.openpilot.org/issues/?filter=12262
   
   ** Bug
   * [OP-1820] - fix onboard mag orientation
   * [OP-1821] - Tricopter tail servo wrong speed on wizard
   * [OP-1827] - Version ID wrong in Windows uninstaller
   * [OP-1857] - PPM on Flexi does not work on CC/CC3D
   
   ** Task
   * [OP-1831] - due to oneshot higher pid values ki now shows "red" warning in
   stabilization page
   

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
