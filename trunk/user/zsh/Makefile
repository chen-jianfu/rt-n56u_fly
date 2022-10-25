THISDIR := $(shell pwd)
ZSH_NAME := zsh

all: extract_test
	@echo "$(ZSH_NAME) install done!"

extract_test:
	( if [ ! -d $(ZSH_NAME) ]; then \
		tar zxf $(ZSH_NAME).tar.gz ; \
	fi )

romfs:
ifeq ($(CONFIG_FIRMWARE_INCLUDE_ZSH),y)
	$(ROMFSINST) -p +x $(THISDIR)/zsh/zsh /usr/bin/zsh
	cp -r $(THISDIR)/zsh/share/zsh $(INSTALLDIR)/usr/share/
	echo "/usr/bin/zsh" >> $(INSTALLDIR)/etc_ro/shells
endif