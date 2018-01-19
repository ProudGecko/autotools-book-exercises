sources = main.c

all: jupiter

jupiter: $(sources)
	gcc -g -O0 -o $@ $+

check: all
	./jupiter | grep "Hello from .*jupiter!"
	@echo "** ALL TESTS PASSED ***"

clean:
	-rm jupiter

install:
	install -d $(prefix)/bin
	install -m 0755 jupiter $(prefix)/bin

uninstall:
	-rrm $(prefix)/bin/jupiter

.PHONY: all clean check install uninstall

