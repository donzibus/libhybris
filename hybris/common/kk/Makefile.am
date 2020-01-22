if WANT_ARCH_ARM
ARCHFLAGS = -DHAVE_ARM_TLS_REGISTER -DANDROID_ARM_LINKER
DEFAULT_INCLUDES =  -I. -I$(top_builddir) -I$(bionic_libc)/ -I$(bionic_libc)/include/ -I$(bionic_libc)/arch-arm/include/
endif

if  WANT_ARCH_X86
ARCHFLAGS = -DANDROID_X86_LINKER
endif

CXXFLAGS += -std=c++11

noinst_LTLIBRARIES = \
	libandroid-linker.la
kk_la_SOURCES = \
	dlfcn.cpp \
	linker.cpp \
	linker_environ.cpp \
	linker_allocator.cpp \
	linker_phdr.cpp \
	rt.cpp
kk_la_CFLAGS = \
	-I$(top_srcdir)/include \
  $(ANDROID_HEADERS_CFLAGS) \
	-I$(top_srcdir)/common \
	-DDEFAULT_HYBRIS_LD_LIBRARY_PATH="\"@DEFAULT_HYBRIS_LD_LIBRARY_PATH@\"" \
	$(ARCHFLAGS)

#	-DLINKER_TEXT_BASE=0xB0000100 \
#	-DLINKER_AREA_SIZE=0x01000000 \

if WANT_DEBUG
kk_la_CFLAGS += -DLINKER_DEBUG=1
else
kk_la_CFLAGS += -DLINKER_DEBUG=0
endif
