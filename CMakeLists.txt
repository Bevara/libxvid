cmake_minimum_required(VERSION 3.7)
project(Filters)

include(filters.cmake)

set(CMAKE_BUILD_TYPE Release)
set(CMAKE_CXX_FLAGS "-O3 -Wall -Wextra")
set(CMAKE_C_FLAGS "-O3 -Wall -Wextra")

add_definitions(-fpic)

SET(XVIDDEC_SRC
        ${CMAKE_CURRENT_SOURCE_DIR}/dec_xvid.c
        ${CMAKE_CURRENT_SOURCE_DIR}/reframe_mpgvid.c
        ${CMAKE_CURRENT_SOURCE_DIR}/av_parsers.c
        ${CMAKE_CURRENT_SOURCE_DIR}/bitstream.c
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
