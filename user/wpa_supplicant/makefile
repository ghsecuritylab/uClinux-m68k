URL = https://w1.fi/releases/wpa_supplicant-2.5.tar.gz
FINALTARGET = my_build
AUTOMAKE_ROMFS = my_romfs
include $(ROOTDIR)/tools/download.inc

build/%-my_build: build/%-patched
	@echo "Building $* ..."
	$(AT)mkdir -p build/$($*_BUILDDIR)
	$(AT)ln -fs `pwd`/config build/$($*_BUILDDIR)/wpa_supplicant/.config
	$(AT)make -C build/$($*_BUILDDIR)/wpa_supplicant
	$(AT)touch $@

my_romfs:
	$(ROMFSINST) -e CONFIG_USER_WPA_SUPPLICANT build/$($(PKG)_BUILDDIR)/wpa_supplicant/wpa_supplicant /bin/wpa_supplicant
	$(ROMFSINST) -e CONFIG_USER_WPA_PASSPHRASE build/$($(PKG)_BUILDDIR)/wpa_supplicant/wpa_passphrase /bin/wpa_passphrase
