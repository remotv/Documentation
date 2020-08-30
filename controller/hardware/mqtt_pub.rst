=======================
MQTT Publish Controller
=======================

`MQTT <https://mqtt.org>`_ is a Machine-to-Machine communication protocol 
supporting a lightweight publish/subscribe message transport. It is commonly 
used in IoT and home automation appliances. This Remo hardware controller will 
allow commands received from the remo site to be published to a MQTT broker. 
Various remote robots, devices, and software can subscribe to the MQTT broker 
to receive messages. This configuration will allow the command processing to be 
decoupled from the Remo client software both in software processing and, if you 
choose, the network/system location.

Potential Uses
==============

Using the MQTT Pub hardware with Remo, you can broadcast the command messages 
from the site to many different devices in your robot environment. It would also 
be possible to publish messages to devices that already have an MQTT interface.

A common example would be to separate the video/audio streaming services from 
the command processing software. That is, you could support a camera with video 
that is on a separate computer/raspberry pi than the robot or robots.

``mqtt_pub`` Description
========================

The ``mqtt_pub.py`` script is an implementation of the Remo client hardware
controller. The script uses the Eclipse Foundation Paho Python library.

It contains methods for ``setup()`` amd ``move()``. On ``setup()`` the script 
will load all configurations. It will create an MQTT client and attach handlers
for connection to the configured MQTT broker, publish the 'command' arguments,
and disconnect.

The ``mqtt_pub`` script does not contain the MQTT broker, or subscription
methods.

MQTT Requirements and MQTT Components
=====================================

To use the ``mqtt_pub`` script, the mqtt library 'paho' must be installed on the
machine with the remo client software. Instructions for the installation of 
paho MQTT can be found `here <https://pypi.org/project/paho-mqtt/>`_.

In addition, to use the mqtt capabilities, a MQTT broker must be available to be 
connected and running. The Mosquitto project has a Broker as well as a command 
line publish and subscribe clients. Information on Mosquitto can be found 
`here <https://mosquitto.org/>`_. 
Information on installing a Mosquitto Broker on a Raspberry Pi can be found 
`here <https://www.switchdoc.com/2018/02/tutorial-installing-and-testing-mosquitto-mqtt-on-raspberry-pi/>`_.