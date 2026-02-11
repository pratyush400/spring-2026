CC=cc
EXEC=bitfun
SOURCES=driver.c bitlib.c
OBJS=driver.o bitlib.o
OPTS=-std=c99 -Wall

all: $(EXEC)

$(EXEC): $(OBJS)
	$(CC) $(OPTS) $(OBJS) -o $(EXEC)

.c.o:
	$(CC) $(OPTS) -c *.c

clean:
	rm -f *.o $(EXEC) a.out
