=======
GoPiGo3
=======

For GoPiGo3, you will need to install the ``gopigo3`` python module (which is 
different from older versions). It will need to be installed with the 
installation script from Dexter. Also, ``PYTHONPATH`` needs to be set to 
``/home/pi/Dexter/GoPiGo3/Software/Python``

Refer to this: https://github.com/DexterInd/GoPiGo3

.. code-block:: console

    pi@raspberry:~$ sudo git clone https://www.github.com/DexterInd/GoPiGo3.git /home/pi/Dexter/GoPiGo3
    pi@raspberry:~$ sudo bash /home/pi/GoPiGo3/Install/install.sh
    pi@raspberry:~$ sudo reboot

Configuration Options
=====================
+--------------+-------------+-------------------------------------------------+
|Variable      |Default Value|Description                                      |
+==============+=============+=================================================+
|``drive_time``|``0.35``     |Time in seconds to run the motor for each        |
|              |             |forward/back command.                            |
+--------------+-------------+-------------------------------------------------+
|``turn_time`` |``0.15``     |Time in seconds to run the motor for each turn   |
|              |             |command.                                         |
+--------------+-------------+-------------------------------------------------+