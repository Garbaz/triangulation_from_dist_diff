progname=triang
builddir=build
srcdir=src

.PHONY: build clean

default: build

build:
	if [ ! -e ${builddir} ];then mkdir ${builddir};fi
	gcc -lm -O2 -o ${builddir}/${progname} ${srcdir}/${progname}.c

clean:
	rm build/*
