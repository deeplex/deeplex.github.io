

######################
 ESP32 (Windows only)
######################

At first make sure to use the `correct template <../copier-cpp-esp>`_.

Clone `this repository <https://github.com/espressif/esp-idf>`_.
Call the ``install.bat`` file to install all requirements.

.. note::

    It is recommended to create a conda environment. Use ``Python=3.9``.

Call the ``export.ps1`` to add all necessary paths to your current session.

Call ``idf.py set-target esp32`` if the target is wrong.

To compile your programm call ``idf.py build`` from the root of your project to build the project.
To flash your program including the bootloader to the ``esp32`` call ``idf.py flash``.
If you only want to flash your program call ``idf.py app-flash``.

.. note::

    ``flash`` and ``app-flash`` will build your project. You do not have to call both commands every time.

You can also call ``idf.py app-flash monitor`` to get terminal output of your application.

