#########################################################################
#									#
# Script ID: src/prg/bash/Makefile.am					#
# Author: Copyright (C) 2018-2019  Mark Grant				#
#									#
# Released under the GPLv3 only.					#
# SPDX-License-Identifier: GPL-3.0					#
#									#
# Purpose:								#
# AutoMake script file to generate dosab.sh script from source.		#
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


EXTRA_DIST = $(srcdir)/dosab.sh.in

CLEANFILES = *.tmp dosab.sh
