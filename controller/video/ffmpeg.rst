======
FFMPEG
======

Configuration Options
=====================

+------------------------+-----------------------+-----------------------------+
|Variable                |Default Value          |Description                  |
+========================+=======================+=============================+
|``ffmpeg_location``     |``/usr/bin/ffmpeg``    |Full path to the location of |
|                        |                       |FFMPEG.                      |
+------------------------+-----------------------+-----------------------------+
|``v4l2-ctl_location``   |``/usr/bin/v4l2-ctl``  |Full path to the location of |
|                        |                       |``v4l2-ctl``                 |
+------------------------+-----------------------+-----------------------------+
|``audio_codec``         |``mp2``                |Audio codec FFMPEG should    |
|                        |                       |use. Only ``mp2`` is         |
|                        |                       |supported but ``twolame``    |
|                        |                       |will work when compiled into |
|                        |                       |FFMPEG.                      |
+------------------------+-----------------------+-----------------------------+ 
|``audio_channels``      |``1``                  |Audio channels, 1 for mono,  |
|                        |                       |2 for stereo.                |
+------------------------+-----------------------+-----------------------------+
|``audio_bitrate``       |``32``                 |Bitrate for the audio stream |
|                        |                       |in kilobits                  |
+------------------------+-----------------------+-----------------------------+
|``audio_sample_rate``   |``44100``              |sample rate for the audio in |
|                        |                       |hertz                        |
+------------------------+-----------------------+-----------------------------+
|``video_codec``         |``mpeg1video``         |Video codec FFMPEG should    |
|                        |                       |use. Currently only          |
|                        |                       |``mpeg1video`` is supported. |
+------------------------+-----------------------+-----------------------------+
|``video_bitrate``       |``350``                |Bitrate for the video stream |
|                        |                       |in kilobits                  |
+------------------------+-----------------------+-----------------------------+
|``audio_input_format``  |``alsa``               |                             |
+------------------------+-----------------------+-----------------------------+
|``audio_input_options`` |                       |Leave this blank if          |
|                        |                       |``audio_input_format`` is    |
|                        |                       |``alsa``                     |
+------------------------+-----------------------+-----------------------------+
|``audio_output_options``|``-nostats``           |                             |
+------------------------+-----------------------+-----------------------------+
|``video_output_format`` |``v4l2``               |                             |
+------------------------+-----------------------+-----------------------------+
|``video_output_options``|``-nostats -threads 2``|                             |
+------------------------+-----------------------+-----------------------------+