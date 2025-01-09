  
  

```JavaScript
CC=g++
CFLAGS=-Wall -Wextra -Iinclude
LIBS=-lm
BIN=hello
ODIR=obj
SDIR=src
IDIR=include
_OBJ = hello.o hellofunc.o
OBJ = $(patsubst %,$(ODIR)/%,$(_OBJ))
_DEPS = hello.h
DEPS = $(patsubst %,$(IDIR)/%,$(_DEPS))
all: $(BIN)
$(ODIR)/%.o : $(SDIR)/%.cpp $(DEPS)
$(CC) -c -o $@ $< $(CFLAGS)
$(BIN): $(OBJ)
$(CC) -o $@ $(OBJ) $(CFLAGS) $(LIBS)
clean:
rm -f $(ODIR)/*.o $(BIN)
```