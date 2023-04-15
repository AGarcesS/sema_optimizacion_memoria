CC = gcc
CFLAGS = -Wall

OBJS = mm.o

# Executable
EXE = mm

all: $(OBJS)
	$(CC) $(CFLAGS) -o $(EXE) $(OBJS)

$(OBJS): $(HDRS)

mm.o: mm.c
	$(CC) $(CFLAGS) -c mm.c

clean:
	rm -f $(OBJS) $(EXE) *.bak *~