
=====
 C++
=====

--------------
 Build system
--------------

The meta build system is *cmake* with the respecitve `CMakeLists.txt`.
The basic `CMakeLists.txt` is provided by the *copier* template and should be adapted accordingly.

The targetted C++ standard is *C++20*, as recorded in the `CMakeLists.txt`.
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
