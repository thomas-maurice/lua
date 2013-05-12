IF(WIN32)
  SET(LIBDL "")
ELSE()
  SET(LIBDL dl)
ENDIF()

# define the lua core source files
SET(LUA_CORE_SRCS lapi.c lcode.c lctype.c ldebug.c ldo.c ldump.c lfunc.c lgc.c llex.c
	lmem.c lobject.c lopcodes.c lparser.c lstate.c lstring.c ltable.c
	ltm.c lundump.c lvm.c lzio.c
)

# define the lua lib source files
SET(LUA_LIB_SRCS lauxlib.c lbaselib.c lbitlib.c lcorolib.c ldblib.c liolib.c
	lmathlib.c loslib.c lstrlib.c ltablib.c loadlib.c linit.c
)

# create the library
ADD_LIBRARY(
	lua
	${LUA_LIB_SRCS}
	${LUA_CORE_SRCS}
)

# create the lue executable and link it to the lib
ADD_EXECUTABLE(
	luaexec
	lua.c
)

TARGET_LINK_LIBRARIES(
	luaexec
	lua
	m
)

# name the executable lua just like the library
SET_TARGET_PROPERTIES(luaexec
	PROPERTIES
	OUTPUT_NAME lua
)

# create the luac thing (I have no clue) and link it
ADD_EXECUTABLE(
	luac
	luac.c
)

TARGET_LINK_LIBRARIES(
	luac
	lua
	m
  ${LIBDL}
)

INSTALL(TARGETS luaexec luac DESTINATION bin)
INSTALL(TARGETS lua DESTINATION lib EXPORT lua-targets)
INSTALL(FILES lauxlib.h luaconf.h lua.h lua.hpp lualib.h DESTINATION include)
