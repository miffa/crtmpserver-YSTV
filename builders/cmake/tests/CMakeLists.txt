cmake_minimum_required(VERSION 2.6.3)
PROJECT(tests)

#make the list with all the source files
FILE(GLOB_RECURSE SOURCES "${CRTMPSERVER_SOURCES_ROOT}/tests/src/*.cpp" )

INCLUDE_DIRECTORIES(
	${OPENSSL_INCLUDE_PATH}
	${LUA_INCLUDE_PATH}
	${CRTMPSERVER_SOURCES_ROOT}/common/include
	${CRTMPSERVER_SOURCES_ROOT}/thelib/include
	${CRTMPSERVER_SOURCES_ROOT}/tests/include
)

ADD_EXECUTABLE(${PROJECT_NAME}  ${SOURCES})
TARGET_LINK_LIBRARIES(${PROJECT_NAME} 
	common 
	thelib 
	${SOCKET_LIB} 
	${OPENSSL_LIBRARY_PATH} 
	${CRYPTO_LIBRARY_PATH} 
	${Z_LIBRARY_PATH}
	${TINYXML_LIBRARY_PATH} 
	${LUA_LIBRARY_PATH}
	${DL_LIBRARY_PATH}
)
ADD_PRECOMPILED_HEADER(${PROJECT_NAME} "${CRTMPSERVER_SOURCES_ROOT}/common/include/common.h")

