lttng.i: lttng.i.in
	sed "s/LTTNG_VERSION_STR/LTTng $(PACKAGE_VERSION)/g" <lttng.i.in >lttng.i

AM_CFLAGS = $(PYTHON_INCLUDE) -I$(top_srcdir)/lib/lttng-ctl -I../common \
              $(BUDDY_CFLAGS)

EXTRA_DIST = lttng.i.in
nodist_python_PYTHON = lttng.py
pyexec_LTLIBRARIES = _lttng.la

MAINTAINERCLEANFILES = lttng_wrap.c lttng.py

nodist__lttng_la_SOURCES = lttng_wrap.c
_lttng_la_LDFLAGS = -module
_lttng_la_LIBADD = 	$(top_srcdir)/src/lib/lttng-ctl/liblttng-ctl.la 		\
			$(top_srcdir)/src/common/sessiond-comm/libsessiond-comm.la		\
			$(top_srcdir)/src/common/libcommon.la

lttng_wrap.c: lttng.i
	$(SWIG) -python -I. -I$(top_srcdir)/src/common/sessiond-comm lttng.i

CLEANFILES = lttng.i lttng.py lttng_wrap.c lttng.pyc
