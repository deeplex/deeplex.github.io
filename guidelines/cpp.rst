
=====
 C++
=====

--------------
 Build system
--------------

The meta build system is ``CMake`` with the respective ``CMakeLists.txt``.
The basic ``CMakeLists.txt`` is provided by the ``copier`` template and should be adapted accordingly.

The C++ target standard is ``C++20``, as configured in the ``CMakeLists.txt``. The ``copier`` template provides vcpkg triplets which enforces this for dependencies.

-----------------
 Package manager
-----------------

The package manager of choice is `vcpkg <https://vcpkg.io>`_.

``vcpkg`` is installed by cloning the `vcpkg repository <https://github.com/microsoft/vcpkg>`_. Create an environment variable with variable name ``VCPKG_ROOT`` and variable value ``path/to/vcpkg``.

The ``copier`` template provides a ``vcpkg.json`` manifest and a ``vcpkg-configuration.json``. The vcpkg manifest contains rudimentary information about your project.
List your dependencies in the ``vcpkg.json`` ``dependencies`` array. To install dependencies run ``CMake``. During the ``CMake`` configure step ``vcpkg`` will be invoked to provide them. Look out for a note how to add the missing dependencies to your targets within the ``CMakeLists.txt``.

``vcpkg`` is hooked to ``CMake`` by a non intrusive toolchain file:

::

    if(DEFINED ENV{VCPKG_ROOT} AND NOT DEFINED CMAKE_TOOLCHAIN_FILE)
    set(CMAKE_TOOLCHAIN_FILE "$ENV{VCPKG_ROOT}/scripts/buildsystems/vcpkg.cmake"
            CACHE STRING "")
    endif()

If you need to use an actual toolchain file, you can provide it via `VCPKG_CHAINLOAD_TOOLCHAIN_FILE <https://vcpkg.io/en/docs/users/buildsystems/cmake-integration.html#using-multiple-toolchain-files>`

------------
 Formatting
------------

The formatting is determined by the ``.clang-format``, included in respective ``copier`` templates.

.. warning::

    Changes are prohibited. Violation implies termination.

-------------
 Compilation
-------------

Before attempting to compile a project make sure to setup the
`package manager <Package manager_>`_ and `build system <Build system_>`_.

The project needs to be configured with ``CMake`` first. This can either be done
with the provided presets or manually (in which case I recommend `ccmake <https://cmake.org/cmake/help/latest/manual/ccmake.1.html>`_ or `cmake-gui <https://cmake.org/cmake/help/latest/manual/cmake-gui.1.html>`_). The presets live within :code:`CMakePresets.json` and can be supplemented with a :code:`CMakeUserPresets.json`.
The :code:`CMakePresets.json` is included in all copier templates concerning C++.
The presets can be used via the commandline like so

::

    cd $project-root
    cmake --list-presets # lists all available presets
    cmake --preset=x64-linux-gcc-debug . # configures the current project with the given prefix
    cmake --build ./build/x64-linux-gcc-debug # builds the previously configured project

However, IDEs like Visual Studio and Visual Studio Code have integrated support
for :code:`CMakePresets.json` (see `VS docs <https://docs.microsoft.com/en-us/cpp/build/cmake-presets-vs?view=msvc-170>`_, `VS Code docs <https://github.com/microsoft/vscode-cmake-tools/blob/main/docs/cmake-presets.md>`_
and `this blog post <https://devblogs.microsoft.com/cppblog/cmake-presets-integration-in-visual-studio-and-visual-studio-code/>`_).

.. warning:: Note that if you do use the commandline, it is your responsibility
    to ensure that the target compiler is reachable via :code:`$PATH`. On Windows
    you probably have to run these commands from a Visual Studio command prompt.


######################
 ESP32 (Windows only)
######################

At first make sure to use the `correct template <../copier-cpp-esp>`_.

Clone `this repository <https://github.com/espressif/esp-idf>`_.
Call the ``install.bat`` file to install all requirements.

.. note:: It is recommended to create a conda environment. Use ``Python=3.9``.

Call the ``export.ps1`` to add all necessary paths to your current session.

Call ``idf.py set-target esp32`` if the target is wrong.

To compile your programm call ``idf.py build`` from the root of your project to build the project.
To flash your program including the bootloader to the ``esp32`` call ``idf.py flash``.
If you only want to flash your program call ``idf.py app-flash``.

.. note:: ``flash`` and ``app-flash`` will build your project. You do not have to call both commands every time.

You can also call ``idf.py app-flash monitor`` to get terminal output of your application.
