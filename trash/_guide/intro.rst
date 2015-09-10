Introduction
============

Welcome to the Getting Started guide! New users of OpenPilot CopterControl,
CC3D and Revolution can use these pages to learn about the system and progress
to their first flight. Experienced users can refresh their memory when setting
up a new board, or gain insight into more detailed functions. Note that
CopterControl and CC3D are functionally the same, use the same GCS and
Firmware, and are set up using an identical process.

It's not practical to have all of the information you need to get started on
a single page, so use this page as a starting point that links to detailed
information and tutorial videos in other parts of the OpenPilot Project
manual (Wiki). Try to take things one step at a time, and don't let the
multitude of links and pages confuse you. It's helpful to open reference
links in a new tab or window so you don't lose your place.

You can think of this page as the trunk of a tree; occasionally you will
need to branch away from this trunk to perform specific tasks, but after
you have completed that task, you can return to the trunk and keep
climbing higher. With that said, let's get started!

This `walk-through video (contributed by fredz69) <https://vimeo.com/51865001>`_
will be very helpful if this is your first time using the GCS.

You will also find detailed instructions & screenshots in the
:doc:`/sw/` portion of this wiki.

The Path to your First Flight
=============================

.. warning:: If you don't read these warnings, you may become part of the
   reason this gets banned in your country! These things can be dangerous.

Personal Safety
---------------

When setting up your vehicle, **DO NOT** install the propellers until ready to fly.
Unintentional activation of motors that are equipped with props can be a bad
way to start your flying experience. **Propellers can cause severe cuts and injury.**
**Be mindful, be safe, and BE CAREFUL!** That being said, just follow these steps to
get safely in the air with the OpenPilot Project.

Avoidable Setup Errors
----------------------

User setup errors can cause fly aways. One example: RC radio is set to hold last
stick position forever on RC Tx failure.

User setup errors can cause crashes, severe personal injury, and expensive
property damage.

It's your responsibility to understand your complete system. The more changes you
make, the more you need to know. One example is that when you enable INS13GPSOutdoor
instead of Complementary in "Attitude -> Settings -> Attitude Estimation Algorithm"
you must learn all about mags, GPS, and twisting your wires.

General Guidelines
------------------

Aircraft need to be configured and tested so that they drop / glide out of the sky
when the go out of RC range or you can get a "fly away" if you fly too far or your
transmitter battery goes dead.  Ground / Water vehicles should simply stop where
they are.  Don't just say "I will avoid those issues" or "I will do that later" because
there are many other things that can cause the RC link to fail.

Never fly over or float / roll beside (or even close to) people or expensive things
because it can drop out of the sky / run over (you didn't think about that boat prop did
you) / hit them if your RC link fails.

If you have a system with a GPS or compass (mags), your mags and wiring (and the
color of your alarms) must be correct and tested or you have confused the controller
into thinking that west is really north, and it will start to fly / run / speed
away, straight into that expensive car / boat over there if you are lucky. Into a
person if you are not lucky.

Step 1: Get a vehicle
---------------------

You will need a radio-controlled vehicle. OpenPilot initially focussed on aircraft but
there is increasing interest and project support for other vehicle types.
:doc:`airframe` section of the Wiki has plenty of examples if you're looking for
inspiration.

Step 2: Install the OpenPilot hardware
--------------------------------------

You will need to install your OpenPilot board on your vehicle.

* :doc:`cc`
* :doc:`revo`

Step 3: Install the Ground Control Station
------------------------------------------

The next step is :doc:`gcs` (GCS) on your computer.

The GCS is used to configure your hardware and can also be used as an interface with the
vehicle during your mission. All OpenPilot products use the same GCS.

.. image:: /img/GCS.jpg

Step 4: Run some preliminary tests, then make your first flight!
----------------------------------------------------------------

* After you have configured your system, run some pre-flight tests, see :doc:`flying`.
* Lastly, before you take to the sky, please read this on :doc:`resp`.

