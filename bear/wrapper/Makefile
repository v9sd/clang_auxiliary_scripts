.PHONY: all

UTILS_ARM_PREFIX:=arm-none-eabi-
USR_BIN:=

BEAR_WRAPPER_OUTPUT_DIRECTORY:=$(PWD)/wrapper.d

UTILS_ARM:=$(notdir $(wildcard /usr/bin/$(UTILS_ARM_PREFIX)*))

UTILS_ORIGINAL:= \
	ar \
	bison  \
	cc \
	f77 \
	g++ \
	ld \
	makeinfo \
	objcopy \
	readelf \
	yacc \
	as \
	c++ \
	cpp  \
	flex \
	gcc \
	lex \
	nm \
	objdump \
	ranlib \
	strip    

all: $(addprefix $(BEAR_WRAPPER_OUTPUT_DIRECTORY)/,$(UTILS_ARM)) \
$(addprefix $(BEAR_WRAPPER_OUTPUT_DIRECTORY)/,$(UTILS_ORIGINAL))

define BEAR_WRAPPER_TARGET
.PHONY: $(BEAR_WRAPPER_OUTPUT_DIRECTORY)/$1
$(BEAR_WRAPPER_OUTPUT_DIRECTORY)/$1: /usr/bin/$1
	mkdir -p "$(BEAR_WRAPPER_OUTPUT_DIRECTORY)"
	ln -f -s /usr/lib/x86_64-linux-gnu/bear/wrapper "$(BEAR_WRAPPER_OUTPUT_DIRECTORY)/$1"
endef

$(foreach i,$(UTILS_ARM),$(eval $(call BEAR_WRAPPER_TARGET,$i)))

$(info $(UTILS_ORIGINAL))

$(foreach i,$(UTILS_ORIGINAL),$(eval $(call BEAR_WRAPPER_TARGET,$i)))


