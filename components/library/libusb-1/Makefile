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
# Copyright (c) 2016, Oracle and/or its affiliates. All rights reserved.
#

BUILD_BITS= 32_and_64
include ../../../make-rules/shared-macros.mk

COMPONENT_NAME= libusb
COMPONENT_VERSION= 1.0.27
COMPONENT_SUMMARY= A cross-platform user library to access USB devices
COMPONENT_SRC= $(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE= $(COMPONENT_SRC).tar.bz2
COMPONENT_ARCHIVE_HASH= sha256:ffaa41d741a8a3bee244ac8e54a72ea05bf2879663c098c82fc5757853441575
COMPONENT_ARCHIVE_URL= https://github.com/libusb/libusb/releases/download/v$(COMPONENT_VERSION)/$(COMPONENT_ARCHIVE)
COMPONENT_PROJECT_URL= https://libusb.info/
COMPONENT_FMRI= library/libusb-1
COMPONENT_CLASSIFICATION= Development/C
COMPONENT_LICENSE= LGPL-2.1-only
COMPONENT_LICENSE_FILE= COPYING

include $(WS_MAKE_RULES)/common.mk

CFLAGS += $(XPG6MODE)

# Find issues with undefined symbols in build time
LD_OPTIONS += $(LD_Z_DEFS)

CONFIGURE_OPTIONS += --enable-static=no
CONFIGURE_OPTIONS += --enable-log
CONFIGURE_OPTIONS += --enable-tests-build

COMPONENT_BUILD_ARGS += "LDFLAGS=$(LDFLAGS) -lnvpair"
COMPONENT_BUILD_ARGS += "INSTALL=$(INSTALL)"
COMPONENT_BUILD_ARGS += "MAKE=$(GMAKE)"

# Test target just runs the 'stress' binary; requires Global Zone
COMPONENT_TEST_TARGETS=
COMPONENT_TEST_ENV_CMD=
COMPONENT_TEST_DIR = $(@D)/tests
COMPONENT_TEST_CMD= ./stress

# Build dependencies
REQUIRED_PACKAGES += system/header/header-usb
REQUIRED_PACKAGES += system/header/header-ugen

# Auto-generated dependencies
REQUIRED_PACKAGES += system/library
