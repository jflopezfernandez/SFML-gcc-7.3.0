
# Implicit Rules
#
# Compiling C Programs
# n.o: n.c
#     $(CC) $(CPPFLAGS) $(CFLAGS) -c
#
# Compiling C++ Programs
# n.o: n.cpp
#     $(CXX) $(CPPFLAGS) $(CXXFLAGS) -c
#
# Assembling and Preprocessing Assembler Programs
# n.o: n.s
#     $(AS) $(ASFLAGS)
#
# Linking a Single Object File (Made automatically by running the linker 'ld'
# via the C Compiler)
# n: n.o
#     $(CC) $(LDFLAGS) n.o $(LOADLIBES) $(LDLIBES)

.SUFFIXES: .cpp .o

vpath %.h include
vpath %.cpp src

CC := g++

# SFML Directories
SFML_INCLUDE := "C:\Libs\SFML\SFML 2.4.2\MSVC x86_64\include"
SFML_LIB_DIR := "C:\Libs\SFML\SFML 2.4.2\gcc 7.3.0 x86_64\lib"

SFML_HEADERS := -I $(SFML_INCLUDE)
#SFML_LIBS := -L $(SFML_LIB_DIR) -lsfml-graphics -lsfml-window -lsfml-system
SFML_LIBS := -L $(SFML_LIB_DIR) -lsfml-audio -lsfml-graphics -lsfml-window -lsfml-system

WINDOWS_INCLUDE := "C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\um"
WINDOWS_LIB_DIR := "C:\Program Files (x86)\Windows Kits\10\Lib\10.0.17134.0\um\x64"

WINDOWS_LIBS := -L $(WINDOWS_LIB_DIR) -l:WinMM.lib

CFLAGS := -std=c++17 # -Wall -Wextra -Weffc++ -pedantic
CPPFLAGS := -I include $(SFML_HEADERS)

LFLAGS := $(SFML_LIBS) $(WINDOWS_LIBS)

SRCS := main.cpp
OBJS := $(patsubst %.cpp, %.o, $(SRCS))

PROGRAM := sfml.exe

.PHONY: all
all: $(PROGRAM)

$(PROGRAM): $(OBJS)
	$(CC) $(CFLAGS) $^ -o $@ $(LFLAGS)

$(OBJS): %.o: %.cpp
	$(CC) -c $(CFLAGS) $(CPPFLAGS) $< -o $@ $(LFLAGS)

#%.d: %.cpp
#	@set -e; rm -f $@; \
#	cc -MM $(CPPFLAGS) $< > $@.$$$$; \
#	sed 's,\($*\)\.o[ :]*,\1.o $@ : ,g' < $@.$$$$ > $@; \
#	rm -f $@.$$$$

#include $(SRCS:.cpp=.d)

.PHONY: clean
clean:
	rm -rf *.d *.o *.exe
