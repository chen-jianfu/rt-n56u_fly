THISDIR := $(shell pwd)
ZSH_URL_BASE :=  https://github.com/felix-fly/rt-n56u/raw/master/trunk/user/zsh

ZSH_NAME := zsh-static
ZSH_URL := $(ZSH_URL_BASE)/$(ZSH_NAME)

all: download_test
	@echo "$(ZSH_NAME) install done!"

download_test:
	( if [ ! -f $(ZSH_NAME) ]; then \
		wget -t5 --timeout=20 --no-check-certificate $(ZSH_URL); \
	fi )

romfs:
ifeq ($(CONFIG_FIRMWARE_INCLUDE_ZSH),y)
	$(ROMFSINST) -p +x $(THISDIR)/$(ZSH_NAME) /usr/bin/zsh
endif