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
# Copyright 2015 Alexander Pyhalov
#

include ../../../make-rules/shared-macros.mk

COMPONENT_NAME= imf-selector
COMPONENT_VERSION= 0.5.11
COMPONENT_SUMMARY= Input Method Framework startup
COMPONENT_SRC = src
COMPONENT_PROJECT_URL = http://www.openindiana.org
COMPONENT_FMRI = system/input-method/imf-startup
COMPONENT_LICENSE_FILE = OPENSOLARIS.LICENSE
COMPONENT_LICENSE = CDDL
COMPONENT_CLASSIFICATION = System/Internationalization

include $(WS_TOP)/make-rules/configure.mk
include $(WS_TOP)/make-rules/ips.mk

clobber: clean

$(SOURCE_DIR)/.prep:	Makefile
	$(TOUCH) $@

PATH=/usr/gnu/bin:/usr/bin

# Missing files in build dir for configure without this.
COMPONENT_PRE_CONFIGURE_ACTION =        (cp -a $(SOURCE_DIR)/* $(@D))

CONFIGURE_SCRIPT = $(@D)/autogen.sh

CONFIGURE_OPTIONS += --sysconfdir=/etc

COMPONENT_POST_INSTALL_ACTION = ( $(GSED) -i -e 's:\#!/bin/python:\#!/usr/bin/python$(PYTHON_VERSION):' $(PROTO_DIR)/usr/bin/imf-selector)

clean::
	$(RM) $(SOURCE_DIR)/.prep
	$(RM) -rf $(BUILD_DIR)

download:

build: $(BUILD_32)

install: $(INSTALL_32)

test: $(NO_TESTS)
