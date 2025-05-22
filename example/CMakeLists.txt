#
# Copyright (c) 2025 Mohammad Nejati
#
# Distributed under the Boost Software License, Version 1.0. (See accompanying
# file LICENSE_1_0.txt or copy at http://www.boost.org/LICENSE_1_0.txt)
#
# See https://www.boost.org/libs/bloom for library home page.
#

macro (add_example_executable name)
    add_executable(${name} ${name}.cpp)
    target_link_libraries(${name} PRIVATE boost_bloom boost_uuid)
    set_target_properties(${name} PROPERTIES FOLDER "example")
endmacro ()

add_example_executable(basic)
if (CMAKE_CXX_STANDARD GREATER_EQUAL 17)
    add_example_executable(genome)
endif ()
add_example_executable(serialization)
