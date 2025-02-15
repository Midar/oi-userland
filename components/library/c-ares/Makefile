#
# CDDL HEADER START
#
# The contents of this file are subject to the terms of the
# Common Development and Distribution License (the "License").
# You may not use this file except in compliance with the License.
#
# You can obtain a copy of the license at usr/src/OPENSOLARIS.LICENSE
# or http://www.opensolaris.org/os/licensing.
# See the License for the specific language governing permissions
# and limitations under the License.
#
# When distributing Covered Code, include this CDDL HEADER in each
# file and include the License file at usr/src/OPENSOLARIS.LICENSE.
# If applicable, add the following below this CDDL HEADER, with the
# fields enclosed by brackets "[]" replaced with your own identifying
# information: Portions Copyright [yyyy] [name of copyright owner]
#
# CDDL HEADER END
#

#
# Copyright (c) 2020, Oracle and/or its affiliates.
# Copyright (c) 2024, Andreas Wacknitz.
#

USE_DEFAULT_TEST_TRANSFORMS= yes
include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=		c-ares
COMPONENT_VERSION=	1.34.3
COMPONENT_SUMMARY=	c-ares - C library for asynchronous DNS requests
COMPONENT_DESCRIPTION=	c-ares is a C library for asynchronous DNS requests including name resolves
COMPONENT_PROJECT_URL=	https://c-ares.haxx.se/
COMPONENT_SRC=          $(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=      $(COMPONENT_SRC).tar.gz
COMPONENT_ARCHIVE_HASH= sha256:26e1f7771da23e42a18fdf1e58912a396629e53a2ac71b130af93bbcfb90adbe
COMPONENT_ARCHIVE_URL=	https://github.com/c-ares/c-ares/releases/download/v$(COMPONENT_VERSION)/$(COMPONENT_ARCHIVE)
COMPONENT_FMRI=		library/libcares
COMPONENT_CLASSIFICATION=	System/Libraries
COMPONENT_LICENSE=		MIT
COMPONENT_LICENSE_FILE=	LICENSE.md

include $(WS_MAKE_RULES)/common.mk

CFLAGS += $(XPG6MODE)

CONFIGURE_OPTIONS += --enable-static=no
CONFIGURE_OPTIONS += --disable-dependency-tracking

# At the moment we have 10 failing tests (out of 1110 total tests)

# Manually added dependencies
TEST_REQUIRED_PACKAGES += developer/googletest

# Auto-generated dependencies
REQUIRED_PACKAGES += system/library
