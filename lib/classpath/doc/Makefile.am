SUBDIRS = api

EXTRA_DIST = README.jaxp texi2pod.pl

info_TEXINFOS = cp-hacking.texinfo cp-vmintegration.texinfo cp-tools.texinfo

.texinfo.dvi:
	texi2dvi $<

.dvi.ps:
	dvips -o $@ $<

docs: cp-hacking.ps cp-vmintegration.ps cp-tools.ps $(TOOLS_MANFILES)

man_MANS = $(TOOLS_MANFILES)
TOOLS_MANFILES = \
	gappletviewer.1 \
	gjar.1 \
	gjarsigner.1 \
	gjavah.1 \
	gcjh.1 \
	gkeytool.1 \
	gnative2ascii.1 \
	gorbd.1 \
	grmid.1 \
	grmiregistry.1 \
	gserialver.1 \
	gtnameserv.1

POD2MAN = pod2man --center="GNU" --release="$(VERSION)"
TEXI2POD = perl $(srcdir)/texi2pod.pl
STAMP = echo timestamp >

.pod.1:
	$(STAMP) $@
	-($(POD2MAN) --section=1 $< > $(@).T$$$$ && \
		mv -f $(@).T$$$$ $@) || \
		(rm -f $(@).T$$$$ && exit 1)

.INTERMEDIATE: gappletviewer.pod gjarsigner.pod gjar.pod gjavah.pod \
	gkeytool.pod gnative2ascii.pod gorbd.pod grmid.pod grmiregistry.pod \
	gserialver.pod gtnameserv.pod gcjh.pod

gappletviewer.pod: $(srcdir)/cp-tools.texinfo
	-$(TEXI2POD) -D gappletviewer < $< > $@

gjarsigner.pod: $(srcdir)/cp-tools.texinfo
	-$(TEXI2POD) -D gjarsigner < $< > $@

gjar.pod: $(srcdir)/cp-tools.texinfo
	-$(TEXI2POD) -D gjar < $< > $@

gcjh.pod: $(srcdir)/cp-tools.texinfo
	-$(TEXI2POD) -D gcjh < $< > $@

gjavah.pod: $(srcdir)/cp-tools.texinfo
	-$(TEXI2POD) -D gjavah < $< > $@

# hack around the cross references and the enumeration
gkeytool.pod: $(srcdir)/cp-tools.texinfo
	-$(TEXI2POD) -D gkeytool < $< \
	  | sed -e 's/^For more details.*/See I<Common Options> for more details./' \
	    -e 's/1\.<\([^>]*\)>/- \1/' \
		> $@

gnative2ascii.pod: $(srcdir)/cp-tools.texinfo
	-$(TEXI2POD) -D gnative2ascii < $< > $@

gorbd.pod: $(srcdir)/cp-tools.texinfo
	-$(TEXI2POD) -D gorbd < $< > $@

grmid.pod: $(srcdir)/cp-tools.texinfo
	-$(TEXI2POD) -D grmid < $< > $@

grmiregistry.pod: $(srcdir)/cp-tools.texinfo
	-$(TEXI2POD) -D grmiregistry < $< > $@

gserialver.pod: $(srcdir)/cp-tools.texinfo
	-$(TEXI2POD) -D gserialver < $< > $@

gtnameserv.pod: $(srcdir)/cp-tools.texinfo
	-$(TEXI2POD) -D gtnameserv < $< > $@

CLEANFILES = $(TOOLS_MANFILES)

