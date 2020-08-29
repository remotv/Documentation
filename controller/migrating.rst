========================
Migrating From LetsRobot
========================

If your robot previously worked on Let's Robot, it'll work on Remo. After you 
have cloned this controller, you should edit or replace your ``start_robot``
file with the one provided with this controller.

Config
------
You may find that copying your old config file may not work with this new 
controller. It's recommended to start fresh with the new file. Here's what's
changed:

* Robot ID and Camera ID have been consolidated into one API key.
* Two new off-by-default features to announce your IP and if your cloned
  instance of the repo is out of date.
* The ``[messenger]`` section is removed. It's now built into the controller 
  without any extra configuration.
* Google cloud now supports random voices with whitelisting.
* New supported motor controller, PiBorg ThunderBorg.
* Other miscellaneous changes.

Command Changes
---------------

* All commands are now received in lowercase.
* The call to get a command has changed from ``args['command']`` to
  ``args['button']['command']``
* The call to get the user of a command or message has changed from
  ``args['name']`` to ``args['sender']``
* All logging is done via ``RemoTV.xxx`` instead of ``LR.xxx``