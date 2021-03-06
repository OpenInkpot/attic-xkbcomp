dnl  Copyright 2005 Red Hat, Inc.
dnl 
dnl  Permission to use, copy, modify, distribute, and sell this software and its
dnl  documentation for any purpose is hereby granted without fee, provided that
dnl  the above copyright notice appear in all copies and that both that
dnl  copyright notice and this permission notice appear in supporting
dnl  documentation, and that the name of Red Hat not be used in
dnl  advertising or publicity pertaining to distribution of the software without
dnl  specific, written prior permission.  Red Hat makes no
dnl  representations about the suitability of this software for any purpose.  It
dnl  is provided "as is" without express or implied warranty.
dnl 
dnl  RED HAT DISCLAIMS ALL WARRANTIES WITH REGARD TO THIS SOFTWARE,
dnl  INCLUDING ALL IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS, IN NO
dnl  EVENT SHALL RED HAT BE LIABLE FOR ANY SPECIAL, INDIRECT OR
dnl  CONSEQUENTIAL DAMAGES OR ANY DAMAGES WHATSOEVER RESULTING FROM LOSS OF USE,
dnl  DATA OR PROFITS, WHETHER IN AN ACTION OF CONTRACT, NEGLIGENCE OR OTHER
dnl  TORTIOUS ACTION, ARISING OUT OF OR IN CONNECTION WITH THE USE OR
dnl  PERFORMANCE OF THIS SOFTWARE.
dnl
dnl Process this file with autoconf to create configure.

AC_PREREQ([2.57])
AC_INIT(xkbcomp,[1.0.5], [https://bugs.freedesktop.org/enter_bug.cgi?product=xorg],xkbcomp)
AM_INIT_AUTOMAKE([dist-bzip2])
AM_MAINTAINER_MODE

# Require xorg-macros: XORG_CWARNFLAGS, XORG_CHANGELOG
m4_ifndef([XORG_MACROS_VERSION], [AC_FATAL([must install xorg-macros 1.2 or later before running autoconf/autogen])])
XORG_MACROS_VERSION(1.2)

AM_CONFIG_HEADER(config.h)

AC_PROG_CC
AC_PROG_YACC
AC_PROG_INSTALL

XORG_CWARNFLAGS

AC_CHECK_FUNCS([strdup strcasecmp])

# Checks for pkg-config packages
PKG_CHECK_MODULES(XKBCOMP, x11 xkbfile)
XKBCOMP_CFLAGS="$CWARNFLAGS $XKBCOMP_CFLAGS"
AC_SUBST(XKBCOMP_CFLAGS)
AC_SUBST(XKBCOMP_LIBS)

AC_ARG_WITH([xkb_config_root],
    [AC_HELP_STRING([--with-xkb-config-root=<paths>],
        [Set default XKB config root (default: ${datadir}/X11/xkb)])],
    [XKBCONFIGROOT="$withval"],
    [XKBCONFIGROOT='${datadir}/X11/xkb'])
AC_SUBST([XKBCONFIGROOT])

XORG_MANPAGE_SECTIONS
XORG_RELEASE_VERSION
XORG_CHANGELOG

AC_OUTPUT([Makefile])
