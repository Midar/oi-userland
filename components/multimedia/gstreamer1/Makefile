#
# This file and its contents are supplied under the terms of the
# Common Development and Distribution License ("CDDL"), version 1.0.
# You may only use this file in accordance with the terms of version
# 1.0 of the CDDL.
#
# A full copy of the text of the CDDL should have accompanied this
# source.  A copy of the CDDL is also available via the Internet at
# http://www.illumos.org/license/CDDL.
#

#
# Copyright 2016-2018 Aurelien Larcher.  All rights reserved.
# Copyright 2019 Michal Nowak
# Copyright 2021 Tim Mooney.  All rights reserved.
# Copyright 2022-2023 Niklas Poslovski
#

BUILD_STYLE= meson
USE_DEFAULT_TEST_TRANSFORMS = yes

include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=		gstreamer
COMPONENT_VERSION=	1.24.10
COMPONENT_SUMMARY=      GNOME streaming media framework
COMPONENT_PROJECT_URL=  https://gstreamer.freedesktop.org/
COMPONENT_SRC=		$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=      $(COMPONENT_SRC).tar.xz
COMPONENT_ARCHIVE_HASH=	sha256:9fc45b1a332e8f812f09e95c281cd75969f6d1682d062a815db0e7bc047518fd
COMPONENT_ARCHIVE_URL=	$(COMPONENT_PROJECT_URL)/src/$(COMPONENT_NAME)/$(COMPONENT_ARCHIVE)
COMPONENT_FMRI=		library/audio/gstreamer1
COMPONENT_CLASSIFICATION= System/Multimedia Libraries
COMPONENT_LICENSE=	LGPL-2.1-only
COMPONENT_LICENSE_FILE=	COPYING

include $(WS_MAKE_RULES)/common.mk

CONFIGURE_OPTIONS += -Dexamples=disabled
CONFIGURE_OPTIONS += -Dintrospection=enabled
CONFIGURE_OPTIONS += -Dpackage-origin="https://github.com/OpenIndiana/oi-userland"

PYTHON_SCRIPTS += usr/libexec/gstreamer-1.0/gst-plugins-doc-cache-generator

# Install additional file
COMPONENT_POST_INSTALL_ACTION += \
	$(INSTALL) -D files/prof_attr $(PROTOETCSECDIR)/prof_attr.d/library-audio-gstreamer1

# Dynamic library version number
SOVER := 0.$(shell printf '%02s%02s' $(wordlist 2,3,$(subst ., ,$(COMPONENT_VERSION)))).0
SOVER_RE = $(subst .,\.,$(SOVER))

# Replace library version number by SOVER
GENERATE_EXTRA_CMD += | $(GSED) -e 's/$(SOVER_RE)/$$(SOVER)/'

# Testing fails without TZ set
COMPONENT_TEST_ENV += TZ=UTC

# SOVER is needed for manifest processing
PKG_MACROS += SOVER=$(SOVER)

# not picked up by REQUIRED_PACKAGES but still needed
REQUIRED_PACKAGES += library/desktop/gobject/gobject-introspection

# gmp & gsl needed only for the test suite
TEST_REQUIRED_PACKAGES += library/gmp
TEST_REQUIRED_PACKAGES += developer/gsl

# gst-devtools is optional testing dependency.  However, if it is available it
# must be at the same major version as the main gstreamer package to run tests
# successfully.
GST_DEVTOOLS_VERSION = \
	$(shell $(GMAKE) -f $(WS_COMPONENTS)/encumbered/gst-devtools1/Makefile print-value-COMPONENT_VERSION)
ifeq ($(basename $(GST_DEVTOOLS_VERSION)),$(basename $(COMPONENT_VERSION)))
TEST_REQUIRED_PACKAGES += library/audio/gstreamer1/devtools
else
TEST_CONFLICTING_PACKAGES += library/audio/gstreamer1/devtools
endif

# Auto-generated dependencies
PYTHON_REQUIRED_PACKAGES += runtime/python
REQUIRED_PACKAGES += $(GCC_RUNTIME_PKG)
REQUIRED_PACKAGES += library/glib2
REQUIRED_PACKAGES += system/library
REQUIRED_PACKAGES += system/library/math
