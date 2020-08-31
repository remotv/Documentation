========================
Extending the controller
========================

The controller is designed to make modifying the functionality as easy as
possible, while still allowing the core code to be updated without requiring
users to modify the controller with their custom functionality every time.

Adding New Hardware Support
===========================
Adding new hardware to the controller is fairly simple. Create a new ``.py``
file in the hardware directory. Ths name you give this file becomes the name 
for this hardware type in the configuration file. This file needs to contain 
two functions, as shown in this example.

.. code-block:: python
    :linenos:

    def setup(robot_config):
        # your hardware setup code goes here
        return

    def move(args): 
        command = args['button']['command']

        if command == 'F':
            # your hardware movement code for forward goes here 
            return
        elif command == 'B':
            # your hardware movement code for backwards goes here 
            return
        elif command == 'L':
            # your hardware movement code for left goes here 
            return
        elif command == 'R':
            # your hardware movement code for right goes here 
            return
        return

Hardware ``setup()`` Function 
-----------------------------
The ``setup()`` function is passed the ConfigParser object for the 
controller.conf file. You can create a new section for your hardware in the 
controller.conf file, and store your configuration variables there. Variables in
the configuration file can be accessed with ``robot_config.get(section, option)``,
``robot_config.getint(section, option)``, and ``robot_config.getboolean(section, option)``.

Any initial hardware setup should happen when the ``setup()`` function is called.
This function is only called once.

``move()`` Function
-------------------
The ``move()`` function is passed the object containing the command for the robot
received from the server.

.. code-block:: json
    :linenos:

    {
    "e": "BUTTON_COMMAND",
    "d": {
        "user": {
            "username": "brooke",
            "id": "user-328a312d-0ac0-4290-b482-720f0dc2166a",
            "status": { "timeout": false, "expireTimeout": 1561673063070 }
        },
        "button": {
                "id": "bttn-75a8e2b5-5bfc-4fa0-8d2d-8a2365a16be1",
                "label": "forward",
                "command": "f",
                "hot_key": "w"
            },
            "controls_id": "cont-ea0d8dd9-c7be-4659-b41a-2ccaa67486bb",
            "channel": "chan-63a18243-9424-4594-b496-e7d80a06a6f1"
        }
    }

It should be mostly self explanatory, the most important part is the ``command``.
The ``move()`` function should use the provided command to determine how to move
the robot. If your hardware needs specific start and stop instructions to move,
with a pause between, you should import the ``time`` module and use its 
``sleep()`` function.

.. code-block:: python

    GPIO.output(StepPinForward, GPIO.HIGH)
    time.sleep(sleepTime)
    GPIO.output(StepPinForward, GPIO.LOW)

The controller will block, and ignore any other commands from the server until
the ``move()`` function finishes. If you want to implement your own blocking, 
or implement proper asynchronous movement commands, you can disable the blocking
by setting ``enable_async=True`` in the [misc] section of controller.conf.

Adding new TTS Support
======================

This is almost exactly the same as adding new hardware. Create a new ``.py`` file 
in the tts directory. The name you give this file becomes the name for this tts 
type in the configuration file. This needs to contain two functions, as shown 
in this example.

.. code-block:: python
    :linenos:

    def setup(robot_config):
        return

    def say(*args):
        message = args[0]
        return

TTS ``setup()`` Function
-------------------------
The ``setup()`` function is passed the ConfigParser object for the controller.conf 
file. You can create a new section for your tts in the conf file, and store
configuration variables there. Variables in the configuration can be accessed
with ``robot_config.get(section, option)``, ``robot_config.getint(section, option)``,
and ``robot_config.getboolean(section, option)``.

Any initial TTS setup should happen when the ``setup()`` function is called. 
This function is only called once.

``say()`` Function
------------------
The first argument will always be the plain text message. The second argument, 
if it exists, will be the chat message object that was sent to the robot from 
the server. It looks like this.

.. code-block:: json
    :linenos:

    {
        "e": "MESSAGE_RECIEVED",
        "d": {
            "message": "beep beep ",
            "sender": "brooke",
            "sender_id": "user-328a312d-0ac0-4290-b482-720f0dc2166a",
            "chat_id": "chat-07aba28b-42b8-4b16-8b69-bdd6997807ae",
            "server_id": "serv-be71b50b-209f-4d76-82e9-c25ce2f547f5",
            "id": "mesg-54fa88df-3b64-4e05-91a4-3cd6175558e4",
            "time_stamp": 1563061665625,
            "broadcast": "",
            "displayMessage": true,
            "badges": ["global_moderator"],
            "type": ""
        }
    }

The actual code required to take the text message, and play it as audio should
reside in this function.

Extending Existing Hardware
===========================
When the ``custom_hardware`` option in the ``misc`` section of controller.conf
is set to true, the controller will look for a file named ``hardware_custom.py``
in the hardware directory. If the file exists, it will load that instead of the
file relating to the hardware type specified in controller.conf.

In this way, existing hardware functions can be modified or extended, or
entirely replaced. Though if you are replacing the functions entirely, you may 
be better off creating a new hardware type instead.

The ``hardware_custom.py`` file needs to have the same two functions, as
outlined for new hardware above, but in order to extend functionality, there is
a slight difference.

.. code-block:: python
    :linenos:

    import mod_utils
    module = None

    def setup(robot_config):
        # Your custom setup code goes here

        # This code calls the default setup function for your hardware. 
        # global module
        module = mod_utils.import_module('hardware', robot_config.get('robot', 'type'))
        module.setup(robot_config)

    def move(args):
        command = args['button']['command']
        # Your custom command interpreter goes here

        # This code calls the default command interpreter function for your hardware.
        module.move(command)

The ``setup()`` function includes code to import the hardware controller you are
extending into ``module``. It also calls the setup function for that module.

The ``move()`` function also has a command interpreter similar to the one in the
hardware module you are extending, except this one only needs to contain the
commands that aren't handled in the hardware module. After the custom command 
interpreter has run, it should call the ``move()`` command from the hardware 
module, to handle the non-custom commands.

Extending existing TTS
======================

This is very similar to extending existing hardware as outlined above. Except 
that where extending hardware involves adding new functions, extending TTS is 
more about modifying the way messages are handled.

When the ``custom_tts`` option in the ``misc`` section of controller.conf is set
to true, the controller will look for a file named ``tts_custom.py`` in the TTS
directory. If that file exists, it will load that instead of the file relating
to the tts type specified in the controller.conf.

In this way, existing TTS functions can be modified and extended, or entirely
replaced. Though if you are replacing functions entirely, you may be better off
creating a new TTS type instead.

The ``tts_custom.py`` file needs to have the same two functions, as outlined for
new tts above, but in order to extend functionality there is a slight difference.

.. code-block:: python
    :linenos:

    import mod_utils
    module = None

    def setup(robot_config):
        # Your custom setup code goes here

        # This code calls the default setup function for your tts.
        # global module
        module = mod_utils.import_module('tts', robot_config.get('tts', 'type'))
        module.setup(robot_config)

    def say(*args):
        message = args[0]
        # Your custom tts interpreter code goes here

        module.say(message, args[1])

The ``setup()`` function includes code to import the hardware controller you are
extending into ``module``. It also calls the setup function for that module. 

The ``say()`` function should modify the message or TTS function before calling 
the ``say()`` command from the TTS module, to handle the actual text conversion
to sound.