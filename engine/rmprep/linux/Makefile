LIBNAME=librmprep
VERSION=1
DBGFLAGS=
LIBRARY=$(LIBNAME).so.$(VERSION)

OUTPATH=../../apps/linux/
VPATH=..
CC=g++
LIBS=-lgsl
CFLAGS=-fPIC -c -Wall $(DBGFLAGS) -I../../../../gsl-1.10/include/
LDFLAGS=-shared -Wl,-export-dynamic -Wl,-soname,$(LIBRARY) -L../../../../gsl-1.10/lib/ $(LIBS)
SOURCES=rmprep.cpp
HEADERS=rmprep.h rmprep_enums.h rmprep_impexp.h rmprepdata.h
OBJECTS=$(SOURCES:.cpp=.o)

all: $(SOURCES) $(LIBRARY) link_lib copy_lib

$(LIBRARY): $(OBJECTS) $(HEADERS)
	$(CC) $(LDFLAGS) $(OBJECTS) -o $@

%.o : %.cpp
	$(CC) $(CFLAGS) $< -o $@

link_lib:
	ln -s $(LIBRARY) $(LIBNAME).so

copy_lib:
	cp $(LIBNAME).so $(OUTPATH)

clean:
	rm -rf *.o $(LIBRARY) $(LIBNAME).so

