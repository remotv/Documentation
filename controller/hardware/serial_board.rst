========================
Serial Based Controllers
========================

Configuration Options
=====================
+-----------------+----------------+-------------------------------------------+
|Variable         |Default Value   |Description                                |
+=================+================+===========================================+
|``serial_device``|``/dev/ttyACM0``|The hardware address of your serial device |
+-----------------+----------------+-------------------------------------------+
|``serial_name``  |                |Optional vlaue, that will search for a     |
|                 |                |serial port with a specific hardware name  |
|                 |                |or ID. Overwrites ``serial_device`` with   |
|                 |                |the correct value if found.                |
+-----------------+----------------+-------------------------------------------+
|``baud_rate``    |``9600``        |Communication speed in Baud. Make sure your|
|                 |                |controller is set to the same number as    |
|                 |                |this.                                      |
+-----------------+----------------+-------------------------------------------+