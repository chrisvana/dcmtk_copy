#
#	Makefile for dcmwlm
#



SHELL = /bin/sh
VPATH = ./include:./../config/include
srcdir = .
top_srcdir = .
configdir = ./../config

include $(configdir)/Makefile.def


all: include-all libsrc-all apps-all wwwapps-all tests-all

install: install-bin install-doc install-support

install-bin: apps-install

install-doc: docs-install

install-data: data-install

install-etc: etc-install

install-include: include-install

install-lib: libsrc-install install-include

install-support: install-data install-etc


include-all:
	(cd include && $(MAKE) ARCH="$(ARCH)" all)

libsrc-all: include-all
	(cd libsrc && $(MAKE) ARCH="$(ARCH)" all)

apps-all: libsrc-all
	(cd apps && $(MAKE) ARCH="$(ARCH)" all)

wwwapps-all: libsrc-all
	(cd wwwapps && $(MAKE) ARCH="$(ARCH)" all)

tests-all: libsrc-all
	(cd tests && $(MAKE) ARCH="$(ARCH)" all)


include-install:
	(cd include && $(MAKE) ARCH="$(ARCH)" install)

libsrc-install: libsrc-all
	(cd libsrc && $(MAKE) ARCH="$(ARCH)" install)

apps-install: apps-all
	(cd apps && $(MAKE) ARCH="$(ARCH)" install)

wwwapps-install: wwwapps-all
	(cd wwwapps && $(MAKE) ARCH="$(ARCH)" install)

docs-install:
	(cd docs && $(MAKE) install)

data-install:
	(cd data && $(MAKE) install)

etc-install:
	(cd etc && $(MAKE) install)


clean:
	(cd include && $(MAKE) clean)
	(cd libsrc && $(MAKE) clean)
	(cd apps && $(MAKE) clean)
	(cd wwwapps && $(MAKE) clean)
	(cd tests && $(MAKE) clean)
	(cd docs && $(MAKE) clean)
	(cd data && $(MAKE) clean)
	(cd etc && $(MAKE) clean)
	rm -f $(TRASH)

distclean:
	(cd include && $(MAKE) distclean)
	(cd libsrc && $(MAKE) distclean)
	(cd apps && $(MAKE) distclean)
	(cd wwwapps && $(MAKE) distclean)
	(cd tests && $(MAKE) distclean)
	(cd docs && $(MAKE) distclean)
	(cd data && $(MAKE) distclean)
	(cd etc && $(MAKE) distclean)
	rm -f $(DISTTRASH)

dependencies:
	(cd libsrc && touch $(DEP) && $(MAKE) dependencies)
	(cd apps && touch $(DEP) && $(MAKE) dependencies)
	(cd wwwapps && touch $(DEP) && $(MAKE) dependencies)
	(cd tests && touch $(DEP) && $(MAKE) dependencies)
