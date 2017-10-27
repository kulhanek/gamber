# ==============================================================================
# GAmber CMake File
# ==============================================================================

CMAKE_MINIMUM_REQUIRED(VERSION 2.8 FATAL_ERROR)
#SET(CMAKE_VERBOSE_MAKEFILE ON)

# ==============================================================================
# project setup ----------------------------------------------------------------
# ==============================================================================

# dynutil major version
SET(GAMBER_MAJOR_VERSION 2)

# dynutil minor version
FIND_PROGRAM(GIT_EXECUTABLE git
                        DOC "git command line client")

MACRO(Git_GET_REVISION variable)
                        EXECUTE_PROCESS(COMMAND ${GIT_EXECUTABLE} rev-list --count HEAD
			  OUTPUT_VARIABLE ${variable}
			  OUTPUT_STRIP_TRAILING_WHITESPACE)
ENDMACRO(Git_GET_REVISION)

MACRO(Git_GET_HASH variable)
                        EXECUTE_PROCESS(COMMAND ${GIT_EXECUTABLE} rev-parse --short HEAD
                          OUTPUT_VARIABLE ${variable}
                          OUTPUT_STRIP_TRAILING_WHITESPACE)
ENDMACRO(Git_GET_HASH)

Git_GET_REVISION(GAMBER_MINOR_VERSION)
Git_GET_HASH(GAMBER_HASH_VERSION)

SET(GAMBER_ALL_VERSION ${GAMBER_MAJOR_VERSION}.${GAMBER_MINOR_VERSION}.${GAMBER_HASH_VERSION})

MESSAGE(STATUS "GAmber version is ${GAMBER_ALL_VERSION}")

# ==============================================================================
# install files ----------------------------------------------------------------
# ==============================================================================

ADD_SUBDIRECTORY(bin)

