sources = main.c

all: jupiter

jupiter: $(sources)
	gcc -g -O0 -o $@ $+

check: all
	./jupiter | grep "Hello from .*jupiter!"
	@echo "** ALL TESTS PASSED ***"

clean:
	-rm jupiter

.PHONY: all clean check

