cmake_minimum_required( VERSION 3.1 )

project( compression_service )

#----------------------------------------------------------------------
# Options:
#
# Standart options:
#   CMAKE_BUILD_TYPE     = [Release]/Debug
#
#----------------------------------------------------------------------

include_directories (${CMAKE_CURRENT_SOURCE_DIR}/include )

#----------------------------------------------------------------------
# Build type
# default CMAKE_BUILD_TYPE = Release
#----------------------------------------------------------------------

string( TOLOWER "${CMAKE_BUILD_TYPE}" STR_TOLOWER )

if( STR_TOLOWER STREQUAL debug )
    set( CMAKE_BUILD_TYPE Debug )
else()
    set( CMAKE_BUILD_TYPE Release )
endif()

#----------------------------------------------------------------------
# Flags of build
#----------------------------------------------------------------------

set ( CMAKE_CXX_STANDARD 11 )
set ( CMAKE_CXX_STANDARD_REQUIRED ON )

set( CMAKE_CXX_FLAGS_DEBUG    " -O0 -g3 -Wall" )
set( CMAKE_CXX_FLAGS_RELEASE  " -O2 -g  -Wall" )

#----------------------------------------------------------------------
# Building gameoflife
#----------------------------------------------------------------------

set( HEADERS
)
set( SOURCES

)

add_library( compression_service_static STATIC ${HEADERS} ${SOURCES} )
add_executable( compression_service "src/compression_service.cpp" )
target_link_libraries( compression_service compression_service_static )