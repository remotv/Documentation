=====================
Anki Cozmo on Windows
=====================

.. attention:: If you are looking for how to set up Cozm on Linux or MacOS, you 
    can find those instructions :doc:`here <./cozmo>`.

Pre-Setup
---------
#. Download and setup 
   `python3 <https://www.python.org/downloads/windows>`_ for Windows. Important note: The latest Python version is unfortunately no longer fully compatible with the Cozmo SDK, but version 3.7.9 is known to be compatible with it.

#. Download the latest version of 
   `ffmpeg  <https://www.ffmpeg.org/download.html#build-windows>`_ for Windows. 
   Click the Windows icon under "more download options", then click the Windows 
   build link. Then click to select 32/64 bit and click "download build".

#. Unzip the files to ``C:\ffmpeg`` so the ``ffmpeg.exe`` file is located at 
   ``C:\ffmpeg\bin\ffmpeg.exe``.

#. Install ``SocketIO-client`` for Python3. 

.. code-block:: doscon
    
    C:\Users\you> pip install socketIO-client configparser

Setup Instructions
------------------
Set up the Cozmo SDK on your computer using `their instructions for Windows
<http://cozmosdk.anki.com/dcs/initial.html#installation>`_.

Edit ``controller.conf``

* Enter your owner, robot_key, etc. from Remo.TV
* Change [robot] ``type=none`` to ``type=cozmo``
* Change [tts] ``type=none`` to ``type=cozmo_tts``
* Using ``[ffmpeg] type=cozmo_vid``, along with the custom cozmo.py code from the main remo.tv repository, worked on the previous letsrobot.tv site, but has actually not been known to work yet on the new remo.tv website. You may need to use a different camera source, using ``[ffmpeg] type=ffmpeg``.
    * See `this fork <https://github.com/ztoddw/RemoTV-controller-Cozmo>`_ for a repo that has been working to use your integrated webcam pc, with an overlay showing the Cozmo 1st person view camera.
* In [ffmpeg] comment out the existing ffmpeg_location and uncomment the windows 
  version below it.

Starting Cozmo
--------------
* Using the Cozmo app enter SDK mode and connect your mobile device to the host
  machine.
* Execute the RemoTV controller using ``python3 controller.py``

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

.. note:: To stream audio you will need to have a microphone or webcam with
    microphone attached to your computer. First you will need to determine the
    device name for your microphone. 

    .. code-block:: doscon

        C:\Users\you> C:\ffmpeg\bin\ffmpeg.exe -list_devices true -f dshow -i dummy

    This will list the available devices. The device name is contained between
    "" like so, "Microphone (2- Logitech G522 Gaming Headset)".

    To stream audio, you will need a second instance of the controller with a 
    separate conf file with the following changes 

    .. code-block:: python3

        [robot]
        type=none

        [camera]
        no_camera=true
        mic_device=TheNameOfYourMicrophoneFromThePreviousCommand

        [tts]
        type=none

    Then you can run the separate controller as you would the first.
