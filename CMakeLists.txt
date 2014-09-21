CMAKE_MINIMUM_REQUIRED(VERSION 2.8.11)

project(libscl C)

include(CMakeStdOpt)

set(HEADERS
	include/libscl/SCL_symbol.h
	include/libscl/SCL.h
	include/libscl/SCL_queuebuf.h
	include/libscl/SCL_stackbuf.h
	include/libscl/SCL_list.h
	include/libscl/SCL_vector.h
	include/libscl/SCL_hash.h
	include/libscl/SCL_map.h
	include/libscl/SCL_tree.h
	)

set(SOURCES
	src/symbol.c
	src/queuebuf.c
	src/stackbuf.c
	src/list.c
	src/vector.c
	src/hash.c
	src/map.c
	src/tree.c
	)

add_library(libscl SHARED ${SOURCES} ${HEADERS})

target_compile_definitions(libscl PUBLIC C99 _unix)

target_compile_options(libscl PRIVATE -Wl,-no-undefined)

target_include_directories(libscl
	PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include
	PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/include/libscl
	)


install(TARGETS libscl DESTINATION ${CMAKE_INSTALL_PREFIX}/lib)
