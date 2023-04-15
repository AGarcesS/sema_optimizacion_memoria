CC = gcc
CFLAGS = -Wall -g

OBJS = mm.o

# Executable
EXE = mm

all: $(OBJS)
	$(CC) $(CFLAGS) -o $(EXE) $(OBJS)

mm.o: mm.c
	$(CC) $(CFLAGS) -c mm.c

valgrind:
	valgrind --leak-check=yes ./$(EXE) 100 100
	valgrind --tool=cachegrind ./$(EXE) 100 100
	cg_annotate --auto=yes cachegrind.out.*
	valgrind --tool=callgrind --cache-sim=yes ./$(EXE) 100 100
	callgrind_annotate --auto=yes callgrind.out.*
	
clean:
	rm -f $(OBJS) $(EXE) *.bak *~ cachegrind.out.* callgrind.out.*