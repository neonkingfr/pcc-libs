# Process this file with autoconf to produce a configure script.

AC_PREREQ(2.59)
AC_INIT([pcc-libs], [1.2.0.DEVEL], [pcc@lists.ludd.ltu.se])

AC_PROG_MAKE_SET
AC_PROG_INSTALL
AC_CANONICAL_TARGET

version=$PACKAGE_VERSION

case "$target_os" in

    apple)
	targos=apple
	case "$target_cpu" in
	    m68k) targmach=m68k endian=big ;;
	esac
	;;

    darwin*)
	targos=darwin
	case "$target_cpu" in
	    i?86) targmach=i386 ;;
	    powerpc) targmach=powerpc endian=big ;;
	    x86_64) targmach=amd64 ;;
	esac
	;;

    dragonfly*)
	targos=dragonfly
	case "$target_cpu" in
	    i?86) targmach=i386 ;;
	esac
	;;

    freebsd*)
	targos=freebsd
	case "$target_cpu" in
	    i?86) targmach=i386 ;;
	    x86_64) targmach=amd64 ;;
	esac
	;;

    linux*)
	targos=linux
	case "$target_cpu" in
	    arm*) targmach=arm ;;
	    i?86) targmach=i386 ;;
	    powerpc*) targmach=powerpc endian=big ;;
	    m68k*) targmach=m68k endian=big target_alias=m68k-linux-gnu CFLAGS="-march=68000 -msoft-float" ;;
	    x86_64) targmach=amd64 ;;
	    aarch64) targmach=aarch64 ;;
	esac
	;;

     litebsd*)
 	targos=litebsd
 	case "$target_cpu" in
 	    mips*) targmach=mips ;;
 	esac
 	;;

    midnightbsd*)
	targos=midnightbsd
	case "$target_cpu" in
	    i?86) targmach=i386 ;;
	    sparc64) targmach=sparc64 endian=big ;;
	esac
	;;

    minix*)
	targos=minix
	case "$target_os" in
	    minix3) CPPFLAGS="$CPPFLAGS -DSOFTFLOAT_NEED_FIXUNS" ;;
	    minix3.*) ;;
	esac
	case "$target_cpu" in
	    i86) targmach=i86 ;;
	    i?86) targmach=i386 ;;
	    arm*) targmach=arm ;;
	    x86_64) targmach=amd64 ;;
	    m68k) targmach=m68k endian=big ;;
	esac 
	;;

    mirbsd*)
	targos=mirbsd
	case "$target_cpu" in
	    i?86) targmach=i386 ;;
	esac
	;;

    netbsd*)
	targos=netbsd
	case "$target_cpu" in
	    armeb) targmach=arm endian=big ;;
	    arm*) targmach=arm ;;
	    i?86) targmach=i386 ;;
	    m68k*) targmach=m68k endian=big ;;
	    mipseb) targmach=mips endian=big ;;
	    mips*) targmach=mips ;;
	    pdp10) targmach=pdp10 ;;
	    powerpc) targmach=powerpc endian=big ;;
	    sparc64) targmach=sparc64 endian=big ;;
	    vax) targmach=vax ;;
	    x86_64) targmach=amd64 ;;
	esac
	;;

    openbsd*)
	targos=openbsd
	case "$target_cpu" in
	    i?86) targmach=i386 ;;
	    mips64el) targmach=mips ;;
	    mips64) targmach=mips endian=big ;;
	    powerpc) targmach=powerpc endian=big ;;
	    sparc64) targmach=sparc64 endian=big ;;
	    vax) targmach=vax ;;
	    x86_64) targmach=amd64 ;;
	esac
	;;

    sysv4*|sunos*|solaris*)
	targos=sunos
	case "$target_cpu" in
	    i?86) targmach=i386 ;;
	    sparc*) targmach=sparc64 endian=big ;;
	    x86_64) targmach=amd64 ;;
	esac
	;;

    windows*|pe*)
	target_alias=i386-pe
	targos=win32
	targmach=i386
	;;

    *)
	targos="$target_os"
	case "$target_cpu" in
	    m16c) targmach=m16c ;;
	    nova) targmach=nova ;;
	    m68k*) targmach=m68k endian=big ;;
	esac
	;;
esac

if test "X$targos" = X -o "X$targmach" = X; then
	AC_MSG_ERROR(['$target' is not (yet) supported by pcc-libs.])
fi

if test "X$endian" = "Xbig"; then
	AC_SUBST([ENDIAN_FLAG],[-DTARGET_BIG_ENDIAN=1])
else
	AC_SUBST([ENDIAN_FLAG],[-DTARGET_LITTLE_ENDIAN=1])
fi

AC_CHECK_TOOLS([CC], [pcc gcc cc])
AC_CHECK_TOOL([AR], [ar], [ar])
AC_CHECK_TOOL([AS], [as], [as])
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
	csu/Makefile
	libsoftfloat/Makefile
	libpcc/Makefile
])
AC_OUTPUT
