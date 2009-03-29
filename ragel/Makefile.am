
INCLUDES = -I../aapl

bin_PROGRAMS = ragel

ragel_SOURCES = \
	main.cpp parsetree.cpp parsedata.cpp fsmstate.cpp fsmbase.cpp \
	fsmattach.cpp fsmmin.cpp fsmgraph.cpp fsmap.cpp rlscan.cpp rlparse.cpp \
	inputdata.cpp common.cpp redfsm.cpp gendata.cpp cdcodegen.cpp \
	cdtable.cpp cdftable.cpp cdflat.cpp cdfflat.cpp cdgoto.cpp cdfgoto.cpp \
	cdipgoto.cpp cdsplit.cpp javacodegen.cpp rubycodegen.cpp rubytable.cpp \
	rubyftable.cpp rubyflat.cpp rubyfflat.cpp rbxgoto.cpp cscodegen.cpp \
	cstable.cpp csftable.cpp csflat.cpp csfflat.cpp csgoto.cpp csfgoto.cpp \
	csipgoto.cpp cssplit.cpp dotcodegen.cpp xmlcodegen.cpp

BUILT_SOURCES = \
	rlscan.cpp rlparse.h rlparse.cpp version.h

CLEANFILES = \
	rlscan.cpp rlparse.h rlparse.cpp

# Get the version info.
include ../version.mk

version.h: ../version.mk
	echo '#define VERSION "$(VERSION)"' > version.h
	echo '#define PUBDATE "$(PUBDATE)"' >> version.h
	echo '#define PREFIX "$(prefix)"' >> version.h

if BUILD_PARSERS

rlparse.h: rlparse.kh
	kelbt -o $@ $<

rlparse.cpp: rlparse.kl rlparse.kh
	kelbt -o $@ $<

# This dependency comes from the import of the parser defines
# into the scanner.
rlscan.cpp: rlparse.h

rlscan.cpp: rlscan.rl
	ragel -G2 -o $@ $<

endif
