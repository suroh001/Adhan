PROJECT(adhan)
SET(CMAKE_PROJECT_NAME adhan)

CMAKE_MINIMUM_REQUIRED(VERSION 3.5)

# Mode debug par defaut
IF("${CMAKE_BUILD_TYPE}" STREQUAL "")
    SET(CMAKE_BUILD_TYPE "DEBUG")
    ADD_DEFINITIONS(-DNOSYSLOG=1)
ENDIF("${CMAKE_BUILD_TYPE}" STREQUAL "")

IF("${CMAKE_BUILD_TYPE}" STREQUAL "DEBUG")
    SET(FORMAT_CODE style)
ENDIF("${CMAKE_BUILD_TYPE}" STREQUAL "DEBUG")



SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=gnu++11")
SET(CMAKE_C_FLAGS_RELEASE "-O2 -DNDEBUG")
SET(CMAKE_CXX_FLAGS_RELEASE "-O2 -DNDEBUG")
SET(CMAKE_C_FLAGS_DEBUG " -DDEBUG ")
SET(CMAKE_CXX_FLAGS_DEBUG " -DDEBUG")
SET(CPACK_SOURCE_IGNORE_FILES "/build.*/;/deb/;/CVS/;/\\\\.svn/;/\\\\.git/;\\\\.swp$;/*~;tags;\\\\.pcs$;")

SET(MAJOR 1)
SET(MINOR 0)
SET(PATCH 1)
SET(VERSION ${MAJOR}.${MINOR}.${PATCH})

#ADD_DEFINITIONS("-fgnu89-inline")

ADD_DEFINITIONS("-Wall -ggdb3  -Wfatal-errors")
ADD_DEFINITIONS("-fno-builtin-malloc -fno-builtin-realloc -fno-builtin-calloc -fno-builtin-free -fno-strict-aliasing -fno-omit-frame-pointer")
ADD_DEFINITIONS("-fstrict-aliasing")

#INCLUDE_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR})
#INCLUDE_DIRECTORIES(include)

# Executable for bidviser
#ADD_EXECUTABLE(${CMAKE_PROJECT_NAME} ${ADAHN_SRC})
#ADD_LIBRARY(${CMAKE_PROJECT_NAME} STATIC ${SOURCE_FILES})
  #TARGET_LINK_LIBRARIES(${CMAKE_PROJECT_NAME}  m  )


add_subdirectory(src)
add_subdirectory(test)
#add_subdirectory(it)
