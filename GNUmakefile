include osfive/mk/gnu.pre.mk

APP =		nrf9160
ARCH =		arm

CC =		${CROSS_COMPILE}gcc
LD =		${CROSS_COMPILE}ld
OBJCOPY =	${CROSS_COMPILE}objcopy

LDSCRIPT =	${CURDIR}/ldscript

OBJECTS =	alloc.o						\
		main.o						\
		${OSDIR}/sys/arm/nordicsemi/nrf_uarte.o		\
		${OSDIR}/sys/arm/nordicsemi/nrf9160_uicr.o	\
		${OSDIR}/sys/arm/nordicsemi/nrf9160_power.o	\
		${OSDIR}/sys/arm/nordicsemi/nrf9160_timer.o	\
		${OSDIR}/sys/arm/arm/machdep.o			\
		${OSDIR}/sys/arm/arm/nvic.o			\
		${OSDIR}/sys/arm/arm/trap.o			\
		${OSDIR}/sys/arm/arm/exception.o		\
		${OSDIR}/sys/kern/kern_malloc_fl.o		\
		${OSDIR}/sys/kern/subr_prf.o			\
		${OSDIR}/sys/kern/subr_console.o		\
		${OSDIR}/sys/kern/kern_panic.o			\
		start.o

OBJECTS_LINK =		\
  ${CURDIR}/nrfxlib/bsdlib/lib/cortex-m33/soft-float/libbsd_nrf9160_xxaa.a \
  ${CURDIR}/nrfxlib/bsdlib/lib/cortex-m33/soft-float/liboberon_2.0.5.a

LIBRARIES = LIBC LIBAEABI MBEDTLS_MDSHA

CFLAGS =-mthumb -mcpu=cortex-m4 -g -nostdlib -nostdinc	\
	-fno-builtin-printf -ffreestanding		\
	-Wredundant-decls -Wnested-externs		\
	-Wstrict-prototypes -Wmissing-prototypes	\
	-Wpointer-arith -Winline -Wcast-qual		\
	-Wundef -Wmissing-include-dirs -Wall -Werror

all:	__compile __link

clean:	__clean

include ${OSDIR}/lib/libaeabi/Makefile.inc
include ${OSDIR}/lib/libc/Makefile.inc
include ${OSDIR}/lib/mbedtls/Makefile.inc
include ${OSDIR}/mk/gnu.post.mk
