First Flight
============

Pre-flight checks
-----------------

There are a few things that you'll want to check before flying. Especially in
the case of a multi-rotor. If you have swapped your motor outputs or your servo
output is reversed, then the multi-rotor may flip or spin directly upon lift
off.

.. warning:: **REMOVE PROPELLERS!**

   You should always remove your propellers prior to starting tests or 
   connecting your battery for the first time.

Arming (Turn your board on)
^^^^^^^^^^^^^^^^^^^^^^^^^^^

At start-up the system is disarmed. When disarmed, the motor(s) will not
function, but the servos should work (*If installed, e.g. on Tri-Copter*).
Before flying, the system needs to be armed with a specific stick input. The
inputthat is needed for arming (and disarming) is configurable. For safety
reasons, the default configuration is such that the system will not arm under
any condition. Hence, it's mandatory that you configure the arming in the GCS
input configuration.

Check your system alarms
^^^^^^^^^^^^^^^^^^^^^^^^

The flight controller will not arm itself if any system status alarms are
present. They can be checked by connecting to the flight controller board with
OpenPilot Ground Control Station, and looking at system status indication under
the primary flight display. All status objects should be green. PATH can remain
yellow. For mode information on alarms, read the next page.

Check your stick inputs
^^^^^^^^^^^^^^^^^^^^^^^

**With props removed**, after you have armed your board, the blue LED should
start flashing rapidly indicating that the board is armed. If you have
specified that the "motors should spin at neutral output" in the
:doc:`output configuration </gcs/output>`, the motors should start spinning
right now. Otherwise you can now apply some throttle and get the motors
spinning.

Verify that the correct motors follow your stick input. E.g. rolling left
should increase the throttle on your right motor(s) and vice versa. If the
wrong motors are spinning faster, you need to recheck your configuration.

.. rubric:: Rate mode

Note that some motors could start spinning faster if you have already selected
a stability mode on your transmitter with the Flight Mode switch. You should
do your first tests in rate mode only.

Check your stabilization
^^^^^^^^^^^^^^^^^^^^^^^^

While the motors are spinning, you can move the aircraft in the pitch or roll
direction. The flight controller should react promptly and accelerate the
correct motors to counteract the movement. Please make sure that the correct
motors are spinning up. If the opposite motors spin up, then you would flip
your multi-rotor immediately upon lift off. In this case, you need to recheck
your configuration.

.. important:: Check fail-safe!

Arm the aircraft and run your motors, now turn off the transmitter and confirm
that all motors stop.


Your first flight (multicopters and helicopters)
------------------------------------------------

You've done your pre-flight checks, your transmitter and flight batteries are
all fully charged, and you are confident that the vehicle has been configured
correctly - it's time to fly!

But, it's also time to take a deep breath and honestly evaluate your flying
skills - if you are a novice then you should consider buying a flight simulator
and developing some basic skills - crashes in a simulator cost nothing, so you
will rapidly justify the investment for this software.

If you are feeling confident, take the model to a large, clear and deserted
open space - you don't want any trees or overhead wires nearby, you definitely
don't want any people or dogs in the area, and you shouldn't be too close to
a road. A grass field is better for first flights, rather than concrete or
tarmac. Ideally there will be no wind, but a very slight breeze shouldn't be
a problem.

.. important::

   You may be disconnecting and connecting power to the model several times
   during these first steps - you must wait at least 30 seconds before
   reconnecting power, otherwise the model may behave unpredictably.

   Remember to keep the model still for about 10 seconds after each connection,
   while the gyros are calibrated.

The following steps have been written on the assumption that 'Zero gyros while
arming aircraft' has been selected on the
:doc:`Attitude Configuration </gcs/attitude>` page of GCS (the recommended
setting). This can help with the stabilization of the model.

.. note:: Remember to keep the model still for several seconds after arming,
   while the gyros are zeroed.

#. If you have brought anybody with you to witness the first flight, make sure
   that they know where to stand, how to behave, and what to do if the vehicle
   goes out of control. If there are any children, make sure that they are
   under close supervision.
#. Put the throttle stick to minimum and switch on the transmitter. If your
   transmitter has a throttle lock facility, set this to 'locked'. Put the
   transmitter on the ground next to where you plan to stand while flying the
   vehicle.
#. Place the model on the ground about 10 paces away with the tail towards the
   transmitter. If there is a breeze, put the model either upwind or downwind
   of the transmitter - you don't want a cross-wind.
#. Connect the power to the vehicle and **do not move it for about 10 seconds**
   **while the gyros are calibrated**. Return to your transmitter.
#. Take a good look around for safety's sake, then unlock the throttle and arm
   your board - the blue LED on the board will now flash rapidly and the rotors
   will spin if you've selected 'Motors spin at neutral output when armed'.
   **IMPORTANT: you must wait a few seconds after arming while the gyros are**
   **zeroed** (see note above). The aircraft may be unstable if this isn't
   done. Use this time to have another good look around you.
#. Steadily increase the throttle until the vehicle is about to lift off the
   ground - any tendency to flip or spin will be apparent at this time. Close
   the throttle immediately if the vehicle does anything unexpected, and then
   take a look at the problem-finding guide.
#. If everything looks OK. then close the throttle, disarm the vehicle, take a
   deep breath and have yet another look round the field - it's time for
   lift-off!
#. Arm the vehicle, wait for a few seconds, then open the throttle confidently
   until the aircraft lifts off the ground. Try to hover about 1 or 2 metres
   off the ground, while keeping in one position.

You are now flying! Obviously this bit is not as easy as it sounds and much
practice is required.

The important thing to remember is to close the throttle if the aircraft goes
out of control - you will crash at some time, and cutting the power will
minimize the damage.

Get into the habit of disarming the board when landing for more than a few
seconds or when approaching the vehicle to handle it, and don't forget the
short wait after re-arming - again, use this period to look around the field
before flying.

Disarm the board and set the throttle lock when you have finished flying, then
put down the transmitter a little way from the model. Disconnect the power
from the aircraft, then turn off your transmitter.

Now that you have proven that the aircraft will fly, you might like to try the
training exercise videos for helicopters found on this website page. Many
of these are also suitable for multi-rotors.

.. todo:: FIXME: Trainig videos


Optimizing values
-----------------

Apart from tuning the stabilization settings, there are some values which
advanced users may want to change pretty soon. The default values will fly your
aircraft perfectly fine, but would limit some users in their flying style.

Please find below a few settings which can easily be cranked up for more
experienced users. Note: these are available in each of the three Settings
Banks.

.. rubric:: Full stick angle in Attitude mode

+--------------+-------------------------------------------------------------------+
| Location     | Stabilization panel, Responsiveness, Attitude mode response (deg) |
+--------------+-------------------------------------------------------------------+
| Standard     | 55°                                                               |
| value        |                                                                   |
+--------------+-------------------------------------------------------------------+
| Tuned+ value | 65° or more                                                       |
+--------------+-------------------------------------------------------------------+

Specifies how many degrees the vehicle will bank on a full stick deflection
when in attitude mode.

If you fly your multi-rotor in heavy wind, you may find that low values are not
sufficient to counteract the wind fast enough. The default value is fairly good
for a beginner.

.. rubric:: Full stick response in Rate mode

+--------------+-----------------------------------------------------------------+
| Location     | Stabilization panel, Responsiveness, Rate mode response (deg/s) |
+--------------+-----------------------------------------------------------------+
| Standard     | 220°/s                                                          |
| value        |                                                                 |
+--------------+-----------------------------------------------------------------+
| Tuned+ value | 360°/s or more                                                  |
+--------------+-----------------------------------------------------------------+

Specifies how many degrees per second a full stick deflection commands in all
modes **except Attitude mode**.

If you want to do flips with your multi-rotor you should increase this setting.
Flips that take too long to complete can result in too much loss of altitude
for the beginner. To get some idea of how fast you want to flip, imagine the
flip taking one second to complete - that would equate to 360°/s.

.. note:: This is the value to control rotation rate when using Rattitude mode.

.. rubric:: Full stick response limit in any mode

+--------------+-------------------------------------------------------------+
| Location     | Stabilization panel, Responsiveness, Max rate limit (deg/s) |
+--------------+-------------------------------------------------------------+
| Standard     | 300°/s                                                      |
| value        |                                                             |
+--------------+-------------------------------------------------------------+
| Tuned+ value | 360°/s or more                                              |
+--------------+-------------------------------------------------------------+

Specifies the maximum rotation rate in degrees per second commanded by a full
stick deflection on the associated axis **in any mode**.

Make sure this is the same or higher than Rate mode response above.

.. rubric:: MaxAxisLock

+--------------+--------------------------------------------+
| Location     | Stabilization panel, Expert Tab, Axis Lock |
+--------------+--------------------------------------------+
| Standard     | 5°                                         |
| value        |                                            |
+--------------+--------------------------------------------+
| Tuned+ value | 15°                                        |
+--------------+--------------------------------------------+

The maximum number of degrees that the control accumulates error. The default
setting is changed to 15° in newer firmware & should be a good value for
multi-rotors.

