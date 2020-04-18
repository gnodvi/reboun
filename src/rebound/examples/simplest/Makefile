#--------------------------------------------------------------------

export OPENGL=1
#export OPENGL=0

#-----------------------------------

#include ../../src/Makefile.defs

#CC = cc -std=c99 -Wpointer-arith -D_GNU_SOURCE
CC = gcc -std=c99 

OPT += $(shell pkg-config --cflags --libs glfw3)

#-----------------------------------

OPT += -I../../src/  -L../../src/ 

#--------------------------------------------------------------------

PROGS = problem empty simple

all: $(PROGS)

#--------------------------------------------------------------------

problem: problem.c
	$(CC) -pthread  -Wl,-rpath,./ $(OPT) $(PREDEF) $<  -lrebound $(LIB) -o $@

#--------------------------------------------------------------------


OPT += $(shell pkg-config --cflags glfw3)
OPT += -I. 

LIB += $(shell pkg-config --libs glfw3) -lm


EXTDIR = ./DEPS

EXTINC = -I$(EXTDIR) 
EXTLIB = $(EXTDIR)/glad.o $(EXTDIR)/tinycthread.o  -ldl

empty: empty.c 
	$(CC) -pthread  -Wl,-rpath,./ $(OPT) $(EXTINC) $^ $(LIB) $(EXTLIB) -o $@  

simple: simple.c 
	$(CC) -pthread  -Wl,-rpath,./ $(OPT) $(EXTINC) $^ $(LIB) $(EXTLIB) -o $@  

#--------------------------------------------------------------------

clean:
	@-rm -vf $(PROGS)

#--------------------------------------------------------------------

