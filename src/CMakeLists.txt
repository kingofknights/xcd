project(xcd C)

set(HEADERS
	    deflate.h
		inffixed.h
		inflate.h
		inftrees.h
		libxcd.h
		trees.h
		zconf.h
		zlib.h
		zutil.h
		inffast.h
)

set(SOURCES
	    adler32.c
		compress.c
		inffast.c
		zutil.c
		deflate.c
		infback.c
		inflate.c
		inftrees.c
		libxcd.c
		trees.c
		uncompr.c
)

add_library(xcd
	${HEADERS}
	${SOURCES}
)
