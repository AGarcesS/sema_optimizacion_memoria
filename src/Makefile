CC = gcc
CFLAGS = -Wall -g

OBJS = mm.o

# Executable
EXE = mm

# Valgrind
MATRIX_SIZE = 256
BLOCK_SIZE = 64

# Cache
I1_SIZE = 1024
I1_ASSOCIATIVITY = 1
I1_BLOCK_SIZE = 128

D1_SIZE = 1024
D1_ASSOCIATIVITY = 2
D1_BLOCK_SIZE = 64

LL_SIZE = 4096
LL_ASSOCIATIVITY = 1
LL_BLOCK_SIZE = 128

all: $(OBJS)
	$(CC) $(CFLAGS) -o $(EXE) $(OBJS)

mm.o: mm.c
	$(CC) $(CFLAGS) -c mm.c

valgrind:
	valgrind --leak-check=yes ./$(EXE) $(MATRIX_SIZE) $(BLOCK_SIZE)
	valgrind --tool=callgrind --cache-sim=yes --I1=$(I1_SIZE),$(I1_ASSOCIATIVITY),$(I1_BLOCK_SIZE) --D1=$(D1_SIZE),$(D1_ASSOCIATIVITY),$(D1_BLOCK_SIZE) --LL=$(LL_SIZE),$(LL_ASSOCIATIVITY),$(LL_BLOCK_SIZE) ./$(EXE) $(MATRIX_SIZE) $(BLOCK_SIZE)
	callgrind_annotate --auto=yes callgrind.out.*	
	
clean:
	rm -f $(OBJS) $(EXE) *.bak *~ callgrind.out.*