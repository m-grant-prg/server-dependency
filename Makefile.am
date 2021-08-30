#########################################################################
#									#
# Script ID: ./Makefile.am						#
# Author: Copyright (C) 2018-2019, 2021  Mark Grant			#
#									#
# Released under the GPLv3 only.					#
# SPDX-License-Identifier: GPL-3.0					#
#									#
# Purpose:								#
# AutoMake script file to generate Dependency on Server At Boot project	#
# from source.								#
#									#
#########################################################################

#########################################################################
#									#
# Changelog								#
#									#
# Date		Author	Version	Description				#
#									#
# 28/09/2018	MG	1.0.1	Initial release.			#
# 01/11/2018	MG	1.0.2	Change srctarball target to build with	#
#				src between package name and version in	#
#				filename.				#
# 20/04/2019	MG	1.0.3	Remove shebang.				#
#				Make source tarball name == GitHub.	#
#				Add install of standard GNU files like	#
#				AUTHORS, etc.				#
# 24/08/2021	MG	1.0.4	Correct systemd action ordering.	#
# 30/08/2021	MG	1.0.5	Add misc subdir to DIST.		#
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


SUBDIRS = src/conf/etc
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

