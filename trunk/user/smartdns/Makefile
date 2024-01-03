THISDIR := $(shell pwd)
SMARTDNS_URL_BASE := https://raw.githubusercontent.com/felix-fly/v2ray-padavan-doh/master/bin
SMARTDNS_HOSTS := https://raw.githubusercontent.com/felix-fly/v2ray-dnsmasq-dnscrypt/master/smartdns

SMARTDNS_NAME := smartdns
SMARTDNS_AD := ad.hosts
SMARTDNS_GW := gw.hosts
CERT_FILE := cacert.pem

all: download_test
	@echo "$(SMARTDNS_NAME) build done!"

download_test:
	( if [ ! -f $(SMARTDNS_NAME) ]; then \
		wget -t5 --timeout=20 --no-check-certificate $(SMARTDNS_URL_BASE)/$(SMARTDNS_NAME); \
	fi )
	( if [ ! -f $(SMARTDNS_AD) ]; then \
		wget -t5 --timeout=20 --no-check-certificate $(SMARTDNS_HOSTS)/$(SMARTDNS_AD); \
	fi )
	( if [ ! -f $(SMARTDNS_GW) ]; then \
		wget -t5 --timeout=20 --no-check-certificate $(SMARTDNS_HOSTS)/$(SMARTDNS_GW); \
	fi )
	( if [ ! -f $(CERT_FILE) ]; then \
		wget -t5 --timeout=20 --no-check-certificate https://curl.se/ca/$(CERT_FILE); \
	fi )

romfs:
ifeq ($(CONFIG_FIRMWARE_INCLUDE_SMARTDNS),y)
	$(ROMFSINST) -p +x $(THISDIR)/$(SMARTDNS_NAME) /usr/bin/$(SMARTDNS_NAME)
	$(ROMFSINST) -p -x $(THISDIR)/$(SMARTDNS_AD) /usr/lib/$(SMARTDNS_AD)
	$(ROMFSINST) -p -x $(THISDIR)/$(SMARTDNS_GW) /usr/lib/$(SMARTDNS_GW)
	$(ROMFSINST) -p -x $(THISDIR)/$(CERT_FILE) /usr/lib/$(CERT_FILE)
endif