======
eSpeak
======

`eSpeak <http://espeak.sourceforge.net/>`_ is a compact open source software 
speech synthesizer for English and other languages, for Linux and Windows.

eSpeak uses a "format synthesis" method. This allows many languages to be 
provided in a small size. The speech is clear, and can be used at high speeds,
but not as natural or smooth as larger synthesizers which are based on human 
speech recordings.

Features
========

* Includes different voices, whose characteristics can be altered.
* Can produce speech output as a WAV file.
* SSML (Speech Synthesis Markup Language) is supported (not complete), and also 
  HTML.
* Compact size. The program and its data, including many languages, total about 
  2 MB. 
* Can be used as a front-end MBROLA diphone voices. eSpeak converts text to 
  phonemes with pitch and length information.
* Can translate text into phoneme codes, so it could be adapted as a front end 
  for other speech synthesis engines.
* Potential for other languages. Several are included in varying stages of
  progress. 

Configuration Options
=====================

+----------------+-------------+-------------------------------------+
|Variable        |Default Value|Description                          |
+================+=============+=====================================+
|``male``        |``true``     |Voice gender, male or female         |
+----------------+-------------+-------------------------------------+
|``voice_number``|``1``        |Male supports voices 1-4, Female, 1-7|
+----------------+-------------+-------------------------------------+