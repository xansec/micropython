MPTOP = ..
CC = clang
CFLAGS += -std=c99 -I. -I$(MPTOP) -DNO_QSTR -g -O1 -fsanitize=fuzzer-no-link,address
CXX = clang++
CXXFLAGS += -I. -I$(MPTOP) -DNO_QSTR -g -O1 -fsanitize=fuzzer-no-link,address
LDFLAGS += -L./build -fsanitize=fuzzer,address

fuzz-execute-from-string: fuzz-execute-from-string.o -lmicropython

-lmicropython:
	$(MAKE) -f $(MPTOP)/examples/embedding/Makefile.upylib MPTOP=$(MPTOP)
