dnl Process this file with autoconf to produce a configure script.
AC_INIT([spin], [0.5.0])
AC_PREREQ([2.50])
AC_CONFIG_AUX_DIR([build-aux])
AM_INIT_AUTOMAKE([-Wall foreign tar-pax no-dist-gzip dist-bzip2 1.10b subdir-objects])
AC_CONFIG_HEADER([config.h])
AC_CONFIG_MACRO_DIR([m4])

m4_ifdef([AM_PROG_AR], [AM_PROG_AR])
dnl kernel style compile messages
m4_ifdef([AM_SILENT_RULES], [AM_SILENT_RULES([yes])])

dnl Checks for programs.
AC_PROG_MAKE_SET
AC_PROG_CC
AC_PROG_INSTALL

dnl Checks for header files.
AC_HEADER_DIRENT
AC_HEADER_STDC
AC_CHECK_HEADERS(fcntl.h unistd.h)

dnl Checks for typedefs, structures, and compiler characteristics.
AC_C_CONST
AC_TYPE_SIZE_T
AC_STRUCT_TM
AC_SYS_LARGEFILE

dnl Checks for library functions.
AC_FUNC_VPRINTF
AC_CHECK_FUNCS(socket strerror)

regular_CFLAGS="-Wall -Wextra -Wno-unused-parameter -Werror -O0"
AC_SUBST([regular_CFLAGS])

dnl Check for the right nfnetlink version
PKG_CHECK_MODULES([libnfnetlink], [libnfnetlink >= 1.0.1])

AC_CHECK_LIB([mosquitto], [mosquitto_lib_version], [], [AC_MSG_ERROR([libmosquitto not found])])

AC_ARG_WITH(linux-headers,
    AC_HELP_STRING([--with-linux-headers=PATH], [specify path of linux headers]),
    [ AC_SUBST(KERNELPATH, "$withval") ]
)

MAKEFILES="Makefile src/Makefile kernelmod/Makefile"

AC_ARG_ENABLE(tests,
              AC_HELP_STRING([--enable-tests], [enable unit tests and code coverage]),
              [
                MAKEFILES="$MAKEFILES src/tests/Makefile";
                AC_SUBST(TESTDIR, "tests")
                AC_CONFIG_FILES(src/tests/Makefile)
                CFLAGS="-g -O0"
              ], [])

AC_CONFIG_FILES(Makefile src/Makefile kernelmod/Makefile)
AC_OUTPUT
