cmake_minimum_required (VERSION 2.6)

project (expat)

set(SOURCES
	xmlparse.c
	xmlrole.c
	xmltok.c
	xmltok_impl.c
	xmltok_ns.c
)

set(HEADERS
	ascii.h
	asciitab.h
	expat.h
	expat_external.h
	iasciitab.h
	internal.h
	latin1tab.h
	nametab.h
	utf8tab.h
	winconfig.h
	xmlrole.h
	xmltok.h
	xmltok_impl.h
)


if (MSVC)
	source_group("Sources" FILES ${SOURCE})
	source_group("Headers" FILES ${HEADERS})
endif()


add_library(expat STATIC ${SOURCES} ${HEADERS})

# When a project links to expat, make expat.h directly available
target_include_directories(expat SYSTEM
	INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}
)
