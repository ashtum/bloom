#
# Copyright (c) 2025 Mohammad Nejati
#
# Distributed under the Boost Software License, Version 1.0. (See accompanying
# file LICENSE_1_0.txt or copy at http://www.boost.org/LICENSE_1_0.txt)
#
# See https://www.boost.org/libs/bloom for library home page.
#

if(NOT TARGET tests)
    add_custom_target(tests)
    set_property(TARGET tests PROPERTY FOLDER Dependencies)
endif()

macro (add_test_executable name)
    add_executable(boost_bloom_${name} ${name}.cpp)
    if (MSVC)
        target_compile_definitions(boost_bloom_${name} PRIVATE -D_SCL_SECURE_NO_WARNINGS)
    endif ()
    target_link_libraries(boost_bloom_${name} PRIVATE boost_bloom)
    set_target_properties(boost_bloom_${name} PROPERTIES FOLDER "tests")
    add_test(NAME boost_bloom_${name} COMMAND boost_bloom_${name})
    add_dependencies(tests boost_bloom_${name})
endmacro ()

add_test_executable(test_array)
add_test_executable(test_capacity)
add_test_executable(test_combination)
add_test_executable(test_comparison)
add_test_executable(test_construction)
add_test_executable(test_fpr)
add_test_executable(test_insertion)
