
if DARWIN

all: prefpane

.PHONY: prefpane
prefpane:
	( cd $(top_srcdir)/tools/macosx/prefpane; \
	  xcodebuild; \
	)

clean-local:
	( cd $(top_srcdir)/tools/macosx/prefpane; \
	  xcodebuild clean; \
	)

install-exec-local:
	$(INSTALL) -d $(DESTDIR)/Library/Filesystems/fuse-ext2.fs
	$(INSTALL) -d $(DESTDIR)/Library/Filesystems/fuse-ext2.fs/Support
	$(INSTALL) -d $(DESTDIR)/Library/Filesystems/fuse-ext2.fs/Contents
	$(INSTALL) -d $(DESTDIR)/Library/Filesystems/fuse-ext2.fs/Contents/Resources
	$(INSTALL) -d $(DESTDIR)/Library/Filesystems/fuse-ext2.fs/Contents/Resources/English.lproj
	$(INSTALL) -m 755 $(top_srcdir)/tools/macosx/fuse-ext2.fs/fuse-ext2.util $(DESTDIR)/Library/Filesystems/fuse-ext2.fs/fuse-ext2.util
	$(INSTALL) -m 755 $(top_srcdir)/tools/macosx/fuse-ext2.fs/Contents/Resources/mount_fuse-ext2 $(DESTDIR)/Library/Filesystems/fuse-ext2.fs/Contents/Resources/mount_fuse-ext2
	sed "s/FUSEEXT2_VERSION_LITERAL/$(VERSION)/g" < $(top_srcdir)/tools/macosx/fuse-ext2.fs/Contents/Info.plist.in > $(top_srcdir)/tools/macosx/fuse-ext2.fs/Contents/Info.plist
	$(INSTALL) -m 644 $(top_srcdir)/tools/macosx/fuse-ext2.fs/Contents/Info.plist $(DESTDIR)/Library/Filesystems/fuse-ext2.fs/Contents/Info.plist
	$(INSTALL) -m 644 $(top_srcdir)/tools/macosx/fuse-ext2.fs/Contents/PkgInfo $(DESTDIR)/Library/Filesystems/fuse-ext2.fs/Contents/PkgInfo
	$(INSTALL) -m 644 $(top_srcdir)/tools/macosx/fuse-ext2.fs/Contents/Resources/English.lproj/InfoPlist.strings $(DESTDIR)/Library/Filesystems/fuse-ext2.fs/Contents/Resources/English.lproj/InfoPlist.strings
	$(INSTALL) -d $(DESTDIR)/Library/PreferencePanes
	cp -R $(top_srcdir)/tools/macosx/prefpane/build/Release/fuse-ext2.prefPane $(DESTDIR)/Library/PreferencePanes/fuse-ext2.prefPane

endif
