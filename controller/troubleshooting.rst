===============
Troubleshooting
===============

Raspberry Pi Camera Module
--------------------------

Sometimes enabling the Raspberry Pi Camera Module in ``raspi-config`` doesn't 
completely load the kernel drivers for it. If you don't see ``/dev/video0`` on
your system, or ``controller.py`` complains about not finding it, then do the 
following:

#. Enable the kernel module for your current session: ::

    sudo modprobe bcm2835-vl42

#. Tell the operating system to load the kernel module at boot going forward: ::

    sudo cat 'bcm2835-vl42' >> /etc/modules

Now you should see ``/dev/video0`` if you do ``ls /dev/video*``