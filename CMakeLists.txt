# Usage:
#         cmake -S src -B builds/release
#         cmake --build builds/release
# The first call caches settings in the build directory and reads
# them from the cache on subsequent builds. If you want to change the
# settings of some options, do _not_ change the CMakeLists.txt files.
# Instead, create a new build directory, pass -DMY_OPTION=my_value to
# cmake. Alternatively, you can use a cmake GUI like ccmake to edit
# the cache.
#
# Two build targets are defined:
#
# * release (default)
#      -O3 optimisation, debugging symbols, assertions inactive
# * debug
#      -O3 optimisation, full debugging information, assertions active
#
# In all build targets, we overwrite the default configuration to
# include "-g", allow cross compilation and switch to pedantic error
# reporting.
#
# You can change the build target, by adding the parameter
#   -DCMAKE_BUILD_TYPE=type
# to the cmake call.

cmake_minimum_required(VERSION 3.16)

project(fast-downward
    DESCRIPTION "Fast Downward is a domain-independent classical planning system."
    HOMEPAGE_URL https://www.fast-downward.org/)

# Add planner components.

# Add search component as a subproject.
add_subdirectory(src/search)
