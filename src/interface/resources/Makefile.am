SUBDIRS = 16x16 32x32 cyril blukis lone minimal opencrystal

CLEANFILES = filezilla.o

resourcesdir = $(pkgdatadir)/resources

dist_resources_DATA = defaultfilters.xml \
		dialogs.xrc down.png dropdown.png \
		finished.wav \
		leds.png menus.xrc netconfwizard.xrc \
		quickconnectbar.xrc \
		settings.xrc \
		theme.xml toolbar.xrc up.png

resources20dir = $(pkgdatadir)/resources/20x20
dist_resources20_DATA = 20x20/unknown.png

resources24dir = $(pkgdatadir)/resources/24x24
dist_resources24_DATA = 24x24/unknown.png

resources48dir = $(pkgdatadir)/resources/48x48
dist_resources48_DATA = 48x48/filezilla.png \
			48x48/speedlimits.png

if USE_RESOURCEFILE
nodist_noinst_DATA = filezilla.o

filezilla.o: $(srcdir)/filezilla.rc $(srcdir)/windows_manifest.xml version.rc
	@if [ -f $@~ ]; then rm $@~; fi
	@WINDRES@ --include-dir=. --include-dir=$(srcdir) $(WINDRESFLAGS) $(srcdir)/filezilla.rc -D GNU_WINDRES -D HAS_VERSIONRC $@~ || rm $@~
	@if [ -f $@ ]; then rm $@; fi
	mv $@~ $@
endif


dist_noinst_DATA = filezilla.rc FileZilla.ico \
		FileZilla.icns MacInfo.plist.in \
		version.rc.in windows_manifest.xml

if MACAPPBUNDLE
mac-copy-resources: $(dist_resources_DATA)
	cp MacInfo.plist $(top_builddir)/FileZilla.app/Contents/Info.plist
	cp $(srcdir)/FileZilla.icns $(top_builddir)/FileZilla.app/Contents/Resources/FileZilla.icns

	for i in $(dist_resources_DATA); \
		do cp -f "$(srcdir)/$$i" "$(top_builddir)/FileZilla.app/Contents/SharedSupport/resources"; \
	done
	mkdir -p "$(top_builddir)/FileZilla.app/Contents/SharedSupport/resources/20x20"
	for i in $(dist_resources20_DATA); \
		do cp -f "$(srcdir)/$$i" "$(top_builddir)/FileZilla.app/Contents/SharedSupport/resources/20x20"; \
	done
	mkdir -p "$(top_builddir)/FileZilla.app/Contents/SharedSupport/resources/24x24"
	for i in $(dist_resources24_DATA); \
		do cp -f "$(srcdir)/$$i" "$(top_builddir)/FileZilla.app/Contents/SharedSupport/resources/24x24"; \
	done
	mkdir -p "$(top_builddir)/FileZilla.app/Contents/SharedSupport/resources/48x48"
	for i in $(dist_resources48_DATA); \
		do cp -f "$(srcdir)/$$i" "$(top_builddir)/FileZilla.app/Contents/SharedSupport/resources/48x48"; \
	done
	
	$(MAKE) -C 16x16 mac-copy-resources
	$(MAKE) -C 32x32 mac-copy-resources
	$(MAKE) -C cyril mac-copy-resources
	$(MAKE) -C blukis mac-copy-resources
	$(MAKE) -C lone mac-copy-resources
	$(MAKE) -C opencrystal mac-copy-resources
endif

pixmapsdir = $(datadir)/pixmaps
pixmaps_DATA = 48x48/filezilla.png

hicolorapps16dir = $(datadir)/icons/hicolor/16x16/apps
hicolorapps16_DATA = 16x16/filezilla.png
hicolorapps32dir = $(datadir)/icons/hicolor/32x32/apps
hicolorapps32_DATA = 32x32/filezilla.png
hicolorapps48dir = $(datadir)/icons/hicolor/48x48/apps
hicolorapps48_DATA = 48x48/filezilla.png
