#
# This file and its contents are supplied under the terms of the
# Common Development and Distribution License ("CDDL)". You may
# only use this file in accordance with the terms of the CDDL.
#
# A full copy of the text of the CDDL should have accompanied this
# source. A copy of the CDDL is also available via the Internet at
# http://www.illumos.org/license/CDDL.
#

#
# Copyright (c) 2013 Ken Mays
# Copyright 2019, Michal Nowak
#

BUILD_BITS=64

include ../../../../make-rules/shared-macros.mk

COMPONENT_NAME=         brasero
COMPONENT_VERSION=      3.12.3
COMPONENT_REVISION=     2
COMPONENT_PROJECT_URL=  https://projects.gnome.org/brasero/
COMPONENT_SUMMARY=      Gnome CD/DVD burner
COMPONENT_SRC=          $(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=      $(COMPONENT_SRC).tar.xz
COMPONENT_ARCHIVE_HASH= sha256:87749eae33a141207d1b00be233b6d8045982ed3249ed4b98dae1f3a975fea15
COMPONENT_ARCHIVE_URL=  https://download.gnome.org/sources/$(COMPONENT_NAME)/3.12/$(COMPONENT_ARCHIVE)
COMPONENT_FMRI=         desktop/cd-burning/brasero
COMPONENT_CLASSIFICATION=Applications/Internet
COMPONENT_LICENSE=      GPLv2
COMPONENT_LICENSE_FILE= COPYING

TEST_TARGET=		$(NO_TESTS)

include $(WS_MAKE_RULES)/common.mk

PATH=$(PATH.gnu)

# Regenerate yelp rules
COMPONENT_PREP_ACTION = ( cd $(@D) ; autoreconf -vif ) 

CONFIGURE_OPTIONS+=	--sysconfdir=/etc
CONFIGURE_OPTIONS.32+=	--libexecdir=/usr/lib
CONFIGURE_OPTIONS.64+=	--libexecdir=/usr/lib/$(MACH64)
CONFIGURE_OPTIONS+=	--localstatedir=/var
CONFIGURE_OPTIONS+=	--enable-shared
CONFIGURE_OPTIONS+=	--disable-static
CONFIGURE_OPTIONS+=	--enable-search
CONFIGURE_OPTIONS+=	--enable-playlist
CONFIGURE_OPTIONS+=	--disable-nautilus
CONFIGURE_OPTIONS.64+=	--enable-introspection
CONFIGURE_OPTIONS+=	--enable-libburnia
CONFIGURE_OPTIONS+=	--disable-gtk-doc
CONFIGURE_OPTIONS+=	--disable-inotify
CONFIGURE_OPTIONS+=	--disable-maintainer-mode

COMPONENT_BUILD_ENV += CC="$(CC)"
COMPONENT_BUILD_ENV += CFLAGS="$(CFLAGS)"

# build dependency
REQUIRED_PACKAGES += developer/documentation-tool/gtk-doc
REQUIRED_PACKAGES += library/gnome/yelp-tools

# Auto-generated dependencies
REQUIRED_PACKAGES += library/audio/gstreamer1
REQUIRED_PACKAGES += library/audio/gstreamer1/plugin/base
REQUIRED_PACKAGES += library/desktop/cairo
REQUIRED_PACKAGES += library/desktop/gdk-pixbuf
REQUIRED_PACKAGES += library/desktop/gtk3
REQUIRED_PACKAGES += library/desktop/pango
REQUIRED_PACKAGES += library/desktop/search/tracker
REQUIRED_PACKAGES += library/desktop/xdg/libcanberra
REQUIRED_PACKAGES += library/glib2
REQUIRED_PACKAGES += library/libnotify
REQUIRED_PACKAGES += library/libxml2
REQUIRED_PACKAGES += library/media-player/totem-pl-parser
REQUIRED_PACKAGES += media/cdrtools
REQUIRED_PACKAGES += media/dvd+rw-tools
REQUIRED_PACKAGES += system/library
REQUIRED_PACKAGES += system/library/math
