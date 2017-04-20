## this is a simple wrapper just to forward on known commands to the
## embedding example with values pulled from Make.inc
SRCDIR := $(abspath $(dir $(lastword $(MAKEFILE_LIST))))
JULIAHOME := $(abspath $(SRCDIR)/..)
BUILDDIR := .
include $(JULIAHOME)/Make.inc

release: # default target
all: release debug

EMBEDDING_ARGS := \
	-C $(BUILDROOT)/examples/embedding \
	JULIA='$(call spawn,$(JULIA_EXECUTABLE))' \
	BIN='$(build_bindir)' \
	CC='$(CC)'

release debug:
	@$(MAKE) $@ $(EMBEDDING_ARGS)

eprint-%:
	@$(MAKE) print-$* $(EMBEDDING_ARGS)

clean:
	@$(MAKE) clean $(EMBEDDING_ARGS)

.PHONY: all release debug clean eprint-*
