MACH ?=	m68k
TARGET ?= $(MACH)-none
VERSION ?= 1.1.0
PCCLIBDIR ?= /usr/local/lib/pcc/$(TARGET)/$(VERSION)/lib
SRCDIR ?= .

CFLAGS += -I$(SRCDIR)/$(MACH) -I$(SRCDIR) -Wall -Wstrict-prototypes -Wmissing-prototypes

OBJS = crt0.o crt1.o crti.o crtn.o crtbegin.o crtend.o crtbeginS.o crtendS.o crtbeginT.o crtendT.o

all:	$(OBJS)

crt0.o:	$(MACH)/crt0.s
	$(AS) -c -o $@ $<

crt1.o:	$(MACH)/crt0.s
	$(AS) -c -o $@ $<

crti.o: $(MACH)/crti.s
	$(CC) -O2 $(CFLAGS) -c -o $@ $<

crtn.o: $(MACH)/crtn.s
	$(CC) -O2 $(CFLAGS) -c -o $@ $<

crtbegin.o: crtbegin.c
	$(CC) -O2 $(CFLAGS) -c -o $@ $<

crtend.o: crtend.c
	$(CC) -O2 $(CFLAGS) -c -o $@ $<

crtbeginS.o: crtbegin.c
	$(CC) -O2 $(CFLAGS) -fpic -c -o $@ $<

crtendS.o: crtend.c
	$(CC) -O2 $(CFLAGS) -fpic -c -o $@ $<

crtbeginT.o: crtbegin.c
	$(CC) -O2 $(CFLAGS) -c -o $@ $<

crtendT.o: crtend.c
	$(CC) -O2 $(CFLAGS) -c -o $@ $<

install:
	mkdir -p ${DESTDIR}$(PCCLIBDIR)
	cp $(OBJS) ${DESTDIR}$(PCCLIBDIR)

clean:
	rm -f $(OBJS)
