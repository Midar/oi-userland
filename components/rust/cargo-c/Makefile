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
# Copyright 2024 Marcel Telka
#

BUILD_STYLE = cargo

include ../../../make-rules/shared-macros.mk

COMPONENT_NAME =		cargo-c
HUMAN_VERSION =			0.10.7+cargo-0.84.0
COMPONENT_SUMMARY =		Helper program to build and install c-like libraries
COMPONENT_ARCHIVE_HASH =	\
	sha256:333b19a1a1dc397a8b4eec0a9a48af214637f1e2b87a2526273ebdf36729ea12
COMPONENT_FMRI =		developer/cargo-c
COMPONENT_CLASSIFICATION =	Development/Other Languages
COMPONENT_LICENSE =		MIT
COMPONENT_LICENSE_FILE =	LICENSE

include $(WS_MAKE_RULES)/common.mk

# Auto-generated dependencies
REQUIRED_PACKAGES += $(GCC_RUNTIME_PKG)
REQUIRED_PACKAGES += $(OPENSSL_PKG)
REQUIRED_PACKAGES += library/libgit2
REQUIRED_PACKAGES += library/zlib
REQUIRED_PACKAGES += system/library
REQUIRED_PACKAGES += system/library/math
REQUIRED_PACKAGES += web/curl
