
=====
 C++
=====

--------------
 Build system
--------------

The meta build system is *cmake* with the respecitve `CMakeLists.txt`.
The basic `CMakeLists.txt` is provided by the *copier* template and should be adapted accordingly.

The targetted C++ standard is *C++20*, as configured in the `CMakeLists.txt`.
Respective triplets for dependencies to respect that are included in the *copier* template.

-----------------
 Package manager
-----------------

The package manager of choice is `vcpkg <https://vcpkg.io>`_.
*vcpkg* is installed by cloning the `vcpkg repository <https://github.com/microsoft/vcpkg>`_.
Create an environment variable with variable name `VCPKG_ROOT` and variable value `path/to/vcpkg`.

The *copier* template provides a `vcpkg.json` and a `vcpkg-configuration.json`.
The `vcpkg.json` contains rudimentary information about your project.
Dependencies are in the `dependencies` array.
To install dependencies run *cmake* and look out for a note how to add the missing dependencies to the `CMakeLists.txt`.
The installation is taken care of by a referenced non-intrusive toolchain-file:

::

    if(DEFINED ENV{VCPKG_ROOT} AND NOT DEFINED CMAKE_TOOLCHAIN_FILE)
    set(CMAKE_TOOLCHAIN_FILE "$ENV{VCPKG_ROOT}/scripts/buildsystems/vcpkg.cmake"
            CACHE STRING "")
    endif()

------------
 Formatting
------------

The formatting is determined by the `.clang-format.json`, included in respective *copier* templates.
Changes are prohibited. Violation implies termination.

-------------
 Compilation
-------------

Before compilation make sure to setup the `package manager <Package manager_>`_ and `build system <Build system_>`_.

#########
 Windows
#########

TODO

#######
 Linux
#######

TODO

######################
 ESP32 (Windows only)
######################

At first make sure to use the `correct template <../copier-cpp-esp>`_.

Clone `this repository <https://github.com/espressif/esp-idf>`_.
Call the `install.bat` file to install all requirements.

.. note:: It is recommended to create a conda environment. Use Python=3.9.

Call the `export.ps1` to add all necessary paths to your current session.

Call `idf.py set-target esp32` if the target is wrong.

To compile your programm call `idf.py build` from the root of your project to build the project.
To flash your program including the bootloader to the *esp32* call `idf.py flash`.
If you only want to flash your program call `idf.py app-flash`.

.. note:: `flash` and `app-flash` will build your project. You do not have to call both commands every time.

You can also call `idf.py app-flash monitor` to get terminal output of your application.

