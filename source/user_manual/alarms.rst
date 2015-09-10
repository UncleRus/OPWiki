Alarms - What they mean and how to fix them
===========================================

.. todo:: FIXME! Need status objects screenshots!

Status widget overview
----------------------

The OpenPilot flight control firmware has a built-in status system that gives
you an overview about what's happening with the board. The System Health Status
widget in the Ground Control Station can be used to diagnose various problems,
and to check which modules of the firmware are running.

.. rubric:: Arming

The flight control board cannot be armed until crossed-out alarms and red
alarms have been solved. All objects, except for the special "Plan", should be
green for optimal flight performance. The information corresponds to the
UAVObject **DataObjects > SystemAlarms > Alarm**.

The System Health gadget pictured on the left is just an example of what the
widget can look like. It shows a Revolution board that has been set up using
Vehicle Setup Wizard, but has not had the calibrations performed, other than
level calibration. The flight battery is not connected, so no input is shown
coming from the receiver. There is no valid data coming from the GPS (the GPS
is only powered from the flight battery, and will not receive power via USB.)
The board is set to use OpenPilot Platinum GPSv9 which has integrated
magnetometer, so MAG does not show any status until the GPS has power.

Status object explanations
--------------------------

Auto (Autonomous)
^^^^^^^^^^^^^^^^^

Atti
""""

Shows the status of the board's attitude data. If all is well with gyroscope
and accelerometer, it turns green after gyroscope calibration upon power up, or
if you are using "GPS Navigation (INS13GPSOutdoor)" stabilization mode, when
the Inertial Navigation System's **Extended Kalman Filter (EKF)** has fired up.
EKF is a sophisticated sensor fusion algorithm that takes data from relevant
sensors and creates a best possible estimation of the board's angle, velocity
and position.

* *(CROSS)* Attitude data not available, waiting for gyroscope calibration.
  Don't move the vehicle while gyros are being calibrated upon board power-up.
* There is no data coming in from the sensors, which usually indicates faulty
  onboard sensors on CC3D and unknown home location on Revo. For Revo this is
  normal when you have not had GPS fix yet on a new build. The home location
  will be automatically set when GPS gets enough satellites and good fix.
  The sensors can be damaged in a bad crash. Otherwise, contact board seller.
* *(RED)* Data is received from the sensors, but attitude information is not
  available. This usually happens when the EKF is not running yet. Make sure
  that GPS and MAG alarms are green, and that all calibrations have been done
  properly. It sometimes helps to move the vehicle around a bit to give EKF a
  better view of what's going on with sensors.
* *(ORANGE)* EKF is running, but the state estimation is not optimal. Good
  calibration and moving the vehicle a bit helps this situation.
* *(GREEN)* The system has a clear view of the state of the vehicle.

.. rubric:: "The Bug"

There is a very specific condition that can arise within the system that can
sometimes occur after the EKF has been initialised, and the vehicle has been
left stationary for an extended period of time.

Fortunately this condition is easily detected and the flight firmware mitigates
the event. However, the solution is extremely complicated and beyond the
capability of most people, and until such stage as the developers have a chance
to address the matter, it's occurrence is indicated as follows:

* A large red X appears over the PFD.
* A Yellow ATTI alarm with STAB green

This event has been nicknamed "The Bug", and it is still possible to arm and
fly the vehicle in this condition.

Should you wish to clear the indication, one can reset the Revolution flight
controller, or alternatively, change the Attitude Estimation Algorithm to
**Basic(Complementary)**, and then change back to **GPS Navigation(INS13)**.
This action will cause the EKF to reinitialise and the indications will be
cleared.

Stab
""""

Shows whether the board is capable of stabilizing flight. This status goes very
much hand in hand with Atti.

* *(CROSS)* Waiting for gyroscope calibration. Don't move the vehicle while
  gyros are being calibrated upon board power-up.
* *(RED)* The stabilization module cannot stabilize flight. See red Atti status
  for explanation.
* *(GREEN)* Stabilization of flight can be performed.

Path
""""

Shows whether the Revolution board is capable of autonomous path following.
Autonomous flight requires a GPS and a stabilization algorithm set up as GPS
navigation.

* *(BLACK)* The flight controller has not been configured to do autonomous
  flying. Autonomous flight is only possible with stabilization mode "GPS
  Navigation".
* The system has been configured to initialize Path Follower module, but it
  can't be used at the moment. It happens usually because EKF is not running,
  see Atti red explanation.
* *(GREEN)* All is good with the Path Follower module. You can use GPS flight
  modes.

Plan
""""

Shows the status of an autonomous flight plan that can be uploaded to Revolution
using the Ground Control Station. The status of Path remains yellow until a
proper plan has been uploaded, and turns green if all is good with the plan. A
valid plan can be activated with a path follower flight mode.

* *(BLACK)* The flight controller has not been configured to do autonomous
  flying. Autonomous flight is only possible with stabilization mode "GPS
  Navigation".
* *(RED)* Path has been uploaded, but data is invalid and cannot be used for
  autonomous missions.
* *(ORANGE)* No path plan has been uploaded, but the system is ready to receive
  a plan. This is okay if you don't intend to do autonomous missions right now.
* *(GREEN)* A valid and usable flight plan has been uploaded and stored on
  Revolution.


Sensor
^^^^^^

GPS
"""

Shows the status of the GPS that can be connected to an OpenPilot flight
controller. GPS is required for autonomous missions and more sophisticated
flight modes.

* *(BLACK)* A GPS has not been configured to be used.
* *(CROSS)* The GPS has been configured, but no valid data is coming in. This
  is normal if flight battery is not connected, because GPS only gets power
  from external sources, not USB. Check the baud rate and the used protocol of
  your GPS.
* *(RED)* Valid data is received but the GPS has no valid fix. Wait for GPS to
  gather satellites, and preferably have your vehicle in an open area.
* *(ORANGE)* The GPS has a fix and navigation can be used. However, the position
  quality is very low (the indication <7 satellites and/or PDOP > 3.5m). A blue
  LED will flash on the OP v8 and v9 GPS.
* *(GREEN)* The GPS has a valid 3D fix.

.. rubric:: Initial GPS setup information

When powering up the GPS for the first time, it might take over 30 minutes for
the GPS to download almanac information from the satellites and acquire a good
lock. Be patient, and have a clear view of the sky.

Sensor
""""""

Shows the status of the sensor handler module.

* *(BLACK)* Sensor module is not being used in current configuration.
* *(GREEN)* Sensor communications are up and ok.

Airspd
""""""

Shows the status of an optional air speed sensor that can be used with fixed
wing aircraft.

* *(BLACK)* Airspeed sensor has not been configured to be used.
* *(GREEN)* Valid data is coming in from the airspeed sensor.

Mag
"""

Shows the status of Revolution's magnetometer, or the status of an auxiliary
magnetometer on board the OpenPilot GPSv9 if the GPS is configured to be used.

* *(BLACK)* Magnetometer is not being used in current configuration, or
  auxiliary magnetometer is not feeding data. If using GPSv9, power up the
  board externally. Home location has to be set to enable magnetometer.

* *(RED)* Data is coming from the magnetometer, but the readings are off by
  over 15%. This can be caused by various reasons:

  - Magnetometer has not been calibrated with current vehicle (or after recent
    modifications to vehicle)
  - There are high currents in wires, interfering with the magnetometer. Twist
    wires and route them away from magnetometer.
  - Calibration was properly done outside, away from metallic objects, but the
    vehicle is now inside in a different magnetic environment. This is ok.

* *(ORANGE)* Magnetometer readings are off by over 5%
* *(GREEN)* Magnetometer is working properly and the quality of the
  measurements is good.


I/O (Input / Output)
^^^^^^^^^^^^^^^^^^^^

Input
"""""

Input module handles the data that is coming from your receiver.

* *(RED)* R/C input has not been configured. Use Input tab or Transmitter
  Setup Wizard to configure your radio channel inputs.
* *(ORANGE)* No R/C input data. Power up receiver with the flight battery.
* *(GREEN)* Valid R/C input data is coming in.

Output
""""""

Output module takes motor speed and servo position data from stabilization
algorithms, and feeds it into output channels.

* *(RED)* Channel outputs have not been configured. Use Vehicle Setup Wizard
  to configure them automatically.
* *(GREEN)* Outputs are configured can be updated.

I2C
"""

I2C is a bus that connects onboard or auxiliary sensors and handles the data
transmissions. I2C is designed for communications internal to a PCB, and does
not work well via wire connections. It is okay to use for LED controls and
similar functions, but is absolutely not recommended for flight-critical
sensor connections.

* *(BLACK)* I2C module is not being used.
* *(RED)* I2C module is in error state.
* *(GREEN)* I2C communications are up and working properly.


Link
^^^^

Telemetry
"""""""""

Shows the status of Telemetry communications module

* *(RED)* Telemetry module has encountered an error. Set up only one telemetry
  output port.
* *(GREEN)* Telemetry data communications are working properly.


Pwr (Power)
^^^^^^^^^^^

Batt
""""

Battery status shows whether you have enough voltage in the battery to fly. Set
limits for this in FlightBatt (CHECK this) settings. It requires a battery
voltage sensor to work. Battery monitoring module can be enabled in system
settings' optional modules.

* *(BLACK)* Battery monitoring module is not enabled
* *(RED)* Not enough battery voltage to safely take off.
* *(ORANGE)* Battery voltage is low, but flying is possible.
* *(GREEN)* Battery voltage is ok.

Time
""""

Shows whether you have enough energy in the battery left for flying, and
requires a battery voltage and current sensor to work. Currently has a bug when
not using a current sensor; set the battery capacity to 0. This disables the
estimated flight time counter and associated alarms.

* *(BLACK)* Battery monitoring module is not enabled, see above Batt
  explanation.
* *(RED)* Battery energy is low, flying cannot be performed safely.
* *(ORANGE)* Low amount of energy in the battery, flying is still possible.
* *(GREEN)* Good amount of energy left in the battery to fly.


Misc
^^^^

Config
""""""

Shows whether your flight controller board has been properly set up.

* *(RED)* Board configuration problem. If you have set up GPS modes to flight
  mode switch, then make sure that "GPS Navigation" stabilization mode is
  selected.
* *(GREEN)* Board configuration ok.


Sys (System)
^^^^^^^^^^^^

Boot
""""

Shows that a board reboot is required, or fail-safe settings have been loaded
upon boot.

* *(RED)* Boot alarm can be caused by various reasons:

  - No valid telemetry option selected, so board will boot with default USB
    telemetry
  - Board init failed due to driver, module or RAM issues, and the board has
    been booted up in fail-safe state
  - Board has been put to safe mode by the user
  - Board needs a reboot after hardware configuration changes

* *(GREEN)* Flight controller booted up properly.

Mem
"""

Displays the status of remaining memory (RAM) that are used by processes
internal to the flight controller.

* *(RED)* Very low RAM left, flying cannot be done safely.
* *(ORANGE)* Low amount of RAM left, flying can be done but don't enable more
  software modules. This is common with older flight controllers such as
  CopterControl.
* *(GREEN)* Sufficient amount of RAM left for system to operate and expand.

Stack
"""""

Shows the status of the microcontroller's stack, which is a place where
low-level functions store data.

* *(GREEN)* Stack status ok.

Event
"""""

Shows the status of event system. A very heavy load can cause the event system
to be overloaded.

* *(RED)* Event system error or overloaded. This can be caused by a bug or too
  high telemetry update rates when OPLink has low baud, for example.
* *(ORANGE)* Event system at high stress. See above.

* *(GREEN)* Event system ok.

CPU
"""

Indicates CPU load.

* *(RED)* CPU load is very high, flight cannot be performed safely.
* *(ORANGE)* CPU load is high, but flight can be performed. Don't enable more
  software modules.
* *(GREEN)* CPU load is at an acceptable level, and flying is safe.


