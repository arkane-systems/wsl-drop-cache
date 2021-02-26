#
# Debian Makefile.
#

# Installation locations.

DESTDIR=debian/wsl-drop-caches

BINDIR = $(DESTDIR)/usr/sbin
SVCDIR = $(DESTDIR)/lib/systemd/system

#
# Default target: package.
#

package:
	# Packaging for Debian.
	debuild

package-inner:
	# Innermost iteration; invoked by debuild.

	# Binaries.
	install -Dm 0755 -o root drop_cache_if_idle -t "$(BINDIR)"

	# Unit files.
	install -Dm 0644 -o root wsl-drop-caches.service -t "$(SVCDIR)"
	install -Dm 0644 -o root wsl-drop-caches.timer -t "$(SVCDIR)"

clean:
	debuild -- clean
