Revo - LED Indications
======================

They will show in sequence:

* Notifications
* Alarms
* Heartbeat/FlightStatus/ArmingMode.

Sequences are shown using the following notation:

+-------+------------------------------+
| r/b/v | short blink on red/blue/both |
+-------+------------------------------+
| R/B/V | long blink on red/blue/both  |
+-------+------------------------------+
| p/P   | pause short/long             |
+-------+------------------------------+

.. rubric:: Notification

+----------------+----------+
| Draw attention | rbrbrbrb |
+----------------+----------+
| Acknowledge    | Vbb      |
+----------------+----------+
| No Acknowledge | VRR      |
+----------------+----------+

.. rubric:: Alarm

+----------+------+
| Warning  | r P  |
+----------+------+
| Error    | rr P |
+----------+------+
| Critical | R    |
+----------+------+

.. rubric:: Heartbeat/FlightMode/ArmingStatus

+------------------------+------+
| disarmed               | B    |
+------------------------+------+
| armed / Stabilization1 | bP   |
+------------------------+------+
| armed / Stabilization2 | bbP  |
+------------------------+------+
| armed / Stabilization3 | bbbP |
+------------------------+------+

+---------------------------------------+-------+
| Armed / AH / AVario / Velocitycontrol | bvP   |
+---------------------------------------+-------+
| armed / PH / Pathplanner / POI        | bbvP  |
+---------------------------------------+-------+
| armed / Land / RTB                    | bbvvP |
+---------------------------------------+-------+

.. todo:: Video Example of Revo LED indications
