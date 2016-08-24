cmake_minimum_required(VERSION 2.8)

# set project name from current directory
set( TARGET cedrus)
project( ${TARGET} )

set(BUILD_SHARED_LIBS YES)

SET(${TARGET}_HEADERS

)

SET(${TARGET}_SOURCES 
	cedrus.c
    cedrus_mem_ve.c
    cedrus_mem_ion.c
    #cedrus_mem_ump.c
)

INCLUDE_DIRECTORIES(
    ./include/  
)


add_definitions(-DLIBDIR=\"/usr/local/lib\")

#MESSAGE ("@${TARGET} -- ${ENV{LIBDIR}")

set (CMAKE_C_FLAGS ${CMAKE_C_FLAGS} 
    "-fpic -fvisibility=hidden -Wall -Wextra -O3"
)
set (CMAKE_CXX_FLAGS ${CMAKE_CXX_FLAGS} 
    "-fpic -fvisibility=hidden -Wall -Wextra -O3"
)

ADD_LIBRARY( ${TARGET} ${${TARGET}_SOURCES} ${${TARGET}_HEADERS} )

TARGET_LINK_LIBRARIES( ${TARGET}   )

# add the install targets
install (TARGETS ${TARGET} DESTINATION bin)
install (FILES "${${TARGET}_SOURCE_DIR}/cedrus.h"        
         DESTINATION include/cedrus)
