#
#	Makefile for dcmdata/apps
#



SHELL = /bin/sh
VPATH = ../include:../../config/include
srcdir = .
top_srcdir = ..
configdir = ../../config

include $(configdir)/Makefile.def

ofstddir = $(top_srcdir)/../ofstd
oflogdir = $(top_srcdir)/../oflog

LOCALINCLUDES = -I$(ofstddir)/include -I$(oflogdir)/include
LIBDIRS = -L$(top_srcdir)/libi2d -L$(top_srcdir)/libsrc -L$(ofstddir)/libsrc -L$(oflogdir)/libsrc
LOCALLIBS = -ldcmdata -loflog -lofstd $(ZLIBLIBS)
LIBI2D = -li2d

objs = dcmftest.o dcmconv.o dcmdump.o dump2dcm.o dcmgpdir.o dcm2xml.o \
	xml2dcm.o dcmcrle.o dcmdrle.o dcmodify.o mdfdsman.o mdfconen.o \
	pdf2dcm.o dcm2pdf.o img2dcm.o

progs = dcmftest dcmconv dcmdump dump2dcm dcmgpdir dcm2xml xml2dcm dcmcrle \
	dcmdrle dcmodify pdf2dcm dcm2pdf img2dcm


all: $(progs)

# Note: dcmftest does not need LOCALLIBS on most platforms, but on OSF1 it is required.
dcmftest: dcmftest.o
	$(CXX) $(CXXFLAGS) $(LDFLAGS) $(LIBDIRS) -o $@ $@.o $(LOCALLIBS) $(MATHLIBS) $(LIBS)

dcmconv: dcmconv.o
	$(CXX) $(CXXFLAGS) $(LDFLAGS) $(LIBDIRS) -o $@ $@.o $(LOCALLIBS) $(MATHLIBS) $(LIBS)

dcmdump: dcmdump.o
	$(CXX) $(CXXFLAGS) $(LDFLAGS) $(LIBDIRS) -o $@ $@.o $(LOCALLIBS) $(MATHLIBS) $(LIBS)

dump2dcm: dump2dcm.o
	$(CXX) $(CXXFLAGS) $(LDFLAGS) $(LIBDIRS) -o $@ $@.o $(LOCALLIBS) $(MATHLIBS) $(LIBS)

dcmgpdir: dcmgpdir.o
	$(CXX) $(CXXFLAGS) $(LDFLAGS) $(LIBDIRS) -o $@ $@.o $(LOCALLIBS) $(MATHLIBS) $(LIBS)

dcmcrle: dcmcrle.o
	$(CXX) $(CXXFLAGS) $(LDFLAGS) $(LIBDIRS) -o $@ $@.o $(LOCALLIBS) $(MATHLIBS) $(LIBS)

dcmdrle: dcmdrle.o
	$(CXX) $(CXXFLAGS) $(LDFLAGS) $(LIBDIRS) -o $@ $@.o $(LOCALLIBS) $(MATHLIBS) $(LIBS)

dcm2xml: dcm2xml.o
	$(CXX) $(CXXFLAGS) $(LDFLAGS) $(LIBDIRS) -o $@ $@.o $(LOCALLIBS) $(MATHLIBS) $(LIBS)

xml2dcm: xml2dcm.o
	$(CXX) $(CXXFLAGS) $(LDFLAGS) $(LIBDIRS) -o $@ $@.o $(XMLLIBS) $(LOCALLIBS) $(MATHLIBS) $(LIBS)

dcmodify: dcmodify.o mdfconen.o mdfdsman.o
	$(CXX) $(CXXFLAGS) $(LDFLAGS) $(LIBDIRS) -o $@ $@.o mdfconen.o mdfdsman.o $(LOCALLIBS) $(MATHLIBS) $(LIBS)

pdf2dcm: pdf2dcm.o
	$(CXX) $(CXXFLAGS) $(LDFLAGS) $(LIBDIRS) -o $@ $@.o $(LOCALLIBS) $(MATHLIBS) $(LIBS)

dcm2pdf: dcm2pdf.o
	$(CXX) $(CXXFLAGS) $(LDFLAGS) $(LIBDIRS) -o $@ $@.o $(LOCALLIBS) $(MATHLIBS) $(LIBS)

img2dcm: img2dcm.o
	$(CXX) $(CXXFLAGS) $(LDFLAGS) $(LIBDIRS) -o $@ $@.o $(LIBI2D) $(LOCALLIBS) $(MATHLIBS) $(LIBS)


install: install-bin

install-bin: all
	$(configdir)/mkinstalldirs $(DESTDIR)$(bindir)
	for prog in $(progs); do \
		$(INSTALL_PROGRAM) $$prog$(BINEXT) $(DESTDIR)$(bindir) && strip $(DESTDIR)$(bindir)/$$prog$(BINEXT) ;\
	done


clean:
	rm -f $(objs) $(progs) $(TRASH)

distclean:
	rm -f $(objs) $(progs) $(DISTTRASH)


dependencies:
	$(CXX) -MM $(defines) $(includes) $(CPPFLAGS) $(CXXFLAGS) *.cc  > $(DEP)

include $(DEP)
