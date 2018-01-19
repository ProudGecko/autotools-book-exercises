package = jupiter
version = 1.0
tarname = $(package)
distdir = $(tarname)-$(version)
disttar = $(distdir).tar.gz

export prefix = /usr/local
export exec_prefix = $(prefix)
export bindir = $(exec_prefix)/bin

all clean check install uninstall jupiter:
	$(MAKE) -C src $@

dist: $(disttar)

distcheck: $(disttar)
	gzip -cd $+ | tar xvf -
	$(MAKE) -C $(distdir) all check
# Use of $$ results in the shell evaluating the "PWD" variable instead of Make
	$(MAKE) -C $(distdir) DESTDIR=$${PWD}/$(distdir)/_inst install uninstall
	$(MAKE) -C $(distdir) clean
	rm -rf $(distdir)
	@echo "*** Package $(disttar) ready for distribution."

$(disttar): FORCE $(distdir)
	tar chof - $(distdir) | gzip -9 -c >$(disttar)
	rm -rf $(distdir)

$(distdir):
	mkdir -p $(distdir)/src
	cp Makefile $(distdir)
	cp src/Makefile $(distdir)/src
	cp src/main.c $(distdir)/src

# Use of leading - causes Make to ignore exit code and NOT fail on non-zero exit codes
FORCE:
	-rm $(disttar) &> /dev/null
	-rm -rf $(distdir) &> /dev/null

.PHONY: FORCE all clean check dist distcheck
.PHONE: install uninstall
