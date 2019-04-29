PWD := $(shell pwd)

ifneq ($(KERNELRELEASE),)
# kbuild part of makefile
obj-m := helloworld.o

ifeq ($(CONFIG_SOC_S32V234),y)
#ipc-shm-dev-y += ipc-hw-s32v234.o
endif

# Add here cc flags (e.g. header lookup paths, defines, etc)
ccflags-y +=

else
ARCH ?= arm64

# The following parameters must be passed from the caller,
# e.g. build system (Yocto), command line:
# KERNELDIR    : Linux kernel source code location
# INSTALL_DIR  : location of the module installation
# CROSS_COMPILE: the path and prefix of the used cross compiler

KERNELDIR := ~/linux
#CROSS_COMPILE := aarch64-linux-gun-

modules:
	$(MAKE) -C  $(KERNELDIR) M=$(PWD) ARCH=$(ARCH) CROSS_COMPILE=$(CROSS_COMPILE) $@

modules_install: modules
	$(MAKE) -C $(KERNELDIR) M=$(PWD) INSTALL_MOD_PATH="$(INSTALL_DIR)" $@

clean:
	$(MAKE) -C $(KERNELDIR) M=$(PWD) ARCH=$(ARCH) $@

.PHONY: modules clean

endif
