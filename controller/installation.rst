============
Installation
============

.. attention:: If you're migrating your robot from Let's Robot, there are a few
    key things this controller does differently. You can read more about it 
    :doc:`here <./migrating>`.

.. tip:: If this is your first time working with a Raspberry Pi or Linux,
    we recommend following our :doc:`initialization tutorial <./getting_started>`
    to get started.

.. tip:: If doing things manually isn't your style, we made an :doc:`optional 
    guided installation script <./guided_installation>` that handles mostly
    everything for you.

The Raspbery Pi will need the following things installed so it can talk to your
motors and to Remo. Make sure you don't get any errors in the console when 
installing. If you have an issue, you can run the first step again, that will 
usually fix it!

#. Install the required software libraries and tools. Make sure you don't get
   any errors in the console. If you have an issue, you can run this line again,
   and that will usually fix it! ::

    sudo apt update
    sudo apt upgrade -y
    sudo apt install ffmpeg python-serial python-dev libgnutls28-dev espeak python-smbus python-pip git 

#. Download the remotv controller scripts from GitHub. ::

    git clone https://github.com/remotv/controller.git ~/remotv

#. Install python requirements. ::

    sudo python -m pip install -r ~/remotv/requirements.txt

#. Open the new ``remotv`` directory. ::

    cd remotv 

#. Copy ``controller.sample.conf`` to ``controller.conf``. ::

    cp controller.sample.conf controller.conf 

Configure the Controller
------------------------
You'll need to follow the guide :doc:`here <./configuration>` to configure the
controller for your robot.

Getting your robot to start the controller when it boots
--------------------------------------------------------

#. Copy the ``start_robot`` script to your home directory. ::

    cp ~/remotv/scripts/start_robot ~

#. Add the startup script to ``crontab``. ::

    crontab -e 

   .. tip:: If you accidentally use the wrong editor, run:
        ``EDITOR=nano crontab -e``

#. Insert the following text at the bottom. ::

    @reboot /bin/bash /home/pi/start_robot

   Example: ::

    # Edit this file to introduce tasks to be run by cron.
    #
    # Each task to run has to be defined through a single line
    # indicating with different fields when the task will be run
    # and what command to run for the task
    #
    # To define the time you can provide concrete values for
    # minute (m), hour (h), day of month (dom), month (mon),
    # and day of week (dow) or use '*' in these fields (for 'any').
    #
    # Notice that tasks will be started based on the cron's system
    # daemon's notion of time and timezones.
    #
    # Output of crontab jobs (including errors) is sent through
    # email to the user the crontab file belongs to (unless redirected).
    #
    # For example, you can run a backup of all your user accounts
    # at 5 a.m every week with:
    # 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
    #
    # For more information see the manual pages of crontab(5) and cron(8)
    #
    # m h dom mon dow   command

    @reboot /bin/bash /home/pi/start_robot

#. Now just plug in your camera and speaker and reboot. ::

    sudo reboot
    