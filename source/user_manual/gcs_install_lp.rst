LibrePilot
==========

You can use the LibrePilot Ground Control Station (GCS) both to configure your
controller board and to control and monitor your aircraft during flight. More
commonly, you would use a conventional radio control transmitter to control
your vehicle, but the GCS is also capable of doing so.

LibrePilot GCS is currently available for the Windows, Mac, and Linux
operating systems.


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

Visit the `LibrePilot forums <http://forum.librepilot.org/>`_  if you have
questions and/or suggestions. Extensive documentation about how the system
works and how to install and configure it is available in the
`LibrePilot wiki <https://librepilot.atlassian.net/wiki/display/LPDOC/Welcome>`_
and here.

Latest version can be found here: `<https://librepilot.atlassian.net/wiki/display/LPDOC/Downloads>`_.

RELEASE – 15.09 – First LibrePilot Release - Supermoon Eclipse
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This is the first LibrePilot release.

This version supports the CopterControl, CC3D, Atom, Revolution, Revolution
Nano, Platinum GPS (V9) and OPLink Modems. The main focus of this release is
to bring back support for CC3D and a general re-branding of the GCS.

Some key addition in this release:
   * Easytune : A TxPID feature for 'offline' tuning,
   * Improved motor scaling,
   * Different Acro+ factors for roll and pitch
   * Fixed wing: Roll differential and setup wizard improvements,
   * Import/Export and manage templates,
   * OSX fix for crashes running 'El Capitan',
   * ...

The full list of bug fixes and enhancements in this release is available here:
`15.09 release JIRA list. <https://librepilot.atlassian.net/browse/LP-162?jql=filter%3D10300>`_

.. note: Known Issues:
   
   Due to a change in release naming there is an issue with GCS not showing it
   as a genuine release. It is just a cosmetic issue and does not affects flight
   performance or reliability.

.. rubric:: Windows

`LibrePilot-15.09-win32.exe <http://bit.ly/1jUC3YT>`_

Uninstall previous version first.

.. rubric:: OSX

`LibrePilot-15.09-osx.dmg <http://bit.ly/1LH0KiZ>`_

.. rubric:: PPA for Ubuntu 15.04+

::

   $ sudo add-apt-repository ppa:librepilot/release
   $ sudo apt-get update
   $ sudo apt-get install librepilot

.. rubric:: Arch Linux

Available on the `AUR <https://aur.archlinux.org/packages/librepilot>`_ or
via repository by adding

::

   [librepilot]
   SigLevel = Optional TrustAll
   Server = http://download.librepilot.org/repo/archlinux/librepilot/$arch

to /etc/pacman.conf.

.. rubric:: Fedora

Repository available `here <https://copr.fedoraproject.org/coprs/parched/LibrePilot>`_.

.. rubric:: Source code

* Archives are available at `<http://download.librepilot.org/source/>`_
* The git mirror at `<https://github.com/librepilot/LibrePilot.git>`_

.. rubric:: Bootloaders

:doc:`/appendices/bootloader`

Installation of the GCS
-----------------------

Open the GCS installer file that you downloaded and follow these steps:

1. Choose a language from the drop-down list on the first page, then click OK.
   (You can cancel installation at any point by clicking Cancel.)
2. The LibrePilot Welcome screen appears. Click Next.
3. Review the conditions of the license agreement and then click I Agree to
   accept the terms.
4. You can select which components to install in the Choose Components dialog
   box. Click Next to accept the default selections.

.. note:: Note that the Mesa OpenGL driver may be required by older operating
   systems and is a required component for the GCS interface. If major elements
   of the GCS user interface fail to display, re-installation with selection of
   the Mesa OpenGL driver may help.

5. You can specify where to install LibrePilot GCS in the Choose Install Location
   dialog box. Click Browse to choose a location or Install to install the
   software in the default location shown in the text box.

   Previous installations of the LibrePilot GCS were installed in the Documents
   and Settings directory on Windows machines. The latest default GCS location
   is the standard Program Files location on Windows machines.
6. LibrePilot GCS installs on your computer. Click Next when installation is
   complete.
7. If you have have chosen the default setup, Windows will now install the CDC
   driver for the Virtual Comm Port of your LibrePilot board.

.. note:: Note that the CDC driver is not required to connect and configure
   your LibrePilot board with the GCS. You need the CDC driver for Virtual
   Comm Port support.

8. Click Finish to complete installation. (Clear the check box if you don't want
   LibrePilot GCS to run immediately.)
9. If you choose to run LibrePilot GCS immediately, click OK to load the default
   configuration file.
10. The LibrePilot GCS start page appears. Congratulations! You can explore
    LibrePilot GCS or proceed to the next step, Installing or Updating Your
    Firmware.
