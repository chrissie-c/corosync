# Copyright (c) 2009 Red Hat, Inc.
#
# Authors: Andrew Beekhof
#	   Steven Dake (sdake@redhat.com)
#
# This software licensed under BSD license, the text of which follows:
#
# Redistribution and use in source and binary forms, with or without
# modification, are permitted provided that the following conditions are met:
#
# - Redistributions of source code must retain the above copyright notice,
#   this list of conditions and the following disclaimer.
# - Redistributions in binary form must reproduce the above copyright notice,
#   this list of conditions and the following disclaimer in the documentation
#   and/or other materials provided with the distribution.
# - Neither the name of the MontaVista Software, Inc. nor the names of its
#   contributors may be used to endorse or promote products derived from this
#   software without specific prior written permission.
#
# THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
# AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
# IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE
# ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE
# LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR
# CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF
# SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS
# INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN
# CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE)
# ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF
# THE POSSIBILITY OF SUCH DAMAGE.

MAINTAINERCLEANFILES	= Makefile.in

noinst_HEADERS		= apidef.h cs_queue.h logconfig.h main.h \
			  quorum.h service.h timer.h totemconfig.h \
			  totemnet.h totemudp.h \
			  totemudpu.h totemsrp.h util.h vsf.h \
			  schedwrk.h sync.h fsm.h votequorum.h vsf_ykd.h \
			  totemknet.h stats.h ipcs_stats.h

sbin_PROGRAMS		= corosync

corosync_SOURCES	= vsf_ykd.c coroparse.c vsf_quorum.c sync.c \
			  logsys.c cfg.c cmap.c cpg.c pload.c \
			  votequorum.c util.c schedwrk.c main.c \
			  apidef.c quorum.c icmap.c timer.c stats.c \
			  ipc_glue.c service.c logconfig.c totemconfig.c \
			  totemip.c totemnet.c totemudp.c \
			  totemudpu.c totemsrp.c \
			  totempg.c totemknet.c

if BUILD_MONITORING
corosync_SOURCES	+= mon.c
endif

if BUILD_WATCHDOG
corosync_SOURCES	+= wd.c
endif

corosync_CPPFLAGS	= -DLOGCONFIG_USE_ICMAP=1

corosync_CFLAGS         = $(statgrab_CFLAGS) $(libsystemd_CFLAGS) $(knet_CFLAGS) $(nozzle_CFLAGS)

corosync_LDADD		= ../common_lib/libcorosync_common.la \
			  $(LIBQB_LIBS) $(statgrab_LIBS) $(libsystemd_LIBS) $(knet_LIBS) $(nozzle_LIBS)

corosync_DEPENDENCIES	= ../common_lib/libcorosync_common.la

lint:
	-splint $(LINT_FLAGS) $(CPPFLAGS) $(CFLAGS) *.c
