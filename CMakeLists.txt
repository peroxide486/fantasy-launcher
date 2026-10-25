cmake_minimum_required(VERSION 3.15)
project(fantasy_launcher)

set(CMAKE_CXX_STANDARD 17)

set(FLTK_BUILD_TEST OFF CACHE BOOL " " FORCE)
set(FLTK_BUILD_FLUID OFF CACHE BOOL " " FORCE) 
set(FLTK_BUILD_FLTK_OPTIONS OFF CACHE BOOL " " FORCE)

include(FetchContent)

FetchContent_Declare(
    fltk
    GIT_REPOSITORY https://github.com/fltk/fltk.git
    GIT_TAG        release-1.4.5
    GIT_SHALLOW    TRUE
)

FetchContent_MakeAvailable(fltk)

file(GLOB_RECURSE SOURCES CONFIGURE_DEPENDS "src/*.cpp" "src/*.c" "src/*.cxx")
add_executable(fantasy_launcher ${SOURCES})
target_link_libraries(fantasy_launcher PRIVATE fltk::fltk)
