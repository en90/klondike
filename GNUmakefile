TRIPLET=$(shell cc -dumpmachine)

.PHONY: all

all: debug release

build/${TRIPLET}/debug/klondike:	src/server/klondike.c src/server/klondike.h
	mkdir -p build/${TRIPLET}/debug
	cc -std=c11 -g -O0 -Wall -DDEBUG -D_BSD_SOURCE -D_DEFAULT_SOURCE src/server/klondike.c -o build/${TRIPLET}/debug/klondike -lbsd -lm

build/${TRIPLET}/release/klondike:	src/server/klondike.c src/server/klondike.h
	mkdir -p build/${TRIPLET}/release
	cc -std=c11 -Ofast -D_BSD_SOURCE -D_DEFAULT_SOURCE src/server/klondike.c -o build/${TRIPLET}/release/klondike -lbsd -lm
	strip build/${TRIPLET}/release/klondike

.PHONY: debug release clean distclean

debug: build/${TRIPLET}/debug/klondike

release: build/${TRIPLET}/release/klondike

clean:
	-rm build/${TRIPLET}/debug/klondike
	-rmdir build/${TRIPLET}/debug

distclean: clean
	-rm -r build
