INSTALL = /usr/bin/install -c

# == Installation directories
prefix = ${DESTDIR}/usr
mandir = ${prefix}/share/man/man1
exec_prefix = ${prefix}
bindir = ${exec_prefix}/bin

# == Build directives
## For SCO
#CFLAGS = -b elf -O -D_SVID
## For IRIX
#CFLAGS = -xansi -fullwarn -O3 -g0
## For Solaris
#CFLAGS = -fast -xO4 -s -v -Xa
## For HPUX
#CFLAGS = -Wall -O -Ae
## For OSF1
#CFLAGS = -w -verbose -fast -std1 -g0
## For GNU C compiler
#CFLAGS = -Wall # -O6 -pedantic

all: shc

shc: shc.c
	$(CC) $(CFLAGS) $(CPPFLAGS) $(LDFLAGS) $@.c -o $@

test: make_the_test

make_the_test: match.x
	@echo '***	Running a compiled test script!'
	@echo '***	It must show files with substring "sh" in your PATH...'
	./match.x sh || true

match.x: shc match
	@echo '***	Compiling script "match"'
	CFLAGS="$(CFLAGS) $(CPPFLAGS) $(LDFLAGS)" ./shc -v -f match

clean:
	rm -f *.o *~ *.x.c shc *.x

cleanall: clean
	rm -f shc *.x

install:
	$(INSTALL) -m 755 -d $(bindir)
	$(INSTALL) -m 755 -d $(mandir)

	$(INSTALL) -m 755 -s shc $(bindir)
	$(INSTALL) -m 644 shc.1 $(mandir)

