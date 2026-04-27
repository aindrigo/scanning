project(scanning VERSION 0.0.0 LANGUAGES CXX)

set(SCANNING_SOURCE_DIR source/)

set(SCANNING_SOURCES )

if (LINUX)
    set(SCANNING_SOURCES ${SCANNING_SOURCE_DIR}/linux/symbolfinder.cpp)
elseif(WIN32)
    set(SCANNING_SOURCES ${SCANNING_SOURCE_DIR}/windows/symbolfinder.cpp)
elseif(APPLE)
    set(SCANNING_SOURCES ${SCANNING_SOURCE_DIR}/macosx/symbolfinder.cpp)
endif()

add_library(scanning STATIC ${SCANNING_SOURCES})
set_target_properties(scanning PROPERTIES POSITION_INDEPENDENT_CODE ON)
target_include_directories(scanning PUBLIC include)