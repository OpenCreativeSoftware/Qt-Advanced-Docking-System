cmake_minimum_required(VERSION 3.16)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
if (POLICY CMP0091)
  cmake_policy(SET CMP0091 NEW)
endif (POLICY CMP0091)

set(ADS_VERSION "4.4.0")
string(REGEX MATCHALL "[\.]" VERSION_DOT_MATCHES ${ADS_VERSION})
list(LENGTH VERSION_DOT_MATCHES VERSION_DOT_COUNT)
if(VERSION_DOT_COUNT EQUAL 2)
    set(VERSION_SHORT ${ADS_VERSION})
else()
    message(FATAL_ERROR "ADS_VERSION must be in major.minor.patch format, e.g. 3.8.1. Got ${ADS_VERSION}")
endif()

project(QtADS LANGUAGES CXX VERSION ${VERSION_SHORT})


if("${CMAKE_SIZEOF_VOID_P}" STREQUAL "4")
    set(ads_PlatformDir "x86")
else()
    set(ads_PlatformDir "x64")
endif()

add_subdirectory(src)

