CMAKE_MINIMUM_REQUIRED(VERSION 2.8)

PROJECT(lua)

# the following two variables are defined for the use of packages 
# that wish to link or compile against lua
SET(LUA_INCLUDE_DIRS
	"${CMAKE_CURRENT_SOURCE_DIR}/src"
)

CONFIGURE_FILE(${CMAKE_SOURCE_DIR}/pkg-config/lua5.2.pc.in ${CMAKE_BINARY_DIR}/lua5.2.pc)
INSTALL(FILES ${CMAKE_BINARY_DIR}/lua5.2.pc DESTINATION lib/pkg-config)

SET(LUA_LIBRARIES lua)

SET(BINARY_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin)
SET(LIBRARY_OUTPUT_PATH ${PROJECT_BINARY_DIR})

ADD_SUBDIRECTORY(src)
