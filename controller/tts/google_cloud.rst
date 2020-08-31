===============================
Google Cloud Text to Speech API
===============================

The Google CLoud TTS API offers high didelity, ultra realistic speech synthesis.
A demo is available on its website, https://cloud.google.com/text-to-speech.

This is not a free service. Prices may vary, but at the time of this writing, a 
free one year trial is available with $300 credit towards all Google Cloud 
Platform services.

Features
========

* Multilingual
    * Supports 30+ voices in 13 languages and variants
* WaveNet Voices
    * Exclusive Multilingual access to DeepMind WaveNet voices that provide the 
      most natural sounding speech.
* Text and SSML support 
    * Customize your speech with SSML tags that allow you to add pauses, numbers,
      date & time formatting, and other pronunciation instructions.
* Speaking rate tuning
    * Customize your speaking rate to be 4x faster or slower than normal rate.
* Pitch tuning
    * Customize the pitch of your selected voice, up to 20 semitones more or
      more or less than the default output.
* Volume gain control
    * Increase the volume by up to 16dB or decrease the volume up to -96dB.
* Audio Format Flexibility
    * Choose from a number of audio formats including mp3, Linear16, Ogg Opus.
* Audio Profiles (BETA)
    * Optimize for the type of speaker from which your speech is intended to 
      play, such as headphones or phone lines.

Pricing 
-------
#. Standard (non-WaveNet) voices: up to 4 million characters free; then USD$4.00
   per 1 million characters.
#. WaveNet voices: Up to 1 million characters free, then USD$16.00 per 1 million
   characters.

Setting Up 
==========

Before you Begin
----------------

#. Select or greate a `GCP Project <https://console.cloud.google.com/cloud-resource-manager?_ga=2.920677.-1786735001.1546386686>`_.
#. Make sure that `Billing <https://cloud.google.com/billing/docs/how-to/modify-project>`_ 
   is enabled for your project.
#. Enable the Cloud Text-to-Speech `API <https://console.cloud.google.com/flows/enableapi?apiid=texttospeech.googleapis.com&_ga=2.253124681.-1786735001.1546386686>`_.
#. From the **Service Account** drop-down list, select **New service account**.
#. Don't select a role from the **Role** drop-down list. No role is required to 
   access this service.
#. Click **Create**. A note appears, warning that this service account has no role.
#. Click **Create without role**. A JSON file that contains your key downloads 
   to your computer (this needs to go to your robot).

Copy your JSON file to your robot. All of the following steps need to be run on 
your robot.

Install the client library
--------------------------

.. code-block:: bash

    python -m pip Install --upgrade google-cloud-texttospeech

Using it with the robot
-----------------------

#. In controller.conf, set your tts ``type`` to ``google_cloud``.
#. Choose a voice from `this list <https://cloud.google.com/text-to-speech/docs/voices>`_.
   Make the following changes in the ``google_cloud`` section of ``controller.conf``
#. Set ``key_file`` to the full path of your key file. (i.e. ``/home/pi/googlecloudkey.json``)
#. Set ``voice`` to the name of the voice you want to use (i.e., ``en-US-Wavenet-A``).

Here's a list of all the options

+-----------------------+-------------------+-----------------------------------+
|Variable               |Default Value      |Description                        |
+=======================+===================+===================================+
|``ssml_enabled``       |``false``          |SSML, or Speech Synthesis Markup   |
|                       |                   |Language gives you more control    |
|                       |                   |over how the text is said, bleep   |
|                       |                   |things, or inject audio into the   |
|                       |                   |text. It's set to false by default |
|                       |                   |because it can be readilly abused. |
+-----------------------+-------------------+-----------------------------------+
|``key_file``           |                   |The JSON key needed to authorize   |
|                       |                   |the robot to use the API.          |
+-----------------------+-------------------+-----------------------------------+
|``voice``              |``en-US-Wavenet-A``|What voice you want to use. A      |
|                       |                   |script to show the list of         |
|                       |                   |supported voices is available in   |
|                       |                   |the ``optional`` directory.        |
+-----------------------+-------------------+-----------------------------------+
|``voice_pitch``        |``0.0``            |Changes the pitch of the voice. It |
|                       |                   |can be between ``-20.0`` and       |
|                       |                   |``20.0``                           |
+-----------------------+-------------------+-----------------------------------+
|``voice_speaking_rate``|``1.0``            |Speaking rate changes the speed at |
|                       |                   |which the voice talks at. It can be| 
|                       |                   |between ``0.25`` and ``4.0``       |
+-----------------------+-------------------+-----------------------------------+