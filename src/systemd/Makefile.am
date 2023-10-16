#########################################################################
#									#
# Author: Copyright (C) 2018-2019, 2021, 2023  Mark Grant		#
#									#
# Released under the GPLv3 only.					#
# SPDX-License-Identifier: GPL-3.0-only					#
#									#
# Purpose:								#
#	AutoMake script file to install systemd service file.		#
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

# systemd requires some ordering of it's actions. Please refer to the comment in
# the top-level Makefile.am
install-data-hook:
	systemctl enable dosab.service
	systemctl start dosab.service

uninstall-hook:
	systemctl daemon-reload

EXTRA_DIST = $(srcdir)/dosab.service.in

CLEANFILES = *.tmp dosab.service
