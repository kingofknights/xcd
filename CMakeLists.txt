cmake_minimum_required(VERSION 3.14)

project(xcd
	    VERSION 1.0
		LANGUAGES C
	    )

set(HEADER
	 include/xcd/deflate.h
	 include/xcd/inffast.h
	 include/xcd/inffixed.h
	 include/xcd/inflate.h
	 include/xcd/inftrees.h
	 include/xcd/libxcd.h
	 include/xcd/trees.h
	 include/xcd/zconf.h
	 include/xcd/zlib.h
	 include/xcd/zutil.h
 )

set(SOURCE
	src/adler32.c
	src/compress.c
	src/deflate.c
	src/infback.c
	src/inffast.c
	src/inflate.c
	src/inftrees.c
	src/libxcd.c
	src/trees.c
	src/uncompr.c
	src/zutil.c
)

add_library(${PROJECT_NAME} ${HEADER} ${SOURCE})
target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include/xcd)
