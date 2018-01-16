package = jupiter
version = 1.0
tarname = $(package)
distdir = $(tarname)-$(version)
disttar = $(distdir).tar.gz

all clean jupiter:
	$(MAKE) -C src $@

dist: $(disttar)

distcheck: $(disttar)
	gzip -cd $+ | tar xvf -
	$(MAKE) -C $(distdir) all clean
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

.PHONY: FORCE all clean dist distcheck

