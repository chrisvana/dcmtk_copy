#
#	Makefile for dcmqrdb/docs
#



SHELL = /bin/sh
srcdir = .
top_srcdir = ..
configdir = ../../config

include $(configdir)/Makefile.def

files = dcmqrcnf.txt dcmqrset.txt


all:

install:
	$(configdir)/mkinstalldirs $(DESTDIR)$(docdir)
	for file in $(files); do \
		$(INSTALL_DATA) $$file $(DESTDIR)$(docdir) ;\
	done

clean:
	rm -f $(TRASH)

distclean:
	rm -f $(DISTTRASH)
