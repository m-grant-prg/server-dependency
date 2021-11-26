#########################################################################
#									#
# Script ID: src/conf/etc/Makefile.am					#
# Author: Copyright (C) 2018-2019, 2021  Mark Grant			#
#									#
# Released under the GPLv3 only.					#
# SPDX-License-Identifier: GPL-3.0-only					#
#									#
# Purpose:								#
# AutoMake script file to install DOSAB configuration files.		#
#									#
#########################################################################

#########################################################################
#									#
# Changelog								#
#									#
# Date		Author	Version	Description				#
#									#
# 26/09/2018	MG	1.0.1	Initial release.			#
# 29/09/2018	MG	1.0.2	Install example files in docdir.	#
# 20/04/2019	MG	1.0.3	Remove shebang.				#
# 26/11/2021	MG	1.0.4	Tighten SPDX tag.			#
#									#
#########################################################################


confdir = $(sysconfdir)/dosab

example.server.available example.server.list example.server.unavailable \
	server.list: Makefile
	mkdir -p $(@D)
	rm -f $@ $@.tmp
	test -f ./$@.in || srcdir=$(srcdir)/; \
	$(edit) $${srcdir}$(@F).in > $@.tmp
	mv $@.tmp $@
example.server.available: $(srcdir)/example.server.available.in
example.server.list: $(srcdir)/example.server.list.in
example.server.unavailable: $(srcdir)/example.server.unavailable.in
server.list: $(srcdir)/server.list.in

conf_DATA = server.list

doc_DATA = example.server.available example.server.list \
	example.server.unavailable

EXTRA_DIST = $(srcdir)/example.server.available.in example.server.list.in \
	$(srcdir)/example.server.unavailable.in $(srcdir)/server.list.in

CLEANFILES = *.tmp example.server.available example.server.list \
	example.server.unavailable server.list
