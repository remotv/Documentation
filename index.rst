.. Remo Documentation master file, created by
   sphinx-quickstart on Thu Aug 27 15:51:28 2020.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

================================
Welcome to Remo's documentation!
================================

.. toctree::
   :maxdepth: 2
   :caption: Prologue
   :glob:
   
   /*

.. toctree::
   :maxdepth: 2
   :caption: Controller
   :glob:

   controller/getting_started
   controller/installation 
   controller/configuration
   controller/troubleshooting
   controller/extending
   controller/parallaxy

.. toctree::
   :maxdepth: 2
   :caption: Controller - Hardware
   :glob:

   controller/hardware/*

.. toctree::
   :maxdepth: 2
   :caption: Controller - TTS
   :glob:

   controller/tts/*

.. toctree::
   :maxdepth: 2
   :caption: Controller - Video
   :glob:

   controller/video/*

.. toctree::
   :maxdepth: 2
   :caption: Client
   :glob:

   client/*


.. put entries that you don't want in a table of contents in here. They won't
   show up in the navbar, or have links rendered in the HTML. This is mostly to
   stop warnings showing up when you build the documentation that the files 
   aren't in any table of contents.


.. toctree::
   :hidden:

   controller/migrating
   controller/guided_installation