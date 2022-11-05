DEBUG = 1
EXECUTABLE_NAME = helloworld

CXX_STANDARD = c++17
CXX = g++
CXX_WARNINGS = -Wall -Wextra -Wpedantic
CXXFLAGS = $(CXX_WARNINGS) -std=$(CXX_STANDARD)
CPPFLAGS =
LDFLAGS =

ifeq ($(DEBUG), 1)
CXXFLAGS += -g -O0
else
CXXFLAGS += -O3
endif

COMPILERCALL = $(CXX) $(CXXFLAGS)

# Targets
build: main.o my_lib.o
	$(COMPILERCALL) main.o my_lib.o -o $(EXECUTABLE_NAME)

main.o:
	$(COMPILERCALL) main.cc -c

my_lib.o:
	$(COMPILERCALL) my_lib.cc -c

execute: build
	./$(EXECUTABLE_NAME)

clean:
	rm -f *.o
	rm -f $(EXECUTABLE_NAME)
