# xrroot - xrandr-aware hsetroot
# Copyright (C) 2003 Hyriand - See COPYING
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA
#
# Process this file with autoconf to produce a configure script.
# 

AC_PREREQ(2.52)
AC_INIT([xrroot], [1.0.3], [djpohly@gmail.com])
AC_CONFIG_AUX_DIR(config)
AM_INIT_AUTOMAKE

# Checks for programs.
AC_PROG_CC

# default set of CFLAGS (override this with ./configure CFLAGS=foo)
CFLAGS=${CFLAGS:=-O2 -g -Wall}

# Checks for header files.
AC_HEADER_STDC
AC_CHECK_HEADERS([string.h])

# Checks for typedefs, structures, and compiler characteristics.
AC_C_CONST

# Check for X11 and XRandR
AC_CHECK_HEADERS([X11/Xlib.h], [],
                 [AC_ERROR([Missing libx11 headers])])
AC_SEARCH_LIBS([XOpenDisplay], [X11], [],
               [AC_ERROR([Missing libx11 libraries])])

AC_CHECK_HEADERS([X11/extensions/Xrandr.h], [],
                 [AC_ERROR([Missing libxrandr headers])])
AC_SEARCH_LIBS([XRRGetScreenResources], [Xrandr], [],
               [AC_ERROR([Missing libxrandr libraries])])

# Check for imlib2
AC_CHECK_HEADERS([Imlib2.h], [],
                 [AC_ERROR([Missing Imlib2 headers])])
AC_SEARCH_LIBS([imlib_context_new], [Imlib2], [],
               [AC_ERROR([Missing Imlib2 libraries])])

# Some extra definitions for config.h
AC_DEFINE(DESCRIPTION, "xrandr-aware hsetroot", [single line package description])

AM_CONFIG_HEADER(config/config.h)
AC_CONFIG_FILES([Makefile src/Makefile config/Makefile])

AC_OUTPUT
