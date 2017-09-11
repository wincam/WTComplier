list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_LIST_DIR}/cmake")

cmake_minimum_required (VERSION 2.6)
project (wtttest)

# add the executable
add_executable(wtttest src/wttest.cpp)

FIND_PACKAGE( Wt REQUIRED )
INCLUDE_DIRECTORIES( ${Wt_INCLUDE_DIR} )
TARGET_LINK_LIBRARIES( wtttest
  ${Wt_DEBUG_LIBRARY}        # or {Wt_LIBRARY}
  ${Wt_HTTP_DEBUG_LIBRARY}   # or {Wt_HTTP_LIBRARY}
  ${Wt_EXT_DEBUG_LIBRARY}    # or {Wt_EXT_LIBRARY}
  )


