cmake_minimum_required(VERSION 3.7)
project(Filters)

include(filters.cmake)

add_definitions(-fpic)

SET(XVIDDEC_SRC
        ${CMAKE_CURRENT_SOURCE_DIR}/dec_xvid.c
)

SET(XVIDDEC_INCLUDE
        ${CMAKE_CURRENT_SOURCE_DIR}/include
)

SET(XVIDDEC_LIB
        ${CMAKE_CURRENT_SOURCE_DIR}/lib/libxvidcore.a
)

add_filter(libxvid
        "${XVIDDEC_SRC}"
        "${XVIDDEC_LIB}"
        []
        GPAC_HAS_XVID
        "${XVIDDEC_INCLUDE}"
        ""
        "1")