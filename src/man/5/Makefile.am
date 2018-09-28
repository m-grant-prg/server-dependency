#! /usr/bin/env bash
#########################################################################
#									#
# Script ID: src/man/5/Makefile.am					#
# Author: Copyright (C) 2018  Mark Grant				#
#									#
# Released under the GPLv3 only.					#
# SPDX-License-Identifier: GPL-3.0					#
#									#
# Purpose:								#
# AutoMake script file to generate dosab manual pages from source.	#
#									#
#########################################################################

#########################################################################
#									#
# Changelog								#
#									#
# Date		Author	Version	Description				#
#									#
# 27/09/2018	MG	1.0.1	Initial release.			#
#									#
#########################################################################


server.list.5: Makefile
	mkdir -p $(@D)
	rm -f $@ $@.tmp
	$(edit) $(srcdir)/$(@F).man.in > $@.tmp
	targfile=$(@F);	\
	if [[ $$targfile == *"."* ]]; then \
		if [[ $${targfile##*.} == "" ]]; then \
			echo "Source file suffix used as section but empty."; \
			exit 1; \
		else \
			section=$${targfile##*.}; \
		fi; \
	else \
		echo "Source file suffix used as section but no dot & empty."; \
		exit 1; \
	fi; \
	txt2manwrap $(@F) $$section "Dependency On Server At Boot Manual" \
		$@.tmp $@
	rm -f $@.tmp

server.list.5: $(srcdir)/server.list.5.man.in

man_MANS = server.list.5

EXTRA_DIST = $(srcdir)/server.list.5.man.in

CLEANFILES = *.tmp server.list.5
