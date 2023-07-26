
=====
 C++
=====

--------------
 Buildsystem
--------------

The meta buildsystem is ``CMake`` with the respective ``CMakeLists.txt``.
The basic ``CMakeLists.txt`` is provided by the ``copier`` template and should be adapted accordingly.

The C++ target standard is ``C++20``, as configured in the ``CMakeLists.txt``. The ``copier`` template provides vcpkg triplets which enforces this for dependencies.

-----------------
 Package Manager
-----------------

The package manager of choice is `vcpkg <https://vcpkg.io>`_.

``vcpkg`` is installed by cloning the `vcpkg repository <https://github.com/microsoft/vcpkg>`_. Create an environment variable with variable name ``VCPKG_ROOT`` and variable value ``path/to/vcpkg``.

The ``copier`` template provides a ``vcpkg.json`` manifest and a ``vcpkg-configuration.json``. The vcpkg manifest contains rudimentary information about your project.
List your dependencies in the ``vcpkg.json`` ``dependencies`` array. To install dependencies run ``CMake``. During the ``CMake`` configure step ``vcpkg`` will be invoked to provide them. Look out for a note how to add the missing dependencies to your targets within the ``CMakeLists.txt``.

.. note::

    You can search available dependencies on `vcpkg.link <https://vcpkg.link>`_ (recommended) or the official `vcpkg index <https://vcpkg.io/en/packages.html>`_.

``vcpkg`` is hooked to ``CMake`` by a non-intrusive toolchain file:

::

    if(DEFINED ENV{VCPKG_ROOT} AND NOT DEFINED CMAKE_TOOLCHAIN_FILE)
    set(CMAKE_TOOLCHAIN_FILE "$ENV{VCPKG_ROOT}/scripts/buildsystems/vcpkg.cmake"
            CACHE STRING "")
    endif()

If you need to use an actual toolchain file, you can provide it via `VCPKG_CHAINLOAD_TOOLCHAIN_FILE <https://vcpkg.io/en/docs/users/buildsystems/cmake-integration.html#using-multiple-toolchain-files>`_.

-------------------
 Source Formatting
-------------------

The formatting is determined by the ``.clang-format``, included in respective ``copier`` templates.

.. warning::

    Changes are prohibited and the CI enforces compliance.
    Violation implies Pull Request rejection.

-------------
 Compilation
-------------

Before attempting to compile a project make sure to setup the
`package manager <Package Manager_>`_ and `buildsystem <Buildsystem_>`_.

The project needs to be configured with ``CMake`` first.
This can either be done with the provided `presets <https://cmake.org/cmake/help/latest/manual/cmake-presets.7.html>`_ or manually (in which case I recommend using `ccmake <https://cmake.org/cmake/help/latest/manual/ccmake.1.html>`_ or `cmake-gui <https://cmake.org/cmake/help/latest/manual/cmake-gui.1.html>`_). The presets live within ``CMakePresets.json`` and can be supplemented with a ``CMakeUserPresets.json``.
The ``CMakePresets.json`` is included in all copier templates concerning C++.
The presets can be used via the commandline like so

::

    cd $project-root
    # lists all available presets
    cmake --list-presets
    # configures the current project with the given preset
    cmake --preset=x64-linux-gcc
    # builds the previously configured project
    cmake --build --preset=x64-linux-gcc
    # usually there exists a release build-preset, too
    cmake --build --preset=x64-linux-gcc-release

However, IDEs like Visual Studio and Visual Studio Code have integrated support
for ``CMakePresets.json`` (see `VS docs <https://docs.microsoft.com/en-us/cpp/build/cmake-presets-vs?view=msvc-170>`_, `VS Code docs <https://github.com/microsoft/vscode-cmake-tools/blob/main/docs/cmake-presets.md>`_
and `this blog post <https://devblogs.microsoft.com/cppblog/cmake-presets-integration-in-visual-studio-and-visual-studio-code/>`_).

.. warning::

    Note that if you do use the commandline, it is your responsibility
    to ensure that the target compiler is reachable via ``$PATH``. On Windows you probably have to run these commands from a Visual Studio command prompt.

.. toctree::
    :hidden:

    cpp/esp32
