AC_INIT([Gladrags], [0.22])

AM_INIT_AUTOMAKE
AM_PATH_PYTHON([3.0])

GLIB_GSETTINGS

AC_ARG_WITH([gtk3],
    [AS_HELP_STRING([--with-gtk3], [Build for Gtk3 instead of Gtk2])],
    [],
    [with_gtk3=no])

AS_IF([test "x$with_gtk3" != xno],
    [
    AM_CONDITIONAL(WITH_GTK3_SET, true)],
    [
    AM_CONDITIONAL(WITH_GTK3_SET, false)
    ])

AC_CONFIG_FILES([Makefile src/Makefile])

AC_OUTPUT
