TARGET = sip.so
OFILES = siplib.o apiversions.o descriptors.o qtlib.o threads.o objmap.o voidptr.o array.o bool.o
HFILES = sip.h sipint.h array.h 

CC = gcc
CXX = g++
LINK = g++
CPPFLAGS = -DNDEBUG -I. -I/home/sgongar/Dev/client/scripts/sip-4.16.8/siplib -I/usr/include/python2.7
CFLAGS = -pipe -fPIC -O2 -w
CXXFLAGS = -pipe -fPIC -O2 -w
LFLAGS = -shared -Wl,--version-script=sip.exp
LIBS = 
VPATH = /home/sgongar/Dev/client/scripts/sip-4.16.8/siplib

.SUFFIXES: .c .o .cpp .cc .cxx .C


.cpp.o:
	$(CXX) -c $(CXXFLAGS) $(CPPFLAGS) -o $@ $<

.cc.o:
	$(CXX) -c $(CXXFLAGS) $(CPPFLAGS) -o $@ $<

.cxx.o:
	$(CXX) -c $(CXXFLAGS) $(CPPFLAGS) -o $@ $<

.C.o:
	$(CXX) -c $(CXXFLAGS) $(CPPFLAGS) -o $@ $<

.c.o:
	$(CC) -c $(CFLAGS) $(CPPFLAGS) -o $@ $<

all: $(TARGET)

$(OFILES): $(HFILES)

$(TARGET): $(OFILES)
	@echo '{ global: initsip; local: *; };' > sip.exp
	$(LINK) $(LFLAGS) -o $(TARGET) $(OFILES) $(LIBS)

install: $(TARGET)
	@test -d $(DESTDIR)/home/sgongar/Dev/client/.venv/lib/python2.7/site-packages || mkdir -p $(DESTDIR)/home/sgongar/Dev/client/.venv/lib/python2.7/site-packages
	cp -f $(TARGET) $(DESTDIR)/home/sgongar/Dev/client/.venv/lib/python2.7/site-packages/$(TARGET)
	strip $(DESTDIR)/home/sgongar/Dev/client/.venv/lib/python2.7/site-packages/$(TARGET)
	@test -d $(DESTDIR)/include/python2.7 || mkdir -p $(DESTDIR)/include/python2.7
	cp -f /home/sgongar/Dev/client/scripts/siplib/sip.h $(DESTDIR)/include/python2.7/sip.h

clean:
	-rm -f $(TARGET)
	-rm -f siplib.o
	-rm -f apiversions.o
	-rm -f descriptors.o
	-rm -f qtlib.o
	-rm -f threads.o
	-rm -f objmap.o
	-rm -f voidptr.o
	-rm -f array.o
	-rm -f bool.o
	-rm -f sip.exp
