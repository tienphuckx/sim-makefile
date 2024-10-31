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


CXX_SOURCES = $(wildcard *.cc) # wildcard all.cc files in the current directory
CXX_OBJECTS = $(patsubst %.cc,%.o,$(CXX_SOURCES)) # generate.o files from.cc files

build: ${CXX_OBJECTS}
	${CXX_SOURCES}
	${CXX_OBJECTS}
# $(COMPILER_CALL) ${CXX_OBJECTS} -o $(EXECUTABLE_NAME)

# main.o:
# 	$(COMPILER_CALL) -c main.cc

# my_lib.o:
# 	$(COMPILER_CALL) -c my_lib.cc

run:
	./$(EXECUTABLE_NAME)

cls:
	rm -f *.o $(EXECUTABLE_NAME)

# in case we have 100 files abc.cc 
# then will must impl 100 line abc.o:
# Apply PATTERNS
# $@ : Target file name
# $< : First prerequisite
# % : matches any character (except /)
# & : matches the whole pattern (equivalent to %.o)
%.o: &.cc
	$(COMPILER_CALL) -c $< -o $@

# It just like
# main.o: main.cc
# 	$(COMPILER_CALL) -c main.cc -o main.o