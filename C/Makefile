# Makefile for building the kata file with the Google Testing Framework
#
# SYNOPSIS:
#
#   make [all]  - makes everything.
#   make TARGET - makes the given target.
#   make clean  - removes all files generated by make.

# Please tweak the following variable definitions as needed by your
# project.

# Points to the root of CppUTest, relative to where this file is.
# Remember to tweak this if you move this file.
CPPUTEST_HOME = CppUTest

# Where to find user code.
USER_DIR = .

# Flags passed to the preprocessor.
CPPFLAGS += -I$(CPPUTEST_HOME)/include

# Flags passed to the C++ compiler.
CFLAGS += -g -Wall -Wextra

LD_LIBRARIES = -L$(CPPUTEST_HOME)/lib -lCppUTest

# All tests produced by this Makefile.  Remember to add new tests you
# created to the list.
TESTS = RoseGardenUnitTests

TEXTTESTS = RoseGardenTextTests

# House-keeping build targets.

all : $(TESTS) $(TEXTTESTS)

RoseGarden.o : $(USER_DIR)/RoseGarden.c

RoseGardenUnitTests : $(USER_DIR)/RoseGardenUnitTests.cc RoseGarden.o
	$(CXX) $(CPPFLAGS) $(CFLAGS) -o $@ $(USER_DIR)/RoseGardenUnitTests.cc RoseGarden.o $(LD_LIBRARIES)

RoseGardenTextTests.o : $(USER_DIR)/RoseGardenTextTests.c

RoseGardenTextTests : RoseGardenTextTests.o RoseGarden.o
	$(CC) $^ -o $@

clean :
	rm -f $(TESTS) $(TEXTTESTS) *.o *~

check-syntax:
	gcc $(CPPFLAGS) -o /dev/null -S ${CHK_SOURCES}
