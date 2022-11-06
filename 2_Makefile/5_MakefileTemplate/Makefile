# variables meant as parameter
DEBUG ?= 1

INCLUDE_DIR = include
SOURCE_DIR = src
BUILD_DIR = build

CXX_STANDARD = c++17
CXX = g++
CXX_WARNINGS = -Wall -Wextra -Wpedantic
CXXFLAGS = $(CXX_WARNINGS) -std=$(CXX_STANDARD)
CPPFLAGS = -I $(INCLUDE_DIR)
LDFLAGS =

ifeq ($(DEBUG), 1)
CXXFLAGS += -g -O0
EXECUTABLE_NAME = helloworld_debug
else
CXXFLAGS += -O3
EXECUTABLE_NAME = helloworld
endif

COMPILERCALL = $(CXX) $(CXXFLAGS) $(CPPFLAGS)

CXX_SOURCES = $(wildcard $(SOURCE_DIR)/*.cc)
CXX_OBJECTS = $(patsubst $(SOURCE_DIR)/%.cc, $(BUILD_DIR)/%.o, $(CXX_SOURCES))

# Targets
all: create build

create:
	@mkdir -p build
# the @ at the beginning of the line will suppress the output
# command that depend on each other must be in one line witl && like
# cd build && mkdir -p subbuild

build: create $(CXX_OBJECTS)
	echo $(CXX_SOURCES)
	$(COMPILERCALL) $(CXX_OBJECTS) -o $(BUILD_DIR)/$(EXECUTABLE_NAME)

execute: build
	./$(BUILD_DIR)/$(EXECUTABLE_NAME)

clean:
	rm -f $(BUILD_DIR)/*.o
	rm -f $(BUILD_DIR)/$(EXECUTABLE_NAME)

# pattern
$(BUILD_DIR)/%.o: $(SOURCE_DIR)/%.cc
	$(COMPILERCALL) -c $< -o $@

# PHONY (make will not look for a file with that name and check the timestamp)
PHONY: all create build execute clean
