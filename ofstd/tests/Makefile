#
#	Makefile for ofstd/tests
#



SHELL = /bin/sh
VPATH = ../include:../../config/include
srcdir = .
top_srcdir = ..
configdir = ../../config

include $(configdir)/Makefile.def

LOCALINCLUDES = -I$(top_srcdir)/include
LIBDIRS = -L$(top_srcdir)/libsrc
LOCALLIBS = -lofstd
LOCALTRASH = *.out

objs = tststack.o tstlist.o tlist.o tstring.o tstthred.o tofstd.o tofdatim.o \
       tstatof.o tstftoa.o toffile.o tmap.o tvec.o
progs = tststack tstlist tlist tstring tstthred tofstd tofdatim tstatof tstftoa \
        toffile tmap tvec


all: $(progs)

tststack: tststack.o
	$(CXX) $(CXXFLAGS) $(LDFLAGS) $(LIBDIRS) -o $@ $@.o $(LOCALLIBS) $(LIBS)

tstlist: tstlist.o
	$(CXX) $(CXXFLAGS) $(LDFLAGS) $(LIBDIRS) -o $@ $@.o $(LOCALLIBS) $(LIBS)

tlist: tlist.o
	$(CXX) $(CXXFLAGS) $(LDFLAGS) $(LIBDIRS) -o $@ $@.o $(LOCALLIBS) $(LIBS)

tmap: tmap.o
	$(CXX) $(CXXFLAGS) $(LDFLAGS) $(LIBDIRS) -o $@ $@.o $(LOCALLIBS) $(LIBS)

tvec: tvec.o
	$(CXX) $(CXXFLAGS) $(LDFLAGS) $(LIBDIRS) -o $@ $@.o $(LOCALLIBS) $(LIBS)

tstring: tstring.o
	$(CXX) $(CXXFLAGS) $(LDFLAGS) $(LIBDIRS) -o $@ $@.o $(LOCALLIBS) $(MATHLIBS) $(LIBS)

tstthred: tstthred.o
	$(CXX) $(CXXFLAGS) $(LDFLAGS) $(LIBDIRS) -o $@ $@.o $(LOCALLIBS) $(LIBS) $(MTLIBS)

tofstd: tofstd.o
	$(CXX) $(CXXFLAGS) $(LDFLAGS) $(LIBDIRS) -o $@ $@.o $(LOCALLIBS) $(MATHLIBS) $(LIBS)

tofdatim: tofdatim.o
	$(CXX) $(CXXFLAGS) $(LDFLAGS) $(LIBDIRS) -o $@ $@.o $(LOCALLIBS) $(MATHLIBS) $(LIBS)

tstatof: tstatof.o
	$(CXX) $(CXXFLAGS) $(LDFLAGS) $(LIBDIRS) -o $@ $@.o $(LOCALLIBS) $(MATHLIBS) $(LIBS)

tstftoa: tstftoa.o
	$(CXX) $(CXXFLAGS) $(LDFLAGS) $(LIBDIRS) -o $@ $@.o $(LOCALLIBS) $(MATHLIBS) $(LIBS)

toffile: toffile.o
	$(CXX) $(CXXFLAGS) $(LDFLAGS) $(LIBDIRS) -o $@ $@.o $(LOCALLIBS) $(MATHLIBS) $(LIBS)


tests: all test-list test-stack test-string

test-list: tlist tstlist
	@echo '--Testing OFList (part 1)'
	./tlist > tlist.out
	diff tlist.exp tlist.out
	@echo '--Testing OFList (part 2)'
	./tstlist > tstlist.out
	diff tstlist.exp tstlist.out

test-stack: tststack
	@echo '--Testing OFStack'
	./tststack > tststack.out
	diff tststack.exp tststack.out

test-string: tstring
	@echo '--Testing OFString'
	./tstring < tstring.inp > tstring.out
	diff tstring.exp tstring.out


install: all


clean:
	rm -f $(objs) $(progs) $(LOCALTRASH) $(TRASH)

distclean:
	rm -f $(objs) $(progs) $(LOCALTRASH) $(DISTTRASH)


dependencies:
	$(CXX) -MM $(defines) $(includes) $(CPPFLAGS) $(CXXFLAGS) *.cc  > $(DEP)

include $(DEP)
