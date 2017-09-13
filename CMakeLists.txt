
# This is the cmake file. It describes how to build our app
# The documentation for how to build these can be found here:
#   http://www.cmake.org/cmake/help/cmake-2-8-docs.html

# CMake likes us to put this here in case someone tries to read this file with an older version of cmake
cmake_minimum_required(VERSION 2.8) # http://www.cmake.org/cmake/help/cmake-2-8-docs.html#command:cmake_minimum_required

# Sets the name of the project. Additionally this sets the variables <projectName>_BINARY_DIR and <projectName>_SOURCE_DIR to the respective values.
project ("test in wt++")      # http://www.cmake.org/cmake/help/cmake-2-8-docs.html#command:project
#set(CMAKE_VERBOSE_MAKEFILE ON)

# Other Libraries
find_package(Boost COMPONENTS program_options)
find_library(wt wt)
find_library(wthttp wthttp)

# This tells cmake that we want to create an executable called 'wtttest' and the source files are in the src directory
# add the executable
file(GLOB_RECURSE wttest_SRC
${PROJECT_SOURCE_DIR}/src/*.C
${PROJECT_SOURCE_DIR}/src/*.h
${PROJECT_SOURCE_DIR}/src/*.cpp
${PROJECT_SOURCE_DIR}/src/*.cxx

)
add_executable(wtttest ${wttest_SRC})
set_target_properties(wtttest PROPERTIES LINKER_LANGUAGE CXX)

target_link_libraries(wtttest
          ${Boost_LIBRARIES}
		      wt wthttp wtdbosqlite3 wtdbo)

