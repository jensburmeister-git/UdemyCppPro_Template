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

CXX_SOURCES = $(wildcard *.cc)
CXX_OBJECTS = $(patsubst %.cc, %.o, $(CXX_SOURCES))

# Targets
build: $(CXX_OBJECTS)
	echo $(CXX_SOURCES)
	$(COMPILERCALL) $(CXX_OBJECTS) -o $(EXECUTABLE_NAME)

execute: build
	./$(EXECUTABLE_NAME)

clean:
	rm -f *.o
	rm -f $(EXECUTABLE_NAME)

# pattern
%.o: %.cc
	$(COMPILERCALL) -c $< -o $@
