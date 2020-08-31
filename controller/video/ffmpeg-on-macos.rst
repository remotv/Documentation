===============
FFMPEG on MacOS
===============

FFMPEG can run on MacOS with AVFoundation software provided in the operating 
system. 

Installation
============
Homebrew
--------
Installing FFMPEG via `homebrew <https://brew.sh>`_ is the easiest way if you 
have administrator access. 
#. Install Homebrew ::

        /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

.. note:: You may need to reboot after installation finishes.

#. Install FFMPEG ::

        brew install ffmpeg


Changes to `controller.conf`
============================

.. code-block:: python

    [camera]
    type = ffmpeg
    camera_device = "YourCameraDeviceOrNumber"
    mic_device = "YourMicDeviceOrNumber"

    [ffmpeg]
    ffmpeg_location = /usr/local/bin/ffmpeg
    audio_input_format = avfoundation
    video_input_format = avfoundation


Your device id's can be gotten from running ::

    ffmpeg -f avfoundation -list_devices true -i ""


You'll get an output similar to

.. code-block:: bash

    [AVFoundation input device @ 0x7ff8e171e580] AVFoundation video devices:
    [AVFoundation input device @ 0x7ff8e171e580] [0] FaceTime HD Camera (Built-in)
    [AVFoundation input device @ 0x7ff8e171e580] [1] Capture screen 0
    [AVFoundation input device @ 0x7ff8e171e580] [2] Capture screen 1
    [AVFoundation input device @ 0x7ff8e171e580] AVFoundation audio devices:
    [AVFoundation input device @ 0x7ff8e171e580] [0] Built-in Microphone
    [AVFoundation input device @ 0x7ff8e171e580] [1] Built-in Input


In my case I want to use the FaceTime HD Camera and the Built-in Microphone so 
I can choose the following:

* video
    * ``"0"``
    * ``"FaceTime"``
    * ``"FaceTime HD Camera (Built-in)"``
    * ``"default"``
* audio
    * ``":0"``
    * ``":Built-in Microphone"``
    * ``":default"``
    * The colon (``:``) before every item is very important because that's how 
      AVFoundation differentiates between a camera and a microphone. If you 
      don't get any sound or have errors relating to audio in your console, 
      check that you have a colon before the device in your conf file. 

Note that I can't use the first word of the device name because there's another 
device that shares the same name (``Built-in``).

The name ``default`` means that it will pick the first item in the list ``"0"``.

