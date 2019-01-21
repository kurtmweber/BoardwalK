#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.69])
AC_INIT([BoardwalK], [0.1], [boardwalk-bugs@kurtweber.us])
AC_CONFIG_SRCDIR([client/client.cpp])
AC_CONFIG_HEADERS([config.h])

AM_INIT_AUTOMAKE

AM_MAINTAINER_MODE

# Checks for programs.
AC_PROG_CXX
AC_PROG_CC

# Checks for libraries.

# Checks for header files.
AC_CHECK_HEADERS([unistd.h])

# Checks for typedefs, structures, and compiler characteristics.

# Checks for library functions.
AC_LANG_CPLUSPLUS

CLIENT_LIBS=$LIBS

AC_MSG_CHECKING([for libkdecore])
SAVED_LIBS=$LIBS
LIBS="$LIBS -lkdecore"
AC_LINK_IFELSE(
  [AC_LANG_PROGRAM([#include <KLocale>], 
    [ki18n("test")])],
  [CLIENT_LIBS="$CLIENT_LIBS -lkdecore"] 
  [HAVE_KDECORE=1]
  [AC_MSG_RESULT([found])], 
  [AC_MSG_ERROR([libkdecore is not installed.])])

AC_MSG_CHECKING([for libQtCore])
SAVED_LIBS=$LIBS
LIBS="$LIBS -lQtCore"
AC_LINK_IFELSE(
	[AC_LANG_PROGRAM([void qFree(void *ptr);],
	[qFree(0)])],
	[CLIENT_LIBS="$CLIENT_LIBS -lQtCore"]
	[HAVE_QTCORE=1]
	[AC_MSG_RESULT([found])],
	[AC_MSG_ERROR([libQtCore is not installed.])])

AC_MSG_CHECKING([for libkdeui])
SAVED_LIBS=$LIBS
LIBS="$LIBS -lkdeui"
AC_LINK_IFELSE(
	[AC_LANG_PROGRAM([#include <KApplication>],
	[KApplication app(true)]	)],
	[CLIENT_LIBS="$CLIENT_LIBS -lkdeui"]
	[HAVE_KDEUI=1]
	[AC_MSG_RESULT([found])],
	[AC_MSG_ERROR([libkdeui is not installed.])])

AC_SUBST(CLIENT_LIBS)

LIBS=$SAVED_LIBS

AC_CONFIG_FILES(Makefile client/Makefile server/Makefile)

AC_OUTPUT
