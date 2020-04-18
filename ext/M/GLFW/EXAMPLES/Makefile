#-------------------------------------------------------------------------------
#-------------------------------------------------------------------------------

OPT += $(shell pkg-config --cflags glfw3)
OPT += -I. 

LIB += $(shell pkg-config --libs glfw3) -lm

#-------------------------------------------------------------------------------

EXTDIR = ./DEPS

EXTINC = -I$(EXTDIR) 
EXTLIB = $(EXTDIR)/glad.o $(EXTDIR)/tinycthread.o  -ldl

# On non-Windows platforms glad requires libdl,
# make sure to link with it (-ldl for gcc)!

#-------------------------------------------------

PROGS = _EXTLIB  empty simple threads splitview  w-test

all: $(PROGS)

#-------------------------------------------------

_EXTLIB:
	(cd $(EXTDIR); make)

#-------------------------------------------------

empty: empty.c 
	$(CC) -pthread  -Wl,-rpath,./ $(OPT) $(EXTINC) $^ $(LIB) $(EXTLIB) -o $@  

simple: simple.c 
	$(CC) -pthread  -Wl,-rpath,./ $(OPT) $(EXTINC) $^ $(LIB) $(EXTLIB) -o $@

threads: threads.c 
	$(CC) -pthread  -Wl,-rpath,./ $(OPT) $(EXTINC) $^ $(LIB) $(EXTLIB) -o $@

splitview: splitview.c 
	$(CC) -pthread  -Wl,-rpath,./ $(OPT) $(EXTINC) $^ $(LIB) $(EXTLIB) -o $@

#-------------------------------------------------

w-test: w-test.c 
	$(CC) -pthread  -Wl,-rpath,./ $(OPT) $(EXTINC) $^ $(LIB) $(EXTLIB) -o $@

#-------------------------------------------------------------------------------

clean:
	(cd $(EXTDIR); make clean)
	@-rm -vf *.o $(PROGS)

#-------------------------------------------------------------------------------
#-------------------------------------------------------------------------------

