# ## VARIABLES ##

# # CC: Program for compiling C programs; default is gcc
# CC = gcc

# # CFLAGS: Flags for compiling C programs; default is -g -Wall
# CFLAGS = -g -Wall

# # CXX: Program for compiling C++ programs; default is g++
# CXX = g++

# # CXXFLAGS: Flags for compiling C++ programs; default is -g -Wall -std=c++11
# CXXFLAGS = -g -Wall -Wextra -Wpednatic -std=c++11

# # CPPFLAGS: Flags for compiling C++ programs; default is -g -Wall -std=c++11
# CPPFLAGS = -g -Wall -std=c++11

# # LDFLAGS: Flags for linking executables; default is -lm
# LDFLAGS = -lm

DEBUG = 1
EXECUTABLE_NAME = main

CXX_STANDARD = c++11
CXX_WARNINGS = -Wall -Wextra -Wpedantic
CXX = g++
CXXFLAGS = ${CXX_WARNINGS} -std=$(CXX_STANDARD)
LDFLAGS = 
COMPILER_CALL = $(CXX) $(CXXFLAGS) $(LDFLAGS)

ifeq ($(DEBUG), 1)
CXXFLAGS += -g -O0
else
CXXFLAGS += -O3
endif

build: my_lib.o main.o
	$(COMPILER_CALL) main.o my_lib.o -o $(EXECUTABLE_NAME)

main.o:
	$(COMPILER_CALL) -c main.cc

my_lib.o:
	$(COMPILER_CALL) -c my_lib.cc

run:
	./$(EXECUTABLE_NAME)

cls:
	rm -f *.o $(EXECUTABLE_NAME)