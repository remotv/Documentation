====
Pico
====

The ``picotts`` text-to-speech platform uses offline pico Text-to-Speech engine 
to read a text with natural sounding voices. This requires to install the pico 
tts library on the system, typically on debian just do ``sudo apt-get install 
libttspico-utils``. On some Raspbian release, this package is missing but you 
can just copy the arm deb package from debian.

Configuration Options
---------------------
+---------+-------------+-------------------------------------------------------+
|Variable |Default Value|Description                                            |
+=========+=============+=======================================================+
|``voice``|``en-US``    |The language to use. Supported languages are ``en-US``,|
|         |             |``en-GB``, ``de-DE``, ``es-ES``, ``fr-FR``, and        |
|         |             |``it-IT``.                                             |
+---------+-------------+-------------------------------------------------------+