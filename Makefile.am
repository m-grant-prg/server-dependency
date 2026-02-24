#########################################################################
#									#
# Author: Copyright (C) 2018-2019, 2021, 2023, 2025, 2026  Mark Grant	#
#									#
# Released under the GPLv3 only.					#
# SPDX-License-Identifier: GPL-3.0-only					#
#									#
# Purpose:								#
# AutoMake script file to generate Dependency on Server At Boot project	#
# from source.								#
#									#
#########################################################################

#########################################################################
#									#
# N.B.									#
# ====									#
# The sequence of the build is important for systemd, see below.	#
#									#
#########################################################################


ACLOCAL_AMFLAGS = -I m4


SUBDIRS = src/bash-comp
SUBDIRS += src/conf/etc
SUBDIRS += src/man/5 src/man/8

# systemd requires the ordering of certain actions, so:-
# Install
#	bash
#	service
#	service-post (hook)
#		enable service
#		start service
# Uninstall
#	bash-pre (local)
#		disable service
#	bash
#	service
#	service-post (hook)
#		daemon reload
SUBDIRS += src/prg/bash
if SYSD
SUBDIRS += src/systemd
endif


doc_DATA = AUTHORS ChangeLog COPYING NEWS README


EXTRA_DIST = $(srcdir)/AUTHORS $(srcdir)/ChangeLog $(srcdir)/COPYING
EXTRA_DIST += $(srcdir)/NEWS $(srcdir)/README
EXTRA_DIST += $(srcdir)/misc


srctarball:
	@cwd="$${PWD}" && \
	targ="$${cwd}/@PACKAGE_TARNAME@-@PACKAGE_VERSION@.tar.gz" && \
	cd @srcdir@ && \
	echo "making srctarball from @srcdir@" && \
	echo "GA	$${targ}" && \
	git archive --format=tar.gz \
		--prefix=@PACKAGE_TARNAME@-@PACKAGE_VERSION@/ \
		--output=$${targ} \
		HEAD && \
	cd -


sign_tarball:
	rm -f @PACKAGE_TARNAME@-@PACKAGE_VERSION@.tar.gz.asc
	gpg --armor --detach-sign @PACKAGE_TARNAME@-@PACKAGE_VERSION@.tar.gz

