####### RULES ############
DEBUG ?= 1
ENABLE_WARNING ?= 1
WARNING_AS_ERROR ?= 0

###### DIRECTORIES ############
HEADER_DIR = header
SOURCE_DIR = src
BUILD_DIR = build

EXECUTABLE_NAME = main
CXX_STANDARD = c++11


######## WARNING #########
ifeq ($(ENABLE_WARNING), 1)
    CXX_WARNINGS += -Wall -Wextra -Wpedantic # enable all warnings
else
    CXX_WARNINGS +=
endif

ifeq ($(WARNING_AS_ERROR), 1)
    CXX_WARNINGS += -Werror # treat warnings as errors
endif

CXX_WARNINGS = -Wall -Wextra -Wpedantic
CXX = g++
CXXFLAGS = ${CXX_WARNINGS} -std=$(CXX_STANDARD)
LDFLAGS = 
CPPFLAGS += -I$(HEADER_DIR) # include header directory

ifeq ($(DEBUG), 1)
CXXFLAGS += -g -O0
else
CXXFLAGS += -O3
endif

COMPILER_CALL = $(CXX) $(CXXFLAGS) $(LDFLAGS) $(CPPFLAGS) # compiler call
CXX_SOURCES = $(wildcard $(SOURCE_DIR)/*.cc) # wildcard all.cc files in the current directory
CXX_OBJECTS = $(patsubst $(SOURCE_DIR)/%.cc,$(BUILD_DIR)/%.o,$(CXX_SOURCES)) # generate.o files from.cc files


######### TARGETS #########
all: create build

build: ${CXX_OBJECTS}
	$(COMPILER_CALL) $(CXX_OBJECTS) $(LDFLAGS) -o $(BUILD_DIR)/$(EXECUTABLE_NAME)

run:
	./$(BUILD_DIR)/$(EXECUTABLE_NAME)

cls:
	rm -f $(BUILD_DIR)/*.o $(BUILD_DIR)/$(EXECUTABLE_NAME)

create:
	@mkdir -p $(BUILD_DIR)


######### Pattern Rules #########

# $@ : Target file name
# $< : First prerequisite
# % : matches any character (except /)
# & : matches the whole pattern (equivalent to %.o)
$(BUILD_DIR)/%.o: $(SOURCE_DIR)/%.cc
	$(COMPILER_CALL) -c $< -o $@


###### PHONY TARGETS #########
.PHONY: all build run cls create