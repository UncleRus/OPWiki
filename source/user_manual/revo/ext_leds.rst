Revo - External LED setup
=========================

Overview
--------

This document will describe the necessary hardware and software setup to
connect an external notification LED to Revolution. WS2811, WS2812 and WS2812B
multicolor LEDs are supported in both single LED or multiple LED configurations.
The LED is useful for debugging and it provides visual information about flight
modes and warnings during flight. The battery low voltage warning is
particularly useful.

`<https://www.youtube.com/watch?v=S7CISYWC7MA>`_

.. raw:: html
   
   <iframe width="560" height="315" 
   src="https://www.youtube.com/embed/S7CISYWC7MA"
   frameborder="0" allowfullscreen></iframe>
   

Hardware Connections
--------------------

.. image:: img/ws2812.jpg

The OpenPilot firmware supports LEDs wired in both parallel and series
configurations. A single LED is capable of displaying all of the data. Both
the LED strips and the modules have voltage input (5V), ground (GND) and signal
input (DI) pins, and also often corresponding output pins. For a single LED
configuration, the output pins are not used; and in a multiple LED
configuration, you can wire the LEDs together serially in a chain.

On the left is an example of a very common single LED module which is readily
available on eBay. If you use a single LED, make sure that the breakout board
has a capacitor on it; otherwise, inrush current spikes can damage the LED.
The capacitor is usually a surface mounted component just like the brown one
next to the LED unit in the photo. A capacitor is optional on configurations
with two or more LEDs.

Revolution can command the LED(s) from various outputs. For the output signal,
servo output rail pins 1-6 are supported, and Flexi-IO port pins 3 and 4
(from the left) are supported. Power for the LED is available from Flexi-IO
pins 1 (GND) and 2 (5V), or from the servo output rail. After making the
necessary connections, it is recommended that you mount the LED so that it is
visible from below while flying.

The diagram below show the various configurations.

.. todo:: FIXME diagram


Software Setup
--------------

Following hardware setup, configure the controller in GCS as follows:

* Go to **System tab > HwSettings > WS2811LED_Out** and choose the pin where
  you connected the LED(s)
* Click the red **Save button** in the top part of the view
* Disconnect Revolution from PC
* Connect your flight battery. LED(s) should start showing system status
  according to the graphic in the Light Codes section below.


Light Codes
-----------

The following graphic shows different notifications Revolution will display
with the LED(s).

.. image:: img/Revo-External-Leds.png
