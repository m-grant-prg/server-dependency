#########################################################################
#									#
# Script ID: src/prg/bash/Makefile.am					#
# Author: Copyright (C) 2018-2019, 2021, 2023  Mark Grant		#
#									#
# Released under the GPLv3 only.					#
# SPDX-License-Identifier: GPL-3.0-only					#
#									#
# Purpose:								#
# AutoMake script file to generate dosab script from source.		#
#									#
#########################################################################

#########################################################################
#									#
# Changelog								#
#									#
# Date		Author	Version	Description				#
#									#
# 27/09/2018	MG	1.0.1	Initial release.			#
# 20/04/2019	MG	1.0.2	Remove shebang.				#
# 24/08/2021	MG	1.0.3	Correct systemd action ordering.	#
# 26/11/2021	MG	1.0.4	Tighten SPDX tag.			#
# 16/10/2023	MG	1.0.5	Drop .sh extension from scripts in	#
#				$PATH.					#
#									#
#########################################################################

#########################################################################
#									#
# N.B.									#
# ====									#
# The sequence of the build is important for systemd, see below.	#
#									#
#########################################################################


dosab: Makefile
	mkdir -p $(@D)
	rm -f $@ $@.tmp
	test -f ./$@.in || srcdir=$(srcdir)/; \
	$(edit) $${srcdir}$(@F).sh.in > $@.tmp
	mv $@.tmp $@
	chmod a+x $@
dosab: $(srcdir)/dosab.sh.in


sbin_SCRIPTS = dosab


# systemd requires some ordering of it's actions. Please refer to the comment in
# the top-level Makefile.am
if SYSD
uninstall-local:
	systemctl disable dosab.service
endif


EXTRA_DIST = $(srcdir)/dosab.sh.in

CLEANFILES = *.tmp dosab

