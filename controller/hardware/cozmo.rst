=============================
Anki Cozmo on MacOS and Linux
=============================

.. attention:: If you are looking for how to set up Cozmo on Windows, you can
    find instructions :doc:`here <./cozmo-win>`.

Pre-Setup
---------
Install ``socketIO-client`` for ``python3`` ::

    python3 -m pip install socketIO-client configparser

Setup Instructions
------------------

#. Set up the Cozmo SDK on your computer using `their instructions <http://cozmosdk.anki.com/docs/initial.html#installation>`_.

#. Edit ``controller.conf``
    #. Enter your owner, robot_key, etc. from remo.tv
    #. Change [robot] ``type=none`` to ``type=cozmo``
    #. Change [tts] ``type=none`` to ``type=cozmo_tts``
    #. Change [ffmpeg] ``type=ffmpeg-arecord`` to ``type=cozmo_vid``
    #. Save the file.

Install FFMPEG 
--------------

FFMPEG should already be installed on Linux if you've followed the base 
installation instructions.

**MacOS:** ::

    brew install ffmpeg

Starting Cozmo 
--------------

#. Using the Cozmo app, enter SDK mode and connect your mobile device to the
   host machine.
#. Execute the Remo controller using: ::

    cd ~/remotv
    python3 controller.py 

#. For audio streaming, you need a second instance of the controller with a 
   separate conf file with the following changes: ::

    [robot]
    type=none

    [camera]
    no_camera=true

    [tts]
    type=none

#. All other changes remain the same. To execute, run: ::

    cd /path/to/second/controller 
    python3 controller.py

.. tip:: If you don't want to, or cannot run another terminal window, ``screen``
    is a helpful tool for running commands concurrently. 

    Linux: ::

        sudo apt install screen

    ``screen`` is already installed on MacOS.

    To detach from a screen session, type ``^A d``. To reattach a detached screen,
    type ``screen -r``.

Custom Controls
---------------
This controls JSON is designed to work out of the box with the existing Cozmo
controls.

.. code-block:: json 

    [
        { "label": "Left", "hot_key": "a", "command": "l" },
        { "label": "Right", "hot_key": "d", "command": "r" },
        { "label": "Forward", "hot_key": "w", "command": "f" },
        { "label": "Backward", "hot_key": "s", "command": "b" },
        { "label": "Look Up", "hot_key": "q", "command": "q" },
        { "label": "Look Down", "hot_key": "z", "command": "a" },
        { "label": "Lift Up", "hot_key": "e", "command": "w" },
        { "label": "Lift Down", "hot_key": "c", "command": "s" },
        { "label": "Light Toggle", "hot_key": "x", "command": "v" },
        { "label": "Drat", "hot_key": "0", "command": "0" },
        { "label": "Giggle", "hot_key": "1", "command": "1" },
        { "label": "Wow", "hot_key": "2", "command": "2" },
        { "label": "Tick Tock", "hot_key": "3", "command": "3" },
        { "label": "Ping Pong", "hot_key": "4", "command": "4" },
        { "label": "Meow", "hot_key": "5", "command": "5" },
        { "label": "WufWuf", "hot_key": "6", "command": "6" },
        { "label": "LookUp", "hot_key": "7", "command": "7" },
        { "label": "Excite", "hot_key": "8", "command": "8" },
        { "label": "BackUp", "hot_key": "9", "command": "9" },
        { "label": "Hello", "hot_key": "", "command": "sayhi" },
        { "label": "Watch This", "hot_key": "", "command": "saywatch" },
        { "label": "Love You", "hot_key": "", "command": "saylove" },
        { "label": "Bye", "hot_key": "", "command": "saybye" },
        { "label": "Happy", "hot_key": "", "command": "sayhappy" },
        { "label": "Sad", "hot_key": "", "command": "saysad" },
        { "label": "How Are You", "hot_key": "", "command": "sayhowru" },
        { "label": "Sing Song", "hot_key": "", "command": "singsong" },
        { "label": "Light Cubes", "hot_key": "", "command": "lightcubes" },
        { "label": "Dim Cubes", "hot_key": "", "command": "dimcubes" }
    ]

Cozmo Chat Commands
-------------------

In addition to the standard chat commands, Cozmo has several specific chat 
commands available to the owner. You can type these into the chat box on the 
robot page.

* ``.anim NAME`` This will play the NAME animation.
* ``.forward_speed ###`` This will allow you ot adjust how fast Cozmo moves
  forward / backwards.
* ``.turn_speed ###`` This will adjust how far Cozmo turns left and right.
* ``.vol ###`` This turns Cozmo's volume up or down [0...100].
* ``.charge x`` If Cozmo is on the dock, force the charging state. If Cozmo is 
  off the dock, mark the charging state to start as soon as Cozmo docks [on|off].
* ``.stay x`` Set cozmo to stay locked on the dock, regardless of charge state
  [on|off].
* ``.annotate`` Toggles the annotated view, to see what Cozmo is seeing.
* ``.color`` or ``.colour`` Toggles color. Color reduces the resolution of the
  video.

.. note:: For audio streaming on MacOS:

    *NOTE: These instructions are out of date. The current method to stream
    audio involves changing the audio_input_format to avfoundation, video type 
    to ffmpeg and no_camera to true.*

    The ``startAudioCaptureLinux`` function in send_video.py calls ffmpeg with
    alsa input. If you want to stream audio from your mac, use
    `` -f avfoundation -i ":0"`` in place of ``-f alsa -ar 44100 -ac %d 0i hw:%d``.

    For example: ::
    
        audioCommandLine = '/usr/local/bin/ffmpeg -f avfoundation -i ":0" -f mpegts -codec:a mp2 -b:a 128k -muxdelay 0.001 http://remo.tv:1567/transmit?name=%s-audio' % (channelID)

