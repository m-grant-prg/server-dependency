#########################################################################
#									#
# Author: Copyright (C) 2018-2019, 2021, 2023  Mark Grant		#
#									#
# Released under the GPLv3 only.					#
# SPDX-License-Identifier: GPL-3.0-only					#
#									#
# Purpose:								#
# AutoMake script file to generate dosab.sh script from source.		#
#									#
#########################################################################

#########################################################################
#									#
# N.B.									#
# ====									#
# The sequence of the build is important for systemd, see below.	#
#									#
#########################################################################


dosab.sh: Makefile
	mkdir -p $(@D)
	rm -f $@ $@.tmp
	test -f ./$@.in || srcdir=$(srcdir)/; \
	$(edit) $${srcdir}$(@F).in > $@.tmp
	mv $@.tmp $@
	chmod a+x $@
dosab.sh: $(srcdir)/dosab.sh.in


sbin_SCRIPTS = dosab.sh


# systemd requires some ordering of it's actions. Please refer to the comment in
# the top-level Makefile.am
if SYSD
uninstall-local:
	systemctl disable dosab.service
endif


EXTRA_DIST = $(srcdir)/dosab.sh.in

CLEANFILES = *.tmp dosab.sh

