==========================
Configuring the Controller
==========================

``[robot]``
-----------

+------------------+--------------------+-----------------------------------+
| Variable         | Default Value      | Description                       |
+==================+====================+===================================+
|``owner``         |``YourRemoUsername``|The username you have registered on|
|                  |                    |remo.tv                            |
+------------------+--------------------+-----------------------------------+
|``robot_key``     |``YourRobotAPIKey`` |The API key for your robot that you|
|                  |                    |made on the site.                  |
+------------------+--------------------+-----------------------------------+
|``channel``       |                    |The name of the channel you want   |
|                  |                    |the robot to join. This is         |
|                  |                    |optional. If the channel name      |
|                  |                    |cannot be found, the robot will    |
|                  |                    |join the first channel.            |
+------------------+--------------------+-----------------------------------+
|``type``          |``none``            |the type of robot you have (see    |
|                  |                    |list).                             |
+------------------+--------------------+-----------------------------------+
|``turn_delay``    |``0.4``             |Only used by the ``motor_hat`` and |
|                  |                    |``mdd10``. This changes how long   |
|                  |                    |your robot turns for. I suggest you|
|                  |                    |leave this at the default value    |
|                  |                    |until after your bot is moving.    |
+------------------+--------------------+-----------------------------------+
|``straight_delay``|``0.5``             |Only used by the ``motor_hat`` and |
|                  |                    |``mdd10``. This changes how long   |
|                  |                    |your robot drives for. I suggest   |
|                  |                    |you leave this at the default value|
|                  |                    |until after your bot is moving.    |
+------------------+--------------------+-----------------------------------+

* ``type`` should be the hardware type for the motor controller for your 
   robot. Available types are currently:
    * :doc:`adafruit_pwm <./hardware/adafruit_pwm>`
    * :doc:`cozmo <./hardware/cozmo>`
    * :doc:`gopigo2 <./hardware/gopigo2>`
    * :doc:`gopigo3 <./hardware/gopigo3>`
    * :doc:`l298n <./hardware/l298n>`
    * :doc:`maestro-serv <./hardware/pololu_maestro-serv>`
    * :doc:`max7219 <./hardware/max7219>`
    * :doc:`motor_hat <./hardware/adafruit_motor_hat>`
    * :doc:`motozero <./hardware/motozero>`
    * :doc:`mqtt_pub <./hardware/mqtt_pub>`
    * none
    * :doc:`owi_arm <./hardware/owi_arm>`
    * :doc:`pololu <./hardware/pololu_drv8835>`
    * :doc:`serial_board <./hardware/serial_board>`
    * :doc:`thunderborg <./hardware/thunderborg>`

``[camera]``
------------
+-----------------+---------------+--------------------------------------------+
|Variable         |Default Value  |Description                                 |
+=================+===============+============================================+
|``no_camera``    |``false``      |This allows the camera to be disabled.      |
+-----------------+---------------+--------------------------------------------+
|``no_mic``       |``false``      |This allows the microphone to be disabled.  |
+-----------------+---------------+--------------------------------------------+
|``type``         |``ffmpeg``     |This sets the audio/video handler to use.   |
|                 |               |Currently only ``ffmpeg`` and               |
|                 |               |``ffmpeg_arecord`` are supported.           |
+-----------------+---------------+--------------------------------------------+
|``x_res``        |``768``        |Sets the resolution for the ``X`` axis.     |
+-----------------+---------------+--------------------------------------------+
|``y_res``        |``432``        |Sets the resolution for the ``Y`` axis.     |
+-----------------+---------------+--------------------------------------------+
|``camera_device``|``/dev/video0``|Sets the device name for the camera.        |
+-----------------+---------------+--------------------------------------------+
|``mic_num``      |``1,0``        |Sets the audio hardware number for the      |
|                 |               |microphone.                                 |
+-----------------+---------------+--------------------------------------------+
|``mic_device``   |               |Sets the name of the microphone for if the  |
|                 |               |hardware number keeps changing.             |
+-----------------+---------------+--------------------------------------------+

``[tts]``
---------
+------------------+-------------+---------------------------------------------+
|Variable          |Default Value|Description                                  |
+==================+=============+=============================================+
|``type``          |``espeak``   |see the list below.                          |
+------------------+-------------+---------------------------------------------+
|``tts_volume``    |``80``       |This is the volume level you want your bot to| 
|                  |             |start with.                                  |
+------------------+-------------+---------------------------------------------+
|``anon_tts``      |``true``     |This allows you to enable or disable         |
|                  |             |anonymous users from accessing your bots' TTS|
|                  |             |features.                                    |
+------------------+-------------+---------------------------------------------+
|``filter_url_tts``|``true``     |This option allows URLs pasted into chat to  |
|                  |             |be blocked from the TTS function.            |
+------------------+-------------+---------------------------------------------+
|``ext_chat``      |``true``     |This enables or disables the extended chat   |
|                  |             |functions.                                   |
+------------------+-------------+---------------------------------------------+
|``speaker_num``   |``1,0``      |This is the ALSA hardware number for your Pi.|
|                  |             |0 is the first sound card that should work   |
|                  |             |for most bots.                               |
+------------------+-------------+---------------------------------------------+
|``speaker_device``|             |This is the name of your device if the       |
|                  |             |hardware number keeps changing.              |
+------------------+-------------+---------------------------------------------+
|``boot_message``  |``ok``       |This is a list of phrases your bot can say   |
|                  |             |when it's ready to move. Separated by commas.|
+------------------+-------------+---------------------------------------------+
|``delay_tts``     |``false``    |This enables or disables delaying messages   |
|                  |             |being spoken. Messages that are deleted while|
|                  |             |waiting will not be spoken over TTS.         |
+------------------+-------------+---------------------------------------------+
|``delay``         |``10``       |Time in seconds to delay the TTS function.   |
+------------------+-------------+---------------------------------------------+

* ``type`` supports:
    * :doc:`espeak <./tts/espeak>`
    * :doc:`festival <./tts/festival>`
    * :doc:`pico <./tts/pico>`
    * :doc:`polly <./tts/polly>`
    * :doc:`cozmo_tts <./tts/cozmo_tts>`
    * :doc:`google_cloud <./tts/google_cloud>`