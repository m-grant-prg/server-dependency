#! /usr/bin/env bash
#########################################################################
#									#
# Script ID: src/systemd/Makefile.am					#
# Author: Copyright (C) 2018  Mark Grant				#
#									#
# Released under the GPLv3 only.					#
# SPDX-License-Identifier: GPL-3.0					#
#									#
# Purpose:								#
#	AutoMake script file to install systemd service file.		#
#									#
#########################################################################

#########################################################################
#									#
# Changelog								#
#									#
# Date		Author	Version	Description				#
#									#
# 28/09/2018	MG	1.0.1	First release. This only gets executed	#
#				if configure is run with		#
#				--enable-systemd=yes.			#
#									#
#########################################################################

systemddir = $(libdir)/systemd/system

dosab.service: Makefile
	mkdir -p $(@D)
	rm -f $@ $@.tmp
	test -f ./$@.in || srcdir=$(srcdir)/; \
	$(edit) $${srcdir}$(@F).in > $@.tmp
	mv $@.tmp $@
dosab.service: $(srcdir)/dosab.service.in


systemd_DATA = dosab.service


install-data-hook:
	systemctl enable dosab.service
	systemctl start dosab.service


uninstall-local:
	systemctl stop dosab.service
	systemctl disable dosab.service


EXTRA_DIST = $(srcdir)/dosab.service.in

CLEANFILES = *.tmp dosab.service
