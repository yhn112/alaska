# $Id: Makefile 1494 2009-04-30 13:10:41Z css1hs $
# (C) 2009: Hans Georg Schaathun <georg@ii.uib.no>

all:
	cd jpeglib ; make all
	$(MAKE) jpegObject.so

txt: __init__.py.txt base.py.txt dct.py.txt compress.py.txt

doc: txt

%.py.txt: %.py
	pylit.py $<


IFLAGS=-I/usr/include/python2.7

LDOFLAGS=-Wl,-O1 -Wl,-Bsymbolic-functions 
CFLAGS=-pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC $(IFLAGS)

test: 
	echo $(IFLAGS)


LDFLAGS=-Ljpeglib -ljpeg

jpegObject.so: jpegobject.o
	gcc -pthread -shared $(LDOFLAGS) jpegobject.o  -o jpegObject.so $(LDFLAGS)

test.log: test.py f4.py f5.py
	./test.py > test.log

clean:
	rm -f *.pyc *.o
	rm -f *.log stego*.jpg
	rm -f *.dat
	rm -rf build
	rm -f 1
	cd jpeglib ; $(MAKE) clean

dclean: clean
	rm -f jpegObject.so
