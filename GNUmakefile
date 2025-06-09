# Using the "Makes" Makefile setup - https://github.com/makeplus/makes
M := $(or $(MAKES_REPO_DIR),.cache/makes)
$(shell [ -d $M ] || git clone -q https://github.com/makeplus/makes $M)
include $M/init.mk
include $M/clean.mk
include $M/just.mk
include $M/rust.mk

MAKES-CLEAN := target

JUST-CMDS := $(JUST-CMDS:%=just-%)
CARGO-CMDS := $(CARGO-CMDS:%=cargo-%)

$(JUST-CMDS): $(JUST) $(CARGO)
	$< $(@:just-%=%)

$(CARGO-CMDS): $(CARGO)
	$< $(@:cargo-%=%)
