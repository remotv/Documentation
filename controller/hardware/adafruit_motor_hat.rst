==================
Adafruit Motor Hat
==================

.. image:: ../img/hardware/adafruit_motor_hat.png

Let your robotic dreams come true with the new DC+Stepper Motor HAT from Adafruit!
This Raspberry Pi add-on is perfect for any motion project as it can drive up to
4 DC or 2 stepper motors with full PWM control.

Since the Raspberry Pi does not have a lot of PWM pins, Adafruit uses a **fully
dedicated PWM driver chip** onboard to both control motor direction and speed.
This chip handles all the motor and speed controls over I2C. Only 2 GPIO pins 
(SDA and SCL) are required to drive the multiple motors, and since it's I2C you 
can also connect any other I2C devices or HATs to the same pins.

In fact, **you can even stack multiple Motor HATs**, up to 32 of them, for
controlling up to 64 stepper motors, or 128 DC motors, just remember to purchase
and solder in a stacking header instead of the one they include.

Specs
-----

* 4 H-Bridges: TB6612 chipset provides 1.2A per bridge (3A brief peak) with 
  thermal shutdown protection, internal kickback diodes. Can run motors on 4.5
  VDC to 13.5 VDC.
* Up to 4 bi-directional DC motors with individual 8-bit speed selection (so 
  about 0.5% resolution)
* Up to 2 stepper motors (unipolar and bipolar) with a single coil, double coil, 
  interleaved, or micro-stepping.
* Big terminal block connectors to easilly hook up wires (18-26 AWG) and power.
* Polarity protected 2-pin terminal block and jumper to connect external 5-12
  VDC power.
* Works best with Raspberry Pi model B+ and A+, `but can be used with a model A 
  or B if you purchase a 2x13 extra tall header and solder that instead of the 
  2x20 <https://www.adafruit.com/product/1658>`_.
* Install the easy-to-use Python library, check out the examples and you're
  ready to go!

Assembly
--------
`Refer to their assembly instructions. <https://learn.adafruit.com/adafruit-dc-and-stepper-motor-hat-for-raspberry-pi/assembly>`_

Installing the software
-----------------------
Run the following commands to install the correct library. Do NOT use the
installation instructions from the Adafruit site for the circuit city libraries. ::

    cd /usr/local/src && sudo git clone https://github.com/adafruit/Adafruit-Motor-HAT-Python-Library.git
    cd /usr/local/src/Adafruit-Motor-HAT-Python-Library && sudo python setup.py install

Enable I2C
----------
The Adafruit DC and Stepper Motor Pi HAT kit uses I2C to communicate with your 
Raspberry Pi. ::

    sudo raspi-config
    Interfacing Options -> I2C -> Enable

Configuration Options
---------------------
+------------------------+---------------+-------------------------------------+
|Variable                |Default Value  |Description                          |
+========================+===============+=====================================+
|``turn_delay``          |``0.4``        |Time in seconds to run the motors    |
|                        |               |while turning. This setting is in the|
|                        |               |``[robot]`` section.                 |
+------------------------+---------------+-------------------------------------+
|``straight_delay``      |``0.5``        |Time in seconds to run the motors    |
|                        |               |while going straight. This setting is|
|                        |               |in the ``[robot]`` secton.           |
+------------------------+---------------+-------------------------------------+
|``day_speed``           |``255``        |Speed of the robot during the day.   |
+------------------------+---------------+-------------------------------------+
|``night_speed``         |``255``        |Speed of the robot during the night. |
+------------------------+---------------+-------------------------------------+
|``turning_speed``       |``250``        |Speed of the robot while turning.    |
+------------------------+---------------+-------------------------------------+
|``forward``             |``[-1,1,-1,1]``|Orientation of the motors while      |
|                        |               |moving forward. If one of your motors|
|                        |               |is backwards, you can change it here.|
+------------------------+---------------+-------------------------------------+
|``left``                |``[1,1,1,1]``  |Orientation of the motors while      |
|                        |               |moving left. If one of your motors is|
|                        |               |backwards, you can change it here.   |
+------------------------+---------------+-------------------------------------+
|``slow_for_low_battery``|``false``      |Slows the robot down if the battery  |
|                        |               |is low when set to ``true``.         |
+------------------------+---------------+-------------------------------------+
|``charge_hours``        |``3.0``        |How many hours to charge for.        |
+------------------------+---------------+-------------------------------------+
|``discharge_hours``     |``8.0``        |How many hours to discharge for.     |
+------------------------+---------------+-------------------------------------+
|``chargeCheckInterval`` |``5``          |                                     |
+------------------------+---------------+-------------------------------------+
|``chargeIONumber``      |``17``         |                                     |
+------------------------+---------------+-------------------------------------+