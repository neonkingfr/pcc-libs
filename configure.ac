# Process this file with autoconf to produce a configure script.

AC_PREREQ(2.59)
AC_INIT([pcc-libs], [0.9.9], <pcc-list@ludd.ltu.se>)

AC_PROG_MAKE_SET
AC_PROG_INSTALL
AC_CANONICAL_TARGET

version=$PACKAGE_VERSION

case "$target_os" in
    netbsd*)
	targos=netbsd
	case "$target_cpu" in
	    armeb) targmach=arm endian=big ;;
	    arm*) targmach=arm ;;
	    i?86) targmach=i386 ;;
	    m68k*) targmach=m68k endian=big ;;
	    mipseb) targmach=mips endian=big ;;
	    mips*) targmach=mips ;;
	    powerpc) targmach=powerpc endian=big ;;
	    sparc64) targmach=sparc64 endian=big ;;
	    vax) targmach=vax ;;
	    pdp10) targmach=pdp10 ;;
	esac
	;;

    openbsd*)
	targos=openbsd
	case "$target_cpu" in
	    i?86) targmach=i386 ;;
	    vax) targmach=vax ;;
	    powerpc) targmach=powerpc endian=big ;;
	    sparc64) targmach=sparc64 endian=big ;;
	esac
	;;

    dragonfly*)
	targos=dragonfly
	case "$target_cpu" in
	    i?86) targmach=i386 ;;
	esac
	;;

    darwin*)
	targos=darwin
	case "$target_cpu" in
	    i?86) targmach=i386 ;;
	    powerpc) targmach=powerpc endian=big ;;
	esac
        ;;

    freebsd*)
	targos=freebsd
	case "$target_cpu" in
	    i386) targmach=i386 ;;
	esac
	;;

    linux*)
	targos=linux
	case "$target_cpu" in
	    i?86) targmach=i386 ;;
	    powerpc*) targmach=powerpc endian=big ;;
	esac
	;;

    midnightbsd*)
	targos=midnightbsd
	case "$target_cpu" in
	    i?86) targmach=i386 ;;
	    sparc64) targmach=sparc64 endian=big ;;
	esac
	;;

    mirbsd*)
	targos=mirbsd
	case "$target_cpu" in
	    i?86) targmach=i386 ;;
	esac
	;;

    windows*|pe*)
	target_alias=i386-pe
	targos=win32
	targmach=i386
	;;

    apple)
	targos=apple
	case "$target_cpu" in
	    m68k) targmach=m68k endian=big ;;
	esac
	;;

    minix)
	targos=minix
	case "$target_cpu" in
	    m68k) targmach=m68k endian=big ;;
	esac
	;;

    *)
        targos="$target_os"
	case "$target_cpu" in
	    m16c) targmach=m16c ;;
	    nova) targmach=nova ;;
	esac
	;;
esac

if test "X$targos" = X -o "X$targmach" = X; then
	AC_MSG_ERROR(['$target' is not (yet) supported by pcc-libs.])
fi

if test "X$endian" = "Xbig"; then
	AC_SUBST([ENDIAN_FLAG],[-D__BIG_ENDIAN__=1])
else
	AC_SUBST([ENDIAN_FLAG],[-D__LITTLE_ENDIAN=1])
fi

AC_CHECK_PROG(CC, cc, cc, :)
AC_CHECK_PROG(AR, ar, ar, :)
AC_PROG_RANLIB

AC_SUBST(targos)
AC_SUBST(targmach)
AC_SUBST(version)
AC_SUBST(prefix)
AC_SUBST(libdir)
AC_SUBST(includedir)
AC_SUBST(CPPFLAGS)
AC_SUBST(CFLAGS)

AC_CONFIG_FILES([Makefile
                libsoftfloat/Makefile
		libpcc/Makefile
])
AC_OUTPUT
