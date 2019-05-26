progname=triang
builddir=build
srcdir=src

.PHONY: build clean

default: build

build:
	if [ ! -e ${builddir} ];then mkdir ${builddir};fi
	ghc -O2 -o ${builddir}/${progname} ${srcdir}/${progname}.hs
	mv ${srcdir}/*.hi ${srcdir}/*.o ${builddir}/

clean:
	rm build/*
