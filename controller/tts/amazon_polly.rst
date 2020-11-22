============
Amazon Polly
============

`Amazon Polly <https://aws.amazon.com/polly>`_ is a service that turns text into
lifelike speech, allowing you to create applications that talk, and build
entirely new categories of speech-enabled products. Amazon Polly is a 
`Text-To-Speech <https://aws.amazon.com/polly/what-is-text-to-speech/>`_ service 
that uses advanced deep learning technologies to synthesize speech that sounds 
like a human voice.

With dozens of lifelike voices across a variety of languages, you can select the 
ideal voice and build speech-enabled applications that work in many different 
countries.

This is not a free service. It requires an Amazon AWS account.

* For the 1st 12 months, Amazon Polly includes 5 million characters per 
  month for speech or speech mark requests, starting from your first request.
* After 12 months, or after you exceed 5 million characters in a month, Amazon 
  Polly is priced at USD$4.00 per 1 million characters for speech or speech 
  marks requests.

More information on pricing is available `here <https://aws.amazon.com/polly/pricing>`_.

Installation
=====================
* Required packages:

.. code-block:: console

    pi@raspberry:~$ sudo apt-get install mpg123 
    pi@raspberry:~$ pip install boto3

Configuration Options
=====================
+-----------------+-------------+----------------------------------------------+
|Variable         |Default Value|Description                                   |
+=================+=============+==============================================+
|``robot_voice``  |``Matthew``  |This is the voice your robot gives to messages|
|                 |             |not sent by a user (i.e., the boot message) if|
|                 |             |``random_voices`` is disabled, every user     |
|                 |             |except the owner will use this voice as well. |
+-----------------+-------------+----------------------------------------------+
|``owner_voice``  |``Russell``  |This is the voice the robot gives to messages |
|                 |             |sent by the owner.                            |
+-----------------+-------------+----------------------------------------------+
|``random_voices``|``true``     |When enabled, every unique user will get a    |
|                 |             |different voice.                              |
+-----------------+-------------+----------------------------------------------+
|``access_key``   |             |The full file path to your access key.        |
+-----------------+-------------+----------------------------------------------+
|``secrets_key``  |             |The full file path to your secrets key.       |
+-----------------+-------------+----------------------------------------------+
|``region_name``  |``us-east-1``|The region to send your requests to. You      |
|                 |             |should choose the one physically closest to   |
|                 |             |you.                                          |
+-----------------+-------------+----------------------------------------------+
