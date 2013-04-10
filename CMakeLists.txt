CMAKE_MINIMUM_REQUIRED(VERSION 2.8)

PROJECT(lua)

# the following two variables are defined for the use of packages 
# that wish to link or compile against lua
SET(LUA_INCLUDE_DIRS
	"${CMAKE_CURRENT_SOURCE_DIR}/src"
)

SET(LUA_LIBRARIES lua)

SET(BINARY_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin)
SET(LIBRARY_OUTPUT_PATH ${PROJECT_BINARY_DIR})

ADD_SUBDIRECTORY(src)
