RUSTC?=rustc.exe
RUST_OPTS=
SRC=src/hello.rs
RES=src/hello.rc
EXE=$(patsubst %.rs, %.exe, $(SRC))
RC=$(patsubst %.rc, %.rc.o, $(RES))

.SUFFIXES:

.PHONY: all
all: $(EXE)

%.exe: %.rs ../libwindows.dummy %.rc.o
	$(RUSTC) -L .. -o $@ $< -C link-args=$*.rc.o $(RUST_OPTS)

%.rc.o: %.rc
	windres $< $@

.PHONY: clean
clean:
	rm -rf $(EXE) $(RC)
