Introduction
============


.. image:: https://readthedocs.org/projects/adafruit-circuitpython-s35710/badge/?version=latest
    :target: https://docs.circuitpython.org/projects/s35710/en/latest/
    :alt: Documentation Status


.. image:: https://raw.githubusercontent.com/adafruit/Adafruit_CircuitPython_Bundle/main/badges/adafruit_discord.svg
    :target: https://adafru.it/discord
    :alt: Discord


.. image:: https://github.com/adafruit/Adafruit_CircuitPython_S35710/workflows/Build%20CI/badge.svg
    :target: https://github.com/adafruit/Adafruit_CircuitPython_S35710/actions
    :alt: Build Status


.. image:: https://img.shields.io/badge/code%20style-black-000000.svg
    :target: https://github.com/psf/black
    :alt: Code Style: Black

CircuitPython driver for the S-35710 low-power wake up timer


Dependencies
=============
This driver depends on:

* `Adafruit CircuitPython <https://github.com/adafruit/circuitpython>`_
* `Bus Device <https://github.com/adafruit/Adafruit_CircuitPython_BusDevice>`_

Please ensure all dependencies are available on the CircuitPython filesystem.
This is easily achieved by downloading
`the Adafruit library and driver bundle <https://circuitpython.org/libraries>`_
or individual libraries can be installed using
`circup <https://github.com/adafruit/circup>`_.

`Purchase one from the Adafruit shop <http://www.adafruit.com/products/5959>`_

Installing from PyPI
=====================

On supported GNU/Linux systems like the Raspberry Pi, you can install the driver locally `from
PyPI <https://pypi.org/project/adafruit-circuitpython-s35710/>`_.
To install for current user:

.. code-block:: shell

    pip3 install adafruit-circuitpython-s35710

To install system-wide (this may be required in some cases):

.. code-block:: shell

    sudo pip3 install adafruit-circuitpython-s35710

To install in a virtual environment in your current project:

.. code-block:: shell

    mkdir project-name && cd project-name
    python3 -m venv .venv
    source .env/bin/activate
    pip3 install adafruit-circuitpython-s35710

Installing to a Connected CircuitPython Device with Circup
==========================================================

Make sure that you have ``circup`` installed in your Python environment.
Install it with the following command if necessary:

.. code-block:: shell

    pip3 install circup

With ``circup`` installed and your CircuitPython device connected use the
following command to install:

.. code-block:: shell

    circup install adafruit_s35710

Or the following command to update an existing version:

.. code-block:: shell

    circup update

Usage Example
=============

.. code-block:: python

    import time
    import board
    import adafruit_s35710

    i2c = board.I2C()

    timer = adafruit_s35710.Adafruit_S35710(i2c)

    timer.alarm = 5
    print(f"The S-35710 alarm is set for {timer.alarm} seconds")

    countdown = timer.alarm - timer.clock

    while True:
        print(f"The S-35710 clock is {timer.clock}")
        countdown = timer.alarm - timer.clock
        if countdown == 0:
            timer.alarm = 5
            print("Alarm reached! Resetting..")
        else:
            print(f"The alarm will expire in {countdown} seconds")
        time.sleep(1)

Documentation
=============
API documentation for this library can be found on `Read the Docs <https://docs.circuitpython.org/projects/s35710/en/latest/>`_.

For information on building library documentation, please check out
`this guide <https://learn.adafruit.com/creating-and-sharing-a-circuitpython-library/sharing-our-docs-on-readthedocs#sphinx-5-1>`_.

Contributing
============

Contributions are welcome! Please read our `Code of Conduct
<https://github.com/adafruit/Adafruit_CircuitPython_S35710/blob/HEAD/CODE_OF_CONDUCT.md>`_
before contributing to help this project stay welcoming.
