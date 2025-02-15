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
# Copyright 2015 Aurelien Larcher
#

# disable CONFIGURE_DEFAULT_DIRS, because libjpeg6-ijg does not support --localdir
CONFIGURE_DEFAULT_DIRS=no

BUILD_BITS=32_and_64
include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=		libjpeg6-ijg
COMPONENT_VERSION=	6.0.2
LIBJPEG_API_VERSION= 6b
COMPONENT_REVISION=	4
COMPONENT_FMRI= 	image/library/libjpeg6-ijg
COMPONENT_PROJECT_URL=	http://www.ijg.org/
COMPONENT_SUMMARY=	libjpeg - Independent JPEG Group library version 6b
COMPONENT_SRC=		jpeg-$(LIBJPEG_API_VERSION)
COMPONENT_ARCHIVE=	$(COMPONENT_NAME)-$(COMPONENT_VERSION).tar.gz
COMPONENT_ARCHIVE_HASH=	\
 sha256:75c3ec241e9996504fe02a9ed4d12f16b74ade713972f3db9e65ce95cd27e35d
COMPONENT_ARCHIVE_URL=	http://www.ijg.org/files/jpegsrc.v$(LIBJPEG_API_VERSION).tar.gz
COMPONENT_LICENSE=	IJG,GPLv2.0
COMPONENT_CLASSIFICATION=System/Multimedia Libraries

include $(WS_MAKE_RULES)/common.mk

CONFIGURE_DEFAULT_DIRS=no

CONFIGURE_OPTIONS+= --enable-shared
CONFIGURE_OPTIONS+= --disable-static
CONFIGURE_OPTIONS+= --mandir=$(CONFIGURE_MANDIR)
CONFIGURE_OPTIONS+= --includedir=$(CONFIGURE_INCLUDEDIR)/$(COMPONENT_NAME)
CONFIGURE_OPTIONS.32+= --bindir=$(USRLIBDIR)/$(COMPONENT_NAME)/bin
CONFIGURE_OPTIONS.32+= --libdir=$(USRLIBDIR)/$(COMPONENT_NAME)/lib
CONFIGURE_OPTIONS.64+= --bindir=$(USRLIBDIR)/$(COMPONENT_NAME)/bin/$(MACH64)
CONFIGURE_OPTIONS.64+= --libdir=$(USRLIBDIR)/$(COMPONENT_NAME)/lib/$(MACH64)

# Auto-generated dependencies
REQUIRED_PACKAGES += system/library
