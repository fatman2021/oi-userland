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
# Copyright (c) 2016 Aurelien Larcher
#

include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=		libepoxy
COMPONENT_VERSION=	1.3.1
COMPONENT_FMRI=		x11/library/libepoxy
COMPONENT_CLASSIFICATION=	System/Hardware
COMPONENT_PROJECT_URL=	http://xorg.freedesktop.org
COMPONENT_SUMMARY=	library for handling OpenGL function pointers
COMPONENT_SRC=		$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=	$(COMPONENT_SRC).tar.bz2
COMPONENT_ARCHIVE_HASH=	\
    sha256:1d8668b0a259c709899e1c4bab62d756d9002d546ce4f59c9665e2fc5f001a64
COMPONENT_ARCHIVE_URL=	\
    https://github.com/anholt/libepoxy/releases/download/v$(COMPONENT_VERSION)/$(COMPONENT_ARCHIVE)
COMPONENT_LICENSE_FILE=	$(COMPONENT_NAME).license
COMPONENT_LICENSE=	MIT

include $(WS_TOP)/make-rules/prep.mk
include $(WS_TOP)/make-rules/configure.mk
include $(WS_TOP)/make-rules/ips.mk

# Missing files in build dir for configure without this.
COMPONENT_PREP_ACTION =        (cd $(@D) && \
                                        libtoolize --automake --copy --force && \
                                        aclocal -Im4 && \
                                        autoheader && \
                                        automake -a -f -c &&\
                                        autoconf )

PATH=/usr/gnu/bin:/usr/bin

# common targets
build:		$(BUILD_32_and_64)

install:	$(INSTALL_32_and_64)

test:		$(NO_TESTS)

REQUIRED_PACKAGES += system/library
