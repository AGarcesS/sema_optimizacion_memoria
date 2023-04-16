CC = gcc
CFLAGS = -Wall -g

OBJS = mm.o

# Executable
EXE = mm

# Valgrind
MATRIX_SIZE = 256
BLOCK_SIZE = 64

all: $(OBJS)
	$(CC) $(CFLAGS) -o $(EXE) $(OBJS)

mm.o: mm.c
	$(CC) $(CFLAGS) -c mm.c

valgrind:
	valgrind --leak-check=yes ./$(EXE) $(MATRIX_SIZE) $(BLOCK_SIZE)
	valgrind --tool=cachegrind ./$(EXE) $(MATRIX_SIZE) $(BLOCK_SIZE)
	cg_annotate --auto=yes cachegrind.out.*
	valgrind --tool=callgrind --cache-sim=yes ./$(EXE) $(MATRIX_SIZE) $(BLOCK_SIZE)
	callgrind_annotate --auto=yes callgrind.out.*
	
clean:
	rm -f $(OBJS) $(EXE) *.bak *~ cachegrind.out.* callgrind.out.*