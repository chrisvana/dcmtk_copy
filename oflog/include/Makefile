#
#	Makefile for oflog/include
#



SHELL = /bin/sh
srcdir = .
top_srcdir = ..
configdir = ../../config

include $(configdir)/Makefile.def


all:

install:
	$(configdir)/mkinstalldirs $(DESTDIR)$(includedir)/dcmtk/oflog
	for file in dcmtk/oflog/*.h ; do \
		$(INSTALL_DATA) $$file $(DESTDIR)$(includedir)/dcmtk/oflog ;\
	done
	$(configdir)/mkinstalldirs $(DESTDIR)$(includedir)/dcmtk/oflog/config
	for file in dcmtk/oflog/config/*.h ; do \
		$(INSTALL_DATA) $$file $(DESTDIR)$(includedir)/dcmtk/oflog/config ;\
	done
	$(configdir)/mkinstalldirs $(DESTDIR)$(includedir)/dcmtk/oflog/helpers
	for file in dcmtk/oflog/helpers/*.h ; do \
		$(INSTALL_DATA) $$file $(DESTDIR)$(includedir)/dcmtk/oflog/helpers ;\
	done
	$(configdir)/mkinstalldirs $(DESTDIR)$(includedir)/dcmtk/oflog/spi
	for file in dcmtk/oflog/spi/*.h ; do \
		$(INSTALL_DATA) $$file $(DESTDIR)$(includedir)/dcmtk/oflog/spi ;\
	done

clean:
	rm -f $(TRASH)

distclean:
	rm -f $(DISTTRASH)
